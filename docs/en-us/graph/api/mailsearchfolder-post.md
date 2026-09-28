<!-- Source: https://learn.microsoft.com/en-us/graph/api/mailsearchfolder-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create mailSearchFolder

Namespace: microsoft.graph

Create a new [mailSearchFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailsearchfolder?view=graph-rest-1.0) in the specified user's mailbox.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Mail.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Mail.ReadWrite | Not available. |
| Application | Mail.ReadWrite | Not available. |

## HTTP request

```http
POST /me/mailFolders/{id}/childFolders
POST /users/{id | userPrincipalName}/mailFolders/{id}/childFolders
```

Specify the parent folder in the query URL as a folder ID, or a well-known folder name. For a list of supported well-known folder names, see [mailFolder resource type](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0).

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | `Bearer {token}`. Required. |
| Content-Type | `application/json`. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| @odata.type | String | The type of folder to be created. Set to "microsoft.graph.mailSearchFolder". |
| displayName | String | The display name of the new folder. |
| includeNestedFolders | Boolean | Indicates how the mailbox folder hierarchy should be traversed in the search. `true` means that a deep search should be done to include child folders in the hierarchy of each folder explicitly specified in **sourceFolderIds**. `false` means a shallow search of only each of the folders explicitly specified in **sourceFolderIds**. |
| sourceFolderIds | String collection | The mailbox folders that should be mined. |
| filterQuery | String | The OData query to filter the messages. |

## Response

If successful, this method returns a `201 Created` response code and a [mailSearchFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailsearchfolder?view=graph-rest-1.0) object in the response body.

## Example

#### Request

The following is an example of the request - it creates a search folder of messages that contain the string "weekly digest" in the subject. The search folder is under the same folder on which the specified filter query applies.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/mailFolders/AQMkADYAAAIBDAAAAA==/childFolders
Content-type: application/json

{
  "@odata.type": "microsoft.graph.mailSearchFolder",
  "displayName": "Weekly digests",
  "includeNestedFolders": true,
  "sourceFolderIds": ["AQMkADYAAAIBDAAAAA=="],
  "filterQuery": "contains(subject, 'weekly digest')"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new MailSearchFolder
{
	OdataType = "microsoft.graph.mailSearchFolder",
	DisplayName = "Weekly digests",
	IncludeNestedFolders = true,
	SourceFolderIds = new List<string>
	{
		"AQMkADYAAAIBDAAAAA==",
	},
	FilterQuery = "contains(subject, 'weekly digest')",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.MailFolders["{mailFolder-id}"].ChildFolders.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewMailFolder()
displayName := "Weekly digests"
requestBody.SetDisplayName(&displayName) 
includeNestedFolders := true
requestBody.SetIncludeNestedFolders(&includeNestedFolders) 
sourceFolderIds := []string {
	"AQMkADYAAAIBDAAAAA==",
}
requestBody.SetSourceFolderIds(sourceFolderIds)
filterQuery := "contains(subject, 'weekly digest')"
requestBody.SetFilterQuery(&filterQuery) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
childFolders, err := graphClient.Me().MailFolders().ByMailFolderId("mailFolder-id").ChildFolders().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MailSearchFolder mailFolder = new MailSearchFolder();
mailFolder.setOdataType("microsoft.graph.mailSearchFolder");
mailFolder.setDisplayName("Weekly digests");
mailFolder.setIncludeNestedFolders(true);
LinkedList<String> sourceFolderIds = new LinkedList<String>();
sourceFolderIds.add("AQMkADYAAAIBDAAAAA==");
mailFolder.setSourceFolderIds(sourceFolderIds);
mailFolder.setFilterQuery("contains(subject, 'weekly digest')");
MailFolder result = graphClient.me().mailFolders().byMailFolderId("{mailFolder-id}").childFolders().post(mailFolder);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const mailFolder = {
  '@odata.type': 'microsoft.graph.mailSearchFolder',
  displayName: 'Weekly digests',
  includeNestedFolders: true,
  sourceFolderIds: ['AQMkADYAAAIBDAAAAA=='],
  filterQuery: 'contains(subject, \'weekly digest\')'
};

await client.api('/me/mailFolders/AQMkADYAAAIBDAAAAA==/childFolders')
	.post(mailFolder);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\MailSearchFolder;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MailSearchFolder();
$requestBody->setOdataType('microsoft.graph.mailSearchFolder');
$requestBody->setDisplayName('Weekly digests');
$requestBody->setIncludeNestedFolders(true);
$requestBody->setSourceFolderIds(['AQMkADYAAAIBDAAAAA==', 	]);
$requestBody->setFilterQuery('contains(subject, \'weekly digest\')');

$result = $graphServiceClient->me()->mailFolders()->byMailFolderId('mailFolder-id')->childFolders()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Mail

$params = @{
	"@odata.type" = "microsoft.graph.mailSearchFolder"
	displayName = "Weekly digests"
	includeNestedFolders = $true
	sourceFolderIds = @(
	"AQMkADYAAAIBDAAAAA=="
)
filterQuery = "contains(subject, 'weekly digest')"
}

# A UPN can also be used as -UserId.
New-MgUserMailFolderChildFolder -UserId $userId -MailFolderId $mailFolderId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.mail_search_folder import MailSearchFolder
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MailSearchFolder(
	odata_type = "microsoft.graph.mailSearchFolder",
	display_name = "Weekly digests",
	include_nested_folders = True,
	source_folder_ids = [
		"AQMkADYAAAIBDAAAAA==",
	],
	filter_query = "contains(subject, 'weekly digest')",
)

result = await graph_client.me.mail_folders.by_mail_folder_id('mailFolder-id').child_folders.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('68ca8ec0-11f8-456b-a785-70d9936650d5')/mailFolders('AQMkADYAAAIBDAAAAA%3D%3D')/childFolders/$entity",
    "@odata.type": "#microsoft.graph.mailSearchFolder",
    "id": "AAMkADYfRAAAZg1yTAAA=",
    "displayName": "Weekly digests",
    "parentFolderId": "AQMkADYAAAIBDAAAAA==",
    "childFolderCount": 0,
    "unreadItemCount": 0,
    "totalItemCount": 0,
    "isSupported": true,
    "includeNestedFolders": true,
    "sourceFolderIds": [
        "AQMkADYAAAIBDAAAAA=="
    ],
    "filterQuery": "contains(subject, 'weekly digest')"
}
```
