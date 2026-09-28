<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/assignments-script-delete -->
<!-- Sitemap-Last-Modified: 2026-02-24 -->

# Assignments Scripts - Delete

Below are the PowerShell scripts for Delete - EDU assignments, Exports - EDU assignments and Get - user classes.

## Delete - EDU assignments

```
<#
   .Synopsis
    Delete the Edu Assignments data of a user in a set of classes specified in csv file.
    .DESCRIPTION
    The script reads the class details of user from input csv file. Get the assignments and submissions of each assignment and then delete the submissions, it also generate a report file(DeleteAssignmentsReport.csv) for extra information of call information. when the deletion of submission is done it updates the DeleteSubmissionsProcessed column to true for that specific class. If the script fails in between we can rerun the script with the same input file, because the file will be updated for last deletion of submission.
   .Example
    .\Delete-EduAssignments.ps1 -userClassDetailsFile <full path of user class details csv file>
    This will delete all the submissions but does not remove the user info from class
    .\Delete-EduAssignments.ps1 -userClassDetailsFile <full path of user class details csv file> -removeMemberFromClass
    This will delete all the submissions and remove the user info from class
   .Parameter userClassDetailsFile
   This is the csv file(userClassDetails.csv) which is the output of Get-UserClasses.ps1 script. This file have information about the user classes and whether the deletion and get submissions are processed. This value should be full path of the file(drive:\GDPR\userClassDetails.csv)
   .Switch Parameter removeMemberFromClass
   When we use this parameter it will remove the user info from each class
   .Notes
   We need to have the Microsoft.IdentityModel.Clients.ActiveDirectory.dll and Microsoft.IdentityModel.Clients.ActiveDirectory.WindowsForms.dll are required
#>
param(
    [parameter(Mandatory=$true)]
    [ValidateNotNullOrEmpty()]
    [ValidateScript({
        if(-Not ($_ | Test-Path)) {
            throw "The userClassDetailsFile does not exist."
        }
        if(-Not ($_ | Test-Path -PathType Leaf) ){
            throw "The userClassDetailsFile argument must be a file. Folder paths are not allowed."
        }
        if($_ -notmatch "(\.csv)"){
            throw "The userClassDetailsFile should be a comma-separated file, generated using Get-UserClasses.ps1"
        }
        return $true
    })]
    [string] $userClassDetailsFile,
    [parameter(Mandatory=$false)]
    [switch] $removeMemberFromClass
)
# Load ADAL
Add-Type -Path ".\ADAL\Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
$educationEndpoint = "https://graph.microsoft.com/beta/education/"
$script:userClassDetails = @()
$script:deleteAssignmentsReport = @()
$script:maxRetryAttempt = 3
$script:authHeaders = $null
$script:authenticationResult = $null
$graphEndpoint = "https://graph.microsoft.com"
$authString = "https://login.windows.net/common"
#Get the authheaders
function Get-AuthHeaders
{
    Param(
        [Parameter(Mandatory=$false)]
        [bool] $useRefreshToken = $false
    )
    $clientId = "eb2298a1-a6bb-4f16-a27a-b582815db47b"
    $redirectURI = New-Object System.Uri("urn:ietf:wg:oauth:2.0:oob")
    $promptBehavior = [Microsoft.IdentityModel.Clients.ActiveDirectory.PromptBehavior]::Always
    $authContext = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext" -ArgumentList $authString
    if($useRefreshToken -eq $false)
    {
        $script:authenticationResult = $authContext.AcquireToken($graphEndpoint, $clientID, $redirectURI, $promptBehavior)
    }
    else
    {
        $script:authenticationResult = $authContext.AcquireTokenByRefreshToken($script:authenticationResult.RefreshToken, $clientId)
    }
    $authHeader = $script:authenticationResult.AccessTokenType + " " + $script:authenticationResult.AccessToken
    $headers = @{"Authorization" = $authHeader; "Content-Type" = "Application/json"}
    return $headers
}
#Retry logic and logging of errors for script
function Invoke-RequestWithRetry
{
    param(
        [Parameter(Mandatory=$true)]$url,
        [Parameter(Mandatory=$true)][ValidateSet('Get','Delete', ignorecase=$true)]$httpmethod,
        [Parameter(Mandatory=$false)]$classId,
        [Parameter(Mandatory=$false)]$className,
        [Parameter(Mandatory=$true)]$OperationName
    )
    for($i=1; $i -le $script:maxRetryAttempt; $i++)
    {
        try
        {
            $APIResult = Invoke-WebRequest -Method $httpmethod -Uri $url -Headers $script:authHeaders
            $resultCount = 0
            if($OperationName -eq "GetAssignments")
            {
                $valueStartIndex = ($APIResult.content.indexof('"value":') + 8)
                $valueEndIndex = $APIResult.content.Length
                $valueString = $APIResult.content.substring($valueStartIndex, $valueEndIndex-$valueStartIndex -1)
                $resultCount = (($valuestring | select-string '"classId":' -AllMatches ).Matches.Count)
            }
            else
            {
                $submissionsJson = $APIResult.content | ConvertFrom-Json
                $resultCount = $submissionsJson.value.count
            }
            $script:deleteAssignmentsReport += [PSCustomObject]@{
                RequestUrl = $url
                Method = $httpmethod
                ResponseCode = $APIResult.StatusCode
                ClassName = $className
                ClassId = $classId
                RequestId = $APIResult.Headers["request-id"]
                StatusDescription = $APIResult.StatusDescription
                NumberOfAttempts = $i
                OperationName = $OperationName
                ResultCount = $resultCount
            }
            return $APIResult
        }
        catch
        {
            if($_.Exception.Response -ne $null)
            {
                $responseCode = $_.Exception.Response.StatusCode.Value__
                $requestId = $_.Exception.Response.Headers["request-id"]
            }
           
            $script:deleteAssignmentsReport += [PSCustomObject]@{
                RequestUrl = $url
                Method = $httpmethod
                ResponseCode = $responseCode
                ClassName = $className
                ClassId = $classId
                RequestId = $requestId
                StatusDescription = $_.Exception.Message
                NumberOfAttempts = $i
                OperationName = $OperationName
                ResultCount = $resultCount
            }
            if($i -eq $script:maxRetryAttempt)
            {
                throw $_
            }
            if($responseCode -eq 401)
            {
                $script:authHeaders = Get-AuthHeaders -useRefreshToken $true
            }
        }
    }
}
#Remove member from class
function Remove-MemberFromClass
{
    param(
        [Parameter(Mandatory=$true)]$classDetails
    )
    $removeMemberUrl = "{0}/v1.0/groups/{1}/members/{2}/`$ref" -f $graphEndpoint, $($classDetails.ClassId), $($classDetails.UserId)
    try
    {
        Invoke-RequestWithRetry -url $removeMemberUrl -httpmethod Delete -classId $($classDetails.ClassId) -className $($classDetails.ClassName) -OperationName "RemoveMemberfromClass" | Out-Null   
    }
    catch
    {
        throw $_
    }
   
}
function Delete-Assignments
{
    param(
        [Parameter(Mandatory=$true)]$classDetail
    )
    try
    {
        $classId = $classDetail.ClassId
        $className = $classDetail.ClassName
        $userId = $classDetail.UserId
        $role = $classDetail.Role
        $getAssignmentsUri = ("{0}/classes('{1}')/assignments?TargetUserId={2}&UserClassRole={3}" -f $educationEndpoint, $classId, $userId, $role)
        $assignments = $null
        $assignments = Invoke-RequestWithRetry -url $getAssignmentsUri -httpmethod Get -classId $classId -className $className -OperationName "GetAssignments"
        if($assignments -ne $null -and $assignments.content -ne $null -and $role -eq "Student"))
        {
            $assignmentsCount = ((($assignments.content) | ConvertFrom-Json).value).count
            Write-Host "Retrieved $assignmentsCount Assignments for $className class"
            $assignmentsTracker = 0
            foreach($assignment in (($assignments.content) | ConvertFrom-Json).value)
            {
                $assignmentName = $assignment.displayName
                $assignmentId = $assignment.id
                $submissions = $assignment.submissions
                Write-Host "Deleting submissions for $($assignmentName)"
                $submissionsTracker = 0
                foreach($submission in $submissions)
                {
                    $deleteSDSSubmissionUri = "{0}/beta/education/classes/{1}/assignments/{2}/submissions/{3}?TargetUserId={4}&UserClassRole=Student" -f $graphEndpoint, $classId, $assignmentId, $($submission.id), $userId
                    if(($submissionsTracker -eq ($submissions.Length -1)) -and ($assignmentsTracker -eq ($assignmentsCount - 1)) -and ($removeMemberFromClass.IsPresent))
                    {
                        Write-Host "Deleting submission and classinfo for user"
                        $deleteSDSSubmissionUri = $deleteSDSSubmissionUri + "&CleanupUserClassData=true"
                    }
                    $deleteResponse = Invoke-RequestWithRetry -url $deleteSDSSubmissionUri -httpmethod Delete -classId $classId -className $className -OperationName "DeleteSubmission"
                    if($deleteResponse -ne $null -and $deleteResponse.Content.Length -ne 0 -and $submissionsTracker -eq ($submissions.Length -1))
                    {
                        $classDetail.DeleteSubmissionsProcessed = "True"
                        $script:userClassDetails | Export-Csv -Path $($directoryPathOfFile) -NoTypeInformation -Force
                    }
                    $submissionsTracker++
                }
                $assignmentsTracker++
            }
        }
    }
    catch
    {   
        throw $_
    }
}
$directoryPathOfFile = (Get-Item -path $($userClassDetailsFile)).FullName
$script:authHeaders = Get-AuthHeaders
$script:userClassDetails = import-csv $userClassDetailsFile
$progressTracker = 0;
foreach($classDetail in $script:userClassDetails)
{
    Write-Progress -Activity "Deleting Assignments for user" -Status "Processing for class: $classDetail.classId" -PercentComplete ($progressTracker/$script:userClassDetails.count * 100)
    if($classDetail.DeleteSubmissionsProcessed -eq "False")
    {
        try
        {
            if($removeMemberFromClass.IsPresent)
            {
                Write-Host "Deleting user from $($classDetail.ClassName)"
                Remove-MemberFromClass -classDetails $classDetail
            }
            Write-host "Deleting Assignments of user for $($classDetails.ClassName)"
            Delete-Assignments -classDetails $classDetail  
        }
        catch
        {
            write-Error $_.Exception.Message   
        }
    }
    $progressTracker++
}
$directoryPath = (Get-Item -Path ".\" -Verbose).FullName
$script:deleteAssignmentsReport | Export-Csv -Path .\DeleteAssignmentsReport.csv -NoTypeInformation -Force
Write-Host "Report file(DeleteAssignmentsReport.csv) is generated at $directoryPath\DeleteAssignmentsReport.csv"
Write-Host "Updated Class details file($($directoryPathOfFile)) and generated updated file is at $($directoryPathOfFile)"
```
