<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-import-export-skills -->
<!-- Sitemap-Last-Modified: 2026-09-04 -->

# Import or export People Skills

You can import skills for a user from third-party platforms and export a user's confirmed skills using the Microsoft Graph API. Also, you can export a user's confirmed skills.

## Import user skills

You can import user skills from third party systems. The imported skills display on that user's skills profile as *Imported by your organization* and can be confirmed by a user. Once confirmed, imported skills behave the same as all confirmed skills.

User skills from external systems can be imported as an attribute while uploading organizational data into Microsoft 365.

Important

The **Imported by your organization** label is shown only in the **Live Profile Editor**. On the **Live Profile Card \("You" card\)**, imported skills aren't visually differentiated from inferred skills and appear in the same skills experience.

Review the below guideline on how you can use the tool to import user skills:

1. Open the [Organization data ingestion tool](https://learn.microsoft.com/en-us/viva/import-orgdata) in the admin center and download the .csv template. In the admin center, click **Setup** > **Migration and imports**.
2. In the organization data ingestion tool template, list all the users for whom you need skills to be imported, and list each user's skills under the attribute **Microsoft\_UserSkillNames**. For more information, see [organization data field in the template](https://learn.microsoft.com/en-us/viva/orgdata-attributes).

   Note

   The skill names in attribute **Microsoft\_UserSkillNames**, need to exactly match the English translation of the skill names that exist in your skills library. Your skills library consists of the out-of-the-box library and the optional custom skills library.
3. Make a copy of all the user skills and add them to People Skills library as custom skills. For more information, see [how to add custom skills](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-manage-custom-skill).
4. Import the user skills data into Microsoft 365 using the .csv upload.

## Export **Custom** or **Default** Skills Library

1. Go to the Microsoft Admin Center > [Manage Skills](https://admin.cloud.microsoft/?#/viva/manage-skills).
2. Select **Export library**
3. Select to either export a Custom, Default or both libraries

Exporting libraries can be useful if you would like to source control your library in an external tool.

Note

Only **People Skills - Advanced** Service Plan customers will be able export the **Default** Skills library.

You must have already imported a **Custom** Skills library to be able to export it.

## Export confirmed user skills with the Microsoft Graph Profile API

This section explains how administrators can retrieve and export users’ confirmed skills through the Microsoft Graph Profile API. It first walks through using Graph Explorer to view the confirmed skills for an individual user, then provides a PowerShell-based workflow for exporting skills for one or more users in bulk. Along the way, you’ll review the required tools and permissions, learn how to obtain and protect a short-lived Microsoft Graph access token, run and interpret the included GetAllSkills.ps1 script, and troubleshoot common execution-policy issues.

Note

Only confirmed skills can be exported. AI-generated \(inferred\) skills can’t be exported.

### **View confirmed skills for one user**

Use Graph Explorer to retrieve and review one user’s confirmed skills through the Microsoft Graph Profile API. Sign in, run a request using the user’s ID or user principal name \(UPN\), and review the displayName value for each confirmed skill in the response.

**To view confirmed skills for a user**

1. Open [Graph Explorer.](https://developer.microsoft.com/graph/graph-explorer)
2. Sign in with your work account.
3. In the request URL, replace {user-id-or-upn} with the user’s ID or user principal name \(UPN\).
4. Run the following request:

   `GET https://graph.microsoft.com/beta/users/{user-id-or-upn}/profile/skills `
5. Review the response for the user’s confirmed skills. Each skill includes a displayName value.

### **Export confirmed skills for one or more users**

Admins can export confirmed skills from the MS Graph API for all of their users. We have provided a python script below that you can use in PowerShell for this. Use the script GetAllSkills.ps1 to retrieve the display names of confirmed Viva Skills for one or more users. The script calls the /beta/users/{userId}/profile/skills endpoint for each user.

**Before you begin**

- PowerShell 7.
- A Microsoft Graph access token with permission to read the target users’ profiles, such as delegated *User.Read.All*. Your organization might require administrator consent.

**To export skills for one or more users**

1. Open **[Graph Explorer](https://developer.microsoft.com/graph/graph-explorer)**.
2. Sign in with your work account.
3. Run the following request to make an access token available in Graph Explorer:

   `GET https://graph.microsoft.com/v1.0/me`
4. Go to the **Access token** tab and copy the token. Microsoft Graph access tokens are short-lived. If the script returns the error “401 Unauthorized,” get a new token and try again. The .token.txt file contains a live credential. Don’t share the file or commit it to source control. Delete it when you finish.
5. Copy the *GetAllSkills.ps1 Script* below into a file named **GetAllSkills.ps1** and save the file in a working folder, such as C:\\GraphSkills. If you received a ZIP folder, extract it first.
6. In the same folder, create a file named **.token.txt**.
7. Paste the access token into .token.txt and save the file.
8. Open **PowerShell 7**.
9. Go to the folder where you saved GetAllSkills.ps1:

   `cd C:\GraphSkills`
10. Run the script by using the command that matches your scenario:

    1. For a single user

       `.\GetAllSkills.ps1 "`[`user@contoso.com`](mailto:user@contoso.com)`"`
    2. For multiple users

       `.\GetAllSkills.ps1 "`[`user1@contoso.com`](mailto:user1@contoso.com)`, `[`user2@contoso.com`](mailto:user2@contoso.com)`"`

#### **GetAllSkills.ps1 Script**

```
<# 
.SYNOPSIS 
    Retrieves the display names of confirmed skills for one or more users from 
    Microsoft Graph, filtered to Viva Skills. 
  
.PARAMETER Users 
    A comma-separated list of user IDs / UPNs. 
  
.PARAMETER TokenFile 
    Path to a file containing the Microsoft Graph bearer token. Defaults to 
    ".token.txt" in the same folder as the script. 
  
.EXAMPLE 
    .\GetAllSkills.ps1 "
#> 
[CmdletBinding()] 
param( 
    [Parameter(Mandatory = $true, Position = 0)] 
    [string]$Users, 
  
    [Parameter()] 
    [string]$TokenFile 
) 
  
$ErrorActionPreference = 'Stop' 
  
if ([string]::IsNullOrWhiteSpace($TokenFile)) { 
    $scriptDir = if ($PSScriptRoot) { $PSScriptRoot } else { Split-Path -Parent $MyInvocation.MyCommand.Path } 
    $TokenFile = Join-Path $scriptDir ".token.txt" 
} 
  
# Well-known Viva Skills source id used to filter user skills. 
$SourceId = "75d4238e-b142-4d2d-aed9-232b830b8706" 
  
function Get-GraphAccessToken { 
    if (-not (Test-Path -Path $TokenFile)) { 
        throw "Token file '$TokenFile' not found. Store a valid access token in it." 
    } 
  
    $token = (Get-Content -Path $TokenFile -Raw) 
    $token = ($token -replace '^\s*Bearer\s+', '').Trim() 
    if ([string]::IsNullOrWhiteSpace($token)) { 
        throw "Token file '$TokenFile' is empty. Store a valid access token in it." 
    } 
  
    Write-Host "Token read from '$TokenFile' ($($token.Length) chars)." 
    return $token 
} 
  
# Parse and normalize the comma-separated user list. 
$userList = $Users -split ',' | 
    ForEach-Object { $_.Trim() } | 
    Where-Object { $_ -ne '' } 
  
if ($userList.Count -eq 0) { 
    throw "No users were supplied. Provide a comma-separated list of user IDs/UPNs." 
} 
  
$token = Get-GraphAccessToken 
$headers = @{ Authorization = "Bearer $token" } 
  
$results = foreach ($user in $userList) { 
    $encodedUser = [System.Uri]::EscapeDataString($user) 
    $uri = "
  
    try { 
        $skills = @() 
        do { 
            $response = Invoke-RestMethod -Uri $uri -Headers $headers -Method Get 
            if ($response.value) { 
                $skills += $response.value 
            } 
            $uri = 
        } while ($uri) 
    } 
    catch { 
        Write-Warning "Failed to retrieve skills for '$user': $($_.Exception.Message)" 
        continue 
    } 
  
    $matched = @($skills | Where-Object { 
        ($_.source.type -contains "SkillsInViva") -and 
        ($_.sources.sourceId -contains $SourceId) 
    }) 
    Write-Host "$user : $($skills.Count) skill(s) total, $($matched.Count) matching." 
  
    foreach ($skill in $matched) { 
        $skill.displayName 
    } 
} 
  
if (-not $results -or @($results).Count -eq 0) { 
    Write-Host "No skills matched for the supplied user(s)." 
} else { 
    Write-Host "" 
    ($results -join ", ") 
} 
```

### **Troubleshooting**

If PowerShell reports that the script isn’t digitally signed, run the following command to change the execution policy for the current session. Then run the script again.

`Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass`

Review the output. The script displays a summary for each user, followed by a comma-separated list of matching skill names. If no skills match, the script reports that it found no matching skills.

## Import **Custom** Skills Library

See the [step by step guide.](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-manage-custom-skill)
