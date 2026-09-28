<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/assignments-script-export -->
<!-- Sitemap-Last-Modified: 2026-02-24 -->

# Assignments scripts- Export

Below are the PowerShell scripts for Exports - EDU assignments.

```
<# 
   .Synopsis 
    Export the Edu Assignments data of a user in a set of classes specified in csv file.
    .DESCRIPTION
    The script reads the class details of user from input csv file. Get the assignments and submissions of each assignment and generates the assignment file(assignment.json) and report file(GetAssignmentsReport.csv). when extracting of submissions is done it updates the GetSubmissionsProcessed column to true for that specific class. If the script fails in between we can rerun the script with the same input file, because the file will be updated for last deletion of submission.
   .Example 
    .\Export-EduAssignments.ps1 -userClassDetailsFile <full path of user class details csv file>
   .Parameter userClassDetailsFile
   This is the csv file(userClassDetails.csv) which is the output of Get-UserClasses.ps1 script. This file have information about the user classes and whether the deletion and get submissions are processed. This value should be full path of the file(drive:\GDPR\userClassDetails.csv)
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
    [string] $userClassDetailsFile
)
# Load ADAL
Add-Type -Path ".\ADAL\Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
$educationEndpoint = "https://graph.microsoft.com/beta/education"
$script:userClassDetails = @()
$script:getAssignmentsReport = @()
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
        [Parameter(Mandatory=$false)]$classId,
        [Parameter(Mandatory=$false)]$className,
        [Parameter(Mandatory=$true)]$OperationName
    )
    for($i=1; $i -le $script:maxRetryAttempt; $i++)
    {
        try 
        {
            $APIResult = Invoke-WebRequest -Method Get -Uri $url -Headers $script:authHeaders
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
            $script:getAssignmentsReport += [PSCustomObject]@{
                RequestUrl = $url
                Method = "Get"
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
            if($null -ne $_.Exception.Response)
            {
                $responseCode = $_.Exception.Response.StatusCode.Value__
                $requestId = $_.Exception.Response.Headers["request-id"]
            }
            
            $script:getAssignmentsReport += [PSCustomObject]@{
                RequestUrl = $url
                Method = "Get"
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
#get assignments
function Get-Assignments
{
    param(
        [Parameter(Mandatory=$true)]$classDetails
    )
    try 
    {
        $classId = $classDetails.ClassId
        $userId = $classDetails.UserId
        $role = $classDetails.Role
        $className = $classId
        if($null -ne $classDetails.ClassName -and $classDetail.ClassName.Length -ne 0)
        {
            $className = $classDetails.ClassName
        }
        $getAssignmentsUri = ("{0}/classes('{1}')/assignments?expand=categories,rubric,resources,submissions&TargetUserId={2}&UserClassRole={3}" -f $educationEndpoint, $classId, $userId, $role)
        $assignments = $null
        $assignments = Invoke-RequestWithRetry -url $getAssignmentsUri -classId $classId -className $className -OperationName "GetAssignments"
        $outputstring = ""
        $assignmentsStrings = @()
        if($null -ne $assignments)
        {
            $valueStartIndex = ($assignments.content.indexof('"value":') + 8)
            $valueEndIndex = $assignments.content.Length
            $valueString = $assignments.content.substring($valueStartIndex, $valueEndIndex-$valueStartIndex -1)
           
            $valueString = $valueString.TrimEnd("]")
            $valueString = $valueString.TrimStart("[")
            $indexValues = (($valuestring | select-string '"classId":' -AllMatches ).Matches.Index)
            Write-Host "Retrieved $($indexValues.count) Assignments for $className class"
            for($i=0; $i -lt $indexValues.count; $i++)
            {
                if($i -ne $indexValues.count -1)
                {
                    $assignmentsStrings += $valueString.substring(($indexValues[$i]-1),($indexValues[$i+1] - $indexValues[$i] -1))
                }
                else 
                {
                    $assignmentsStrings += $valueString.substring(($indexValues[$i]-1), ($valueString.Length - $indexValues[$i] +1))
                }
                
                if($role -eq "Student")
                {
                    $submissionsIndex = $assignmentsStrings[$i].indexof('"submissions":[')
                    $assignmentsStrings[$i] = $assignmentsStrings[$i].substring(0, $submissionsIndex+15)
                    $assignmentsStrings[$i] = $assignmentsStrings[$i] + "]}"
                }
            }
            for($i=0; $i -lt $assignmentsStrings.Length ; $i++)
            {
                $assignmentString = $assignmentsStrings[$i]
                $assignmentJson = $assignmentString | ConvertFrom-Json
                $assignmentId = $assignmentJson.id
                Write-Host "Getting submissions for $($assignmentJson.displayName) assignment"
                $sumbmissionsEndpoint = ("{0}/classes('{1}')/assignments('{2}')/submissions?expand=outcomes,resources,submittedResources&TargetUserId={3}&UserClassRole={4}" -f $educationEndpoint, $classId, $assignmentId, $userId, $role)
                $submissions = Invoke-RequestWithRetry -classId $classId -url $sumbmissionsEndpoint -classname $className -OperationName "GetSubmissions"
                if($null -ne $submissions -and $submissions.Content.Length -ne 0 )
                {
                    $submissionsJson = $submissions.content | ConvertFrom-Json
                    Write-Host "Retrieved $($submissionsJson.value.count) submissions for $($assignmentJson.displayName) assignment"
                    $valueStartIndex = ($submissions.content.indexof('"value":') + 9)
                    $valueEndIndex = $submissions.content.lastindexof("}")
                    $submissionsString = $submissions.content.substring($valueStartIndex, $valueEndIndex-$valueStartIndex -1)
                    $assignmentsStrings[$i] = $assignmentsStrings[$i].TrimEnd("]}")
                    $assignmentsStrings[$i] = $assignmentsStrings[$i] + $submissionsString + "]}"
                }
            }
        }
        $completeAssigmentsString = "["
        if($assignmentsStrings.Length -eq 0)
        {
            $completeAssigmentsString = $completeAssigmentsString + "]"
        }
        else
        {
            for($i=0; $i -lt $assignmentsStrings.Length; $i++)
            {
                if($i -eq $assignmentsStrings.Length -1)
                {
                    $completeAssigmentsString = $completeAssigmentsString + $assignmentsStrings[$i] + "]"
                }
                else 
                {
                    $completeAssigmentsString = $completeAssigmentsString + $assignmentsStrings[$i] + ","
                }
            }
        }
        $outputstring = '{"ClassId":"' + $classId + '","ClassName":"' + $className +'","assignments":' + $completeAssigmentsString
        if($role -eq "Teacher")
        {
            Write-Host "Getting all assignment categories for $($classDetail.ClassName)"
            $getCategoriesUri = ("{0}/classes('{1}')/assignmentCategories?TargetUserId={2}&UserClassRole={3}" -f $educationEndpoint, $classId, $userId, $role)
            $categories = $null
            $categories = Invoke-RequestWithRetry -url $getCategoriesUri -classId $classId -className $className -OperationName "GetAssignmentCategories"
            $categoriesStrings = @()
            if ($null -ne $categories)
            {
                $valueStartIndex = ($categories.content.indexof('"value":') + 8)
                $valueEndIndex = $categories.content.Length
                $valueString = $categories.content.substring($valueStartIndex, $valueEndIndex-$valueStartIndex -1)
           
                $valueString = $valueString.TrimEnd("]")
                $valueString = $valueString.TrimStart("[")
                $indexValues = (($valuestring | select-string '"displayName":' -AllMatches ).Matches.Index)
                Write-Host "Retrieved $($indexValues.count) Assignment Categories for $className class"
                for($i=0; $i -lt $indexValues.count; $i++)
                {
                    if($i -ne $indexValues.count -1)
                    {
                        $categoriesStrings += $valueString.substring(($indexValues[$i]-1),($indexValues[$i+1] - $indexValues[$i] -1))
                    }
                    else 
                    {
                        $categoriesStrings += $valueString.substring(($indexValues[$i]-1), ($valueString.Length - $indexValues[$i] +1))
                    }
                }
                $outputstring += '","categories":' + $categoriesStrings
            }
        }
        $outputstring += '}'
        $dateTimeStamp = $(get-date -f yyyy-MM-dd)
        $fileName = $directoryPath + "\" + $className + "_" + $userId + "_" + $dateTimeStamp + ".json"
        $outputstring | Out-File $fileName
        Write-Host("Assignments file for $className is generated at $fileName")
        $classDetails.GetSubmissionsProcessed = "True"
        $script:userClassDetails | Export-Csv -Path $($directoryPathOfFile) -NoTypeInformation -Force
    }
    catch 
    {
        write-Error $_.Exception.Message
    }
    
}
#get me rubrics
function Get-Rubrics
{
    param(
        [Parameter(Mandatory=$true)]$userId
    )
    try
    {
        $getRubricsUri = ("{0}/me/rubrics?TargetUserId={1}" -f $educationEndpoint, $userId)
        $rubrics = $null
        $rubrics = Invoke-RequestWithRetry -url $getRubricsUri -OperationName "GetRubrics"
        $rubricsStrings = @()
        if($null -ne $rubrics)
        {
            $valueStartIndex = ($rubrics.content.indexof('"value":') + 8)
            $valueEndIndex = $rubrics.content.Length
            $rubricsStrings = $rubrics.content.substring($valueStartIndex, $valueEndIndex-$valueStartIndex -1)
            $outputstring = '{"Rubrics":' + $rubricsStrings + '}'
        }
        $dateTimeStamp = $(get-date -f yyyy-MM-dd)
        $fileName = $directoryPath + "\" + "Rubrics_" + $userId + "_" + $dateTimeStamp + ".json"
        $outputstring | Out-File $fileName
        Write-Host("Rubrics file for $userId is generated at $fileName")
    }
    catch 
    {
        write-Error $_.Exception.Message
    }
}
$directoryPathOfFile = (Get-Item -path $($userClassDetailsFile)).FullName
$directoryPath = (Get-Item -Path ".\" -Verbose).FullName
$script:authHeaders = Get-AuthHeaders
$script:userClassDetails = import-csv $userClassDetailsFile
$userId = $null
$progressTracker = 1;
#loop through each line and get submissions if the getsubmissionsprocessed column is false
foreach($classDetail in $script:userClassDetails)
{
    Write-Progress -Activity "Getting Assignments for user" -Status "Processing for class: $($classDetail.classId)" -PercentComplete ($progressTracker/$($script:userClassDetails | Measure-object).count * 100)
    if($classDetail.GetSubmissionsProcessed -eq "False")
    {
        Write-Host "Getting Assignments for $($classDetail.ClassName)"
        Get-Assignments -classDetails $classDetail
    }
    $progressTracker++
    $userId = $classDetail.userId
}
#check if the user has any rubrics
Write-Host "Getting Rubrics for user $($userId)"
Get-Rubrics -userId $userId
$script:getAssignmentsReport | Export-Csv -Path .\GetAssignmentsReport.csv -NoTypeInformation
Write-Host "Report file(GetAssignmentsReport.csv) is generated at $directoryPath\GetAssignmentsReport.csv"
Write-Host "Updated Class details file($($directoryPathOfFile)) and generated updated file is at $($directoryPathOfFile)"
```
