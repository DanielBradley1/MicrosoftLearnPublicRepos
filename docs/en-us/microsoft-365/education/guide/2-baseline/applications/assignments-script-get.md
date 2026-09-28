<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/assignments-script-get -->
<!-- Sitemap-Last-Modified: 2026-02-24 -->

# Assignments Scripts - Get

Note

This script cannot be run in PowerShell ISE.

Below are the PowerShell scripts for Get - user classes.

```
<#
   .Synopsis
    Get the user classes info like in which classes the user is member and what is the user role of the user in those classes.
    .DESCRIPTION
    Scripts reads the file and get all the classids and updates the role with the userrole mentioned, if not mentioned assign to student which is default. Then it gets the classes in which the user is owner and classes where the user is member. Script refines and generates the output with the class details and role of user in specific class.
   .Example
    .\Get-userClasses.ps1 -userId <specific user Id>
        This will get the user details according to user membership
    .\Get-userClasses.ps1 -userId <specific user Id> -classIdsFile <complete csv file path>
        This will get the user details of classes specified in csv file and user membership, if we don't pass the userRole parameter, it will be assigned to Student default for the classIds specified in csv file
    .\Get-userClasses.ps1 -userId <specific user Id> -classIdsFile <complete csv file path> -userrole <Student or Teacher>
        This will get the user details of classes specified in csv file and user membership. For the classids specified in file user data is generated according to the userrole specified(Teacher or Student)
   .Parameter userId
   UserId of the user to export and delete submissions
   .Parameter classIdsFile
   Full path to a plain text file which contains a single classId on each line.
   sample list of classIds. Each line should have single classId
   e81c2cd2-e3ff-4c0a-8ed0-63df43ff884c
   044b4c35-5fab-454a-9705-bc750108c059
   e81c2cd2-4c0a-e3ff-9705-bc750108c059
   .Parameter userrole
   This parmeter is used to specify the role of the user to be used for the class ids present in classIdsFile and the user is removed from class.
   .paramter outputFileName
   This parameter is used to name the output file of the script, no extensions. This is not mandatorty by default the output file name is UserClassDetails
#>
param(
    [Parameter(Mandatory=$true, Position=1)]
    [ValidateNotNullOrEmpty()]
    [ValidateScript({
        try {
            [System.Guid]::Parse($_) | Out-Null
            $true
        } catch {
            throw $_
        }
    })]
    [string] $userId,
    [parameter(Mandatory=$false, Position=2)]
    [ValidateNotNullOrEmpty()]
    [ValidateScript({
        if(-Not ($_ | Test-Path) ){
            throw "File or folder does not exist"
        }
        if(-Not ($_ | Test-Path -PathType Leaf) ){
            throw "The classIdsFile argument must be a file. Folder paths are not allowed."
        }
        if($_ -notmatch "(\.txt)"){
            throw "The file specified in the path argument must be of type txt"
        }
        return $true
    })]
    [string] $classIdsFile,
    [Parameter(Mandatory=$false, Position=3)]
    [ValidateNotNullOrEmpty()]
    [ValidateSet('Student','Teacher', ignorecase=$false)]
    [string] $userrole = "Student",
    [parameter(Mandatory=$false, Position=4)]
    [ValidateNotNullOrEmpty()]
    [string] $outputFileName = "UserClassDetails"
)
# Load ADAL
#Add-Type -Path ".\ADAL\Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
# Load MSAL
if ( -not(Get-Module Microsoft.Identity.Client -ListAvailable) ) {
   Install-Module Microsoft.Identity.Client -Force -Scope CurrentUser -ErrorAction Stop
}
Import-Module Microsoft.Identity.Client
$script:maxRetryAttempt = 3
$script:authenticationResult = $null
$graphEndpoint = "https://graph.microsoft.com"
$authString = "https://login.windows.net/common"
# Output to summarize success/failure of API calls.
$script:getClassDetailsReport = @()
#Makes Web request and logs the response status
function Invoke-RequestWithRetry
{
    param(
        [Parameter(Mandatory=$true)]$url,
        [Parameter(Mandatory=$false)]$classId,
        [Parameter(Mandatory=$false)]$className
    )
    for($i=1; $i -le $script:maxRetryAttempt; $i++)
    {
        try
        {
            $tempResult = Invoke-WebRequest -Method Get -Uri $url -Headers $script:authHeaders
            $script:getClassDetailsReport += [PSCustomObject]@{
                RequestUrl = $url
                Method = "Get"
                ResponseCode = $tempResult.StatusCode
                ClassName = $className
                ClassId = $classId
                RequestId = $tempResult.Headers["request-id"]
                StatusDescription = $tempResult.StatusDescription
                NumberOfAttempts = $i
            }
            return $tempResult
        }
        catch
        {
            if($_.Exception.Response -ne $null)
            {
                $responseCode = $_.Exception.Response.StatusCode.Value__
                $requestId = $_.Exception.Response.Headers["request-id"]
            }
           
            $script:getClassDetailsReport += [PSCustomObject]@{
                RequestUrl = $url
                Method = "Get"
                ResponseCode = $responseCode
                ClassName = $className
                ClassId = $classId
                RequestId = $requestId
                StatusDescription = $_.Exception.Message
                NumberOfAttempts = $i
            }
            if($i -eq $script:maxRetryAttempt)
            {
                throw $_.Exception.Message
            }
            if($responseCode -eq 401)
            {
                $script:authHeaders = Get-AuthHeaders -useRefreshToken $true
            }
        }
    }
}
#Get the authheaders
function Get-AuthHeaders {
   Param(
      [Parameter(Mandatory = $false)]
      [bool] $useRefreshToken = $false
   )
   $pcaOptions = [Microsoft.Identity.Client.PublicClientApplicationOptions]::new()
   $pcaOptions.ClientId = "eb2298a1-a6bb-4f16-a27a-b582815db47b"
   $pcaOptions.RedirectUri = New-Object System.Uri("urn:ietf:wg:oauth:2.0:oob")
   $pcaBuilder = [Microsoft.Identity.Client.PublicClientApplicationBuilder]::CreateWithApplicationOptions($pcaOptions)
   $pca = $pcaBuilder.Build()
   $scopes = New-Object System.Collections.Generic.List[string]       
   $scopes.Add("EduRoster.ReadBasic") 
   $scopes.Add("Group.Read.All")
   $authResult = $pca.AcquireTokenInteractive($scopes)
   if ($useRefreshToken -eq $false) {
      $script:token = $authResult.ExecuteAsync()
      while ( $script:token.IsCompleted -eq $False ) { <# Waiting for token auth flow to complete #> }
   }
   else {
      $script:token = $pca.AcquireTokenByRefreshToken($scopes, $script:token.Result.AccessToken)
   }
   $authHeader = $script:token.Result.TokenType + " " + $script:token.Result.AccessToken
   $headers = @{"Authorization" = $authHeader; "Content-Type" = "Application/json" }
   return $headers
}
#Get the group Name
function Get-ClassName
{
    param(
        [Parameter(Mandatory=$true)]$classId
    )
    $getClassDetailsUrl = "{0}/v1.0/groups/{1}" -f $graphEndpoint, $classId
    $getClassDetailsResult = (Invoke-RequestWithRetry -url $getClassDetailsUrl) | ConvertFrom-Json
    $className = $getclassDetailsResult.displayName
    return $className
}
#Get ownership details of user id using edu endpoit and refine with the creation type to assignments
function Get-OwnershipDetails
{
    param(
        [Parameter(Mandatory=$true)]$userId
    )
    $ownershipUrl = ("{0}/edu/users/{1}/ownedobjects?`$top=999" -f $graphEndpoint,$userId)
    $ownershipQuery = (Invoke-RequestWithRetry -url $ownershipUrl) | ConvertFrom-Json
    $classes = $ownershipQuery.value | Where-Object {$_.creationOptions -contains "classAssignments" } | Select-Object objectId, displayName
    return $classes
}
#Get the membership details of user id using edu endpoint and refine with the creation type to assignments
function Get-MembershipDetails
{
    param(
        [Parameter(Mandatory=$true)]$userId
    )
    $membershipUrl = ("{0}/edu/users/{1}/memberof?`$top=999" -f $graphEndpoint,$userId)
    $membershipQuery = (Invoke-RequestWithRetry -url $membershipUrl) | ConvertFrom-Json
    $classes = $membershipQuery.value | Where-Object {$_.creationOptions -contains "classAssignments" } | Select-Object objectId, displayName
    return $classes
}
#Return custom pscutom object which have classid, userid, classname, role, getsubmissionprocessed and deletesubmissionprocessed properties
function Generate-ClassRecord
{
    param(
        [Parameter(Mandatory=$true)]$userId,
        [Parameter(Mandatory=$true)]$classId,
        [Parameter(Mandatory=$true)]$role,
        [Parameter(Mandatory=$false)]$displayName
    )
    $classRecord = [PSCustomObject]@{
        ClassId = $classId
        UserId = $userId
        ClassName = $displayName
        Role = $role
        GetSubmissionsProcessed = $false
        DeleteSubmissionsProcessed = $false
    }
    return $classRecord
}
$script:authHeaders = Get-AuthHeaders
# This will contain the details for all "interesting" classes
$script:classDetails= @{}
# Find owned classes (where user is currently a teacher)
try
{
    $ownedClasses = Get-OwnershipDetails -userId $userId
    foreach($class in $ownedClasses)
    {
        if(-NOT $script:classDetails.ContainsKey($class.objectId))
        {
            $classRecord = Generate-ClassRecord -userId $userId -classId $class.objectId -role "Teacher" -displayName $class.displayName
            $script:classDetails.Add($class.objectId, $classRecord)
        }
    }
}
catch
{
    Write-Error $_.Exception.Message
}
# Find joined groups (where user is currently a student)
try
{
    $joinedClasses = Get-MembershipDetails -userId $userId
    foreach($class in $joinedClasses)
    {
        if(-NOT $script:classDetails.ContainsKey($class.objectId))
        {
            $classRecord = Generate-ClassRecord -userId $userId -classId $class.objectId -role "Student" -displayName $class.displayName
            $script:classDetails.Add($class.objectId, $classRecord)
        }
    }
}
catch
{
    Write-Error $_.Exception.Message
}
# Find details for the additional groups from the file.
if(![string]::IsNullOrEmpty($classIdsFile))
{
    $classIdsFromFile = Select-String -Pattern "\w" -Path $($classIdsFile) | ForEach-Object{
        $_.Line
    }
    foreach ($classId in $classIdsFromFile)
    {
        # List of user's current classes takes precendence over the additional set of classes
        # i.e. if we've already identified the role, we don't need to do it again.
        if(-NOT $script:classDetails.ContainsKey($classId.Trim("")))
        {
            try
            {
                $displayName = Get-ClassName -classId $classId
                $classRecord = Generate-ClassRecord -userId $userId -classId $classId -role $userrole -displayName $displayName
                $script:classDetails.Add($classId, $classRecord)
            }
            catch
            {
                Write-Host $_.Exception.Message
            }
           
        }
    }
}
$script:classDetails.Values | Export-Csv -Path .\$($outputFileName).csv -NoTypeInformation
$script:getClassDetailsReport | Export-Csv -Path .\UserClassDetailsReport.csv -NoTypeInformation
$directoryPath = (Get-Item -Path ".\" -Verbose).FullName
Write-Host "Class details file($($outputFileName).csv) is generated at $directoryPath\($($outputFileName).csv)"
Write-Host "Class details report(UserClassDetailsReport.csv) is generated at $directoryPath\UserClassDetailsReport.csv"
```
