<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-capabilities-ids -->
<!-- Sitemap-Last-Modified: 2026-05-11 -->

# Retrieving capabilities IDs for declarative agent manifest

This article describes methods for developers to retrieve the necessary IDs to include Copilot connectors and SharePoint/OneDrive files within the `capabilities` section of their [declarative agent manifest](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8). Developers can use [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) or [Microsoft Graph PowerShell](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview).

## Microsoft 365 Copilot connectors

This section describes how developers can retrieve the value to set in the `connection_id` property of the [Connection object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#connection-object) in the [Copilot connectors object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#copilot-connectors-object) in the manifest.

Important

Querying for Microsoft 365 Copilot connectors requires an admin account.

- [Graph Explorer](#tabpanel_1_explorer)
- [PowerShell](#tabpanel_1_powershell)

1. Browse to [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) and sign in with your admin account.

   ![A screenshot of the Graph Explorer sign in button](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/declarative-agents/graph-explorer-sign-in.png)
2. Select your user avatar in the upper right corner and select **Consent to permissions**.

   ![A screenshot of the user profile flyout in Graph Explorer](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/declarative-agents/graph-explorer-consent-to-permissions.png)
3. Search for `ExternalConnection.Read.All` and select **Consent** for that permission. Follow the prompts to grant consent.

   ![A screenshot of Graph Explorer's permission consent dialog with ExternalConnection.Read.All](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/declarative-agents/graph-explorer-external-connection-permission.png)
4. Enter `https://graph.microsoft.com/v1.0/external/connections?$select=id,name` in the request field and select **Run query**.

   ![A screenshot of Graph Explorer's request field with the connections query](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/declarative-agents/graph-explorer-get-connections.png)
5. Locate the connector you want and copy its `id` property. For example, to use the **GitHub Repos** connector in the following response, copy the `githubrepos` value.

   ```json
   {
     "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#connections(id,name)",
     "value": [
       {
         "id": "applianceparts",
         "name": "Appliance Parts Inventory"
       },
       {
         "id": "githubrepos",
         "name": "GitHub Repos"
       }
     ]
   }
   ```

1. Copy the following code into a new file named **GetGraphConnectorIds.ps1**.

   ```powershell
   param(
       [Parameter(Mandatory = $false)]
       [Switch]
       $StayConnected = $false
   )

   # Requires an admin
   Connect-MgGraph -Scopes "ExternalConnection.Read.All" `
       -UseDeviceCode -ErrorAction Stop -NoWelcome

   Get-MgExternalConnection -Property "Name", "Id" | Format-Table "Name", "Id"

   if ($StayConnected -eq $false) {
       Disconnect-MgGraph | Out-Null
       Write-Host "Disconnected from Microsoft Graph"
   }
   else {
       Write-Host
       Write-Host -ForegroundColor Yellow `
           "The connection to Microsoft Graph is still active. To disconnect, use Disconnect-MgGraph"
   }
   ```

2. Open [PowerShell 7](https://learn.microsoft.com/en-us/powershell/scripting/overview) in the directory where **GetGraphConnectorIds.ps1** is located and run the script with the following command.

   ```powershell
   .\GetGraphConnectorIds.ps1
   ```

3. Open your browser and browse to `https://microsoft.com/devicelogin`. Enter the code that is provided by the prompt and complete the sign-in and consent flow.

   ```powershell
   To sign in, use a web browser to open the page https://microsoft.com/devicelogin and enter the code BQGGRREGN to authenticate.
   ```

4. Locate the connector you want and copy its `Id` property. For example, to use the **GitHub Repos** connector in the following response, copy the `githubrepos` value.

   ```powershell
   Name                      Id
   ----                      --
   Appliance Parts Inventory applianceparts
   GitHub Repos              githubrepos
   ```

## Retrieving SharePoint IDs

This section describes how developers can retrieve the value to set in the following properties within the `items_by_sharepoint_ids` property of the [`OneDriveAndSharePoint` object](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.8#onedrive-and-sharepoint-object):

- `site_id`
- `list_id`
- `web_id`
- `unique_id`

- [Graph Explorer](#tabpanel_2_explorer)
- [PowerShell](#tabpanel_2_powershell)

1. Browse to [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) and sign in with your admin account.
2. Select your user avatar in the upper right corner and select **Consent to permissions**.
3. Search for `Sites.Read.All` and select **Consent** for that permission. Follow the prompts to grant consent. Repeat this process for `Files.Read.All`.

   ![A screenshot of Graph Explorer's permission consent dialog with Sites.Read.All](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/declarative-agents/graph-explorer-sites-permission.png)
4. Change the method dropdown to **POST** and enter `https://graph.microsoft.com/v1.0/search/query` in the request field.

   ![A screenshot of Graph Explorer's request field with a search query](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/declarative-agents/graph-explorer-post-query.png)
5. Add the following in the **Request body**, replacing `https://yoursharepointsite.com/sites/YourSite/Shared%20Documents/YourFile.docx` with the URL to the file or folder you want to get IDs for.

   ```json
   {
     "requests": [
       {
         "entityTypes": [
           "driveItem"
         ],
         "query": {
           "queryString": "Path:\"https://yoursharepointsite.com/sites/YourSite/Shared%20Documents/YourFile.docx\""
         },
         "fields": [
           "fileName",
           "listId",
           "webId",
           "siteId",
           "uniqueId"
         ]
       }
     ]
   }
   ```

6. Select **Run query**.
7. Locate the file you want and copy its `listId`, `webId`, `siteId`, and `uniqueId` properties.

   ```json
   {
     "value": [
       {
         "searchTerms": [],
         "hitsContainers": [
           {
             "hits": [
               {
                 "hitId": "01AJOINAHZHINTBHPESZBISPIPSJG3D5EO",
                 "rank": 1,
                 "summary": "Reorder policy Our reorder policy for suppliers is straightforward and designed to maintain cost-efficiency and inventory control. We kindly request that no order exceeds a total",
                 "resource": {
                   "@odata.type": "#microsoft.graph.driveItem",
                   "listItem": {
                     "@odata.type": "#microsoft.graph.listItem",
                     "id": "301b3af9-e49d-4296-893d-0f924db1f48e",
                     "fields": {
                       "fileName": "YourFile.docx",
                       "listId": "12fde922-4fab-4238-8227-521829cd1099",
                       "webId": "a25fab47-f3b9-4fa3-8ed9-1acb83c12a4f",
                       "siteId": "5863dfa5-b39d-4cd1-92a6-5cf539e04971",
                       "uniqueId": "{301b3af9-e49d-4296-893d-0f924db1f48e}"
                     }
                   }
                 }
               }
             ],
             "total": 1,
             "moreResultsAvailable": false
           }
         ]
       }
     ]
   }
   ```

1. Copy the following code into a new file named **GetSharePointIds.ps1**.

   ```powershell
   param(
       [Parameter(Mandatory = $true,
       HelpMessage = "The URL path to the file or folder to search for")]
       [String]
       $FilePath,

       [Parameter(Mandatory = $false)]
       [Switch]
       $StayConnected = $false
   )

   Connect-MgGraph -Scopes "Sites.Read.All Files.Read.All" `
       -UseDeviceCode -ErrorAction Stop -NoWelcome

   $searchQuery = @{
       requests = @(
           @{
               entityTypes = @("driveItem")
               query = @{
                   queryString = "Path:""" + $FilePath +  """"
               }
               fields = @(
                   "fileName"
                   "listId"
                   "webId"
                   "siteId"
                   "uniqueId"
               )
           }
       )
   }

   $results = Invoke-MgQuerySearch -Body $searchQuery

   foreach($hitContainer in $results.HitsContainers)
   {
       foreach($hit in $hitContainer.Hits)
       {
           Write-Output $hit.Resource.AdditionalProperties["listItem"]["fields"] | Format-Table
       }
   }

   if ($StayConnected -eq $false) {
       Disconnect-MgGraph | Out-Null
       Write-Host "Disconnected from Microsoft Graph"
   }
   else {
       Write-Host
       Write-Host -ForegroundColor Yellow `
           "The connection to Microsoft Graph is still active. To disconnect, use Disconnect-MgGraph"
   }
   ```

2. Open [PowerShell 7](https://learn.microsoft.com/en-us/powershell/scripting/overview) in the directory where **GetSharePointIds.ps1** is located and run the script with the following command, replacing `https://yoursharepointsite.com/sites/YourSite/Shared%20Documents/YourFile.docx` with the URL to the file or folder you want to get IDs for.

   ```powershell
   .\GetSharePointIds.ps1 -FilePath "https://yoursharepointsite.com/sites/YourSite/Shared%20Documents/YourFile.docx"
   ```

3. Open your browser and browse to `https://microsoft.com/devicelogin`. Enter the code that is provided by the prompt and complete the sign-in and consent flow.

   ```powershell
   To sign in, use a web browser to open the page https://microsoft.com/devicelogin and enter the code BQGGRREGN to authenticate.
   ```

4. Locate the file you want and copy its values.

   ```powershell
   Key      Value
   ---      -----
   fileName YourFile.docx
   listId   12fde922-4fab-4238-8227-521829cd1099
   webId    a25fab47-f3b9-4fa3-8ed9-1acb83c12a4f
   siteId   5863dfa5-b39d-4cd1-92a6-5cf539e04971
   uniqueId {301b3af9-e49d-4296-893d-0f924db1f48e}
   ```
