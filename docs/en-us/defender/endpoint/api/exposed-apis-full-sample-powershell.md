<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-full-sample-powershell -->
<!-- Sitemap-Last-Modified: 2026-02-27 -->

# Microsoft Defender for Endpoint APIs using PowerShell

Important

Advanced hunting capabilities aren't included in Microsoft Defender for Business.

Note

If you're a US Government customer, use the URIs listed in [Microsoft Defender for Endpoint for US Government customers](https://learn.microsoft.com/en-us/defender-endpoint/gov#api).

Tip

For better performance, instead of using api.security.microsoft.com, use a server closer to your geolocation:

- us.api.security.microsoft.com
- eu.api.security.microsoft.com
- uk.api.security.microsoft.com
- au.api.security.microsoft.com
- swa.api.security.microsoft.com
- ina.api.security.microsoft.com
- aea.api.security.microsoft.com

Full scenario using multiple APIs from Microsoft Defender for Endpoint.

In this section, we share PowerShell samples to:

- Retrieve a token.
- Use token to retrieve the latest alerts in Microsoft Defender for Endpoint.
- For each alert, if the alert has medium or high priority and is still in progress, check how many times the device has connected to suspicious URL.

**Prerequisite**: You first need to [create an app](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro).

## Preparation instructions

1. Open a PowerShell window.
2. If your policy doesn't allow you to run the PowerShell commands, you can run the following command:

   ```powershell
   Set-ExecutionPolicy -ExecutionPolicy Bypass
   ```

For more information, see [PowerShell documentation](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.security/set-executionpolicy).

## Get token

Run the following command, using your information as follows:

- `$tenantId`: ID of the tenant on behalf of which you want to run the query \(that is, the query is run on the data of this tenant\).
- `$appId`: ID of your Microsoft Entra app \(the app must have 'Run advanced queries' permission to Defender for Endpoint\).
- `$appSecret`: Secret of your Microsoft Entra app.
- `$suspiciousUrl`: The URL.

Tip

Some Microsoft Defender for Endpoint APIs continue to require access tokens issued for the legacy resource `https://api.securitycenter.microsoft.com`. If the token audience doesn't match the resource expected by the API, requests fail with `403 Forbidden`, even if the API endpoint uses `https://api.security.microsoft.com`. Use `https://api.securitycenter.microsoft.com` as the resource or scope when acquiring tokens.

```powershell
$tenantId = '00000000-0000-0000-0000-000000000000' # Paste your own tenant ID here
$appId = '11111111-1111-1111-1111-111111111111' # Paste your own app ID here
$appSecret = '22222222-2222-2222-2222-222222222222' # Paste your own app secret here
$suspiciousUrl = 'www.suspiciousUrl.com' # Paste your own URL here

$resourceAppIdUri = 'https://api.securitycenter.microsoft.com'
$oAuthUri = "https://login.microsoftonline.com/$TenantId/oauth2/token"
$authBody = [Ordered] @{
    resource = "$resourceAppIdUri"
    client_id = "$appId"
    client_secret = "$appSecret"
    grant_type = 'client_credentials'
}
$authResponse = Invoke-RestMethod -Method Post -Uri $oAuthUri -Body $authBody -ErrorAction Stop
$aadToken = $authResponse.access_token

#Get latest alert
$alertUrl = "https://api.security.microsoft.com/api/alerts?`$top=10"
$headers = @{
    'Content-Type' = 'application/json'
    Accept = 'application/json'
    Authorization = "Bearer $aadToken"
}
$alertResponse = Invoke-WebRequest -Method Get -Uri $alertUrl -Headers $headers -ErrorAction Stop
$alerts =  ($alertResponse | ConvertFrom-Json).value

$machinesToInvestigate = New-Object System.Collections.ArrayList

Foreach($alert in $alerts)
{
    #echo $alert.id $alert.machineId    $alert.severity $alert.status

    $isSevereAlert = $alert.severity -in 'Medium', 'High'
    $isOpenAlert = $alert.status -in 'InProgress', 'New'
    if($isOpenAlert -and $isSevereAlert)
    {
        if (-not $machinesToInvestigate.Contains($alert.machineId))
        {
            $machinesToInvestigate.Add($alert.machineId) > $null
        }
    }
}

$commaSeparatedMachines = '"{0}"' -f ($machinesToInvestigate -join '","')

$query = "NetworkCommunicationEvents
| where MachineId in ($commaSeparatedMachines)
| where RemoteUrl  == `"$suspiciousUrl`"
| summarize ConnectionsCount = count() by MachineId"

$queryUrl = "https://api.security.microsoft.com/api/advancedqueries/run"

$queryBody = ConvertTo-Json -InputObject @{ 'Query' = $query }
$queryResponse = Invoke-WebRequest -Method Post -Uri $queryUrl -Headers $headers -Body $queryBody -ErrorAction Stop
$response =  ($queryResponse | ConvertFrom-Json).Results
$response
```

## See also

- [Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)
- [Advanced Hunting API](https://learn.microsoft.com/en-us/defender-endpoint/api/run-advanced-query-api)
- [Advanced Hunting using Python](https://learn.microsoft.com/en-us/defender-endpoint/api/run-advanced-query-sample-python)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bd-p/MicrosoftDefenderATP).
