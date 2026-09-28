<!-- Source: https://learn.microsoft.com/en-us/graph/api/mailboxfolder-list-childfolders?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# List childFolders

Namespace: microsoft.graph

Get the [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) collection under the specified [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) in a mailbox.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | MailboxFolder.Read | MailboxFolder.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | MailboxFolder.Read.All | MailboxFolder.ReadWrite.All |

## HTTP request

```http
GET /admin/exchange/mailboxes/{mailboxId}/folders/{mailboxFolderId}/childFolders
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$top`, `$skip`, `$orderby`, `$count`, and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows how to get the mailbox folder collection under a specified folder.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0643f21@a7809c93/folders/NJWt2LeVEAAAIBDAAAAA==/childFolders
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Exchange.Mailboxes["{mailbox-id}"].Folders["{mailboxFolder-id}"].ChildFolders.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
childFolders, err := graphClient.Admin().Exchange().Mailboxes().ByMailboxId("mailbox-id").Folders().ByMailboxFolderId("mailboxFolder-id").ChildFolders().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MailboxFolderCollectionResponse result = graphClient.admin().exchange().mailboxes().byMailboxId("{mailbox-id}").folders().byMailboxFolderId("{mailboxFolder-id}").childFolders().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let childFolders = await client.api('/admin/exchange/mailboxes/MBX:e0643f21@a7809c93/folders/NJWt2LeVEAAAIBDAAAAA==/childFolders')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->admin()->exchange()->mailboxes()->byMailboxId('mailbox-id')->folders()->byMailboxFolderId('mailboxFolder-id')->childFolders()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.admin.exchange.mailboxes.by_mailbox_id('mailbox-id').folders.by_mailbox_folder_id('mailboxFolder-id').child_folders.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 232

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#admin/exchange/mailboxes/MBX:e0643f21@a7809c93/folders('NJWt2LeVEAAAIBDAAAAA==')/childFolders",
    "value": [
        {
            "@odata.type": "#microsoft.graph.mailboxFolder",
            "id": "EDSVrdi3lRAAEvNS16AAA=",
            "displayName": "Folder_1",
            "parentFolderId": "NJWt2LeVEAAAIBDAAAAA==",
            "parentMailboxUrl": "https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0643f21@a7809c93",
            "childFolderCount": 0,
            "totalItemCount": 20,
            "wellKnownName": null,
            "type": "IPF.Note"
        },
        {
            "@odata.type": "#microsoft.graph.mailboxFolder",
            "id": "EDSVrdi3lRAAEED0yTAAA=",
            "displayName": "Folder_2",
            "parentFolderId": "NJWt2LeVEAAAIBDAAAAA==",
            "parentMailboxUrl": "https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0643f21@a7809c93",
            "childFolderCount": 0,
            "totalItemCount": 1,
            "wellKnownName": null,
            "type": "IPF.Note"
        }
    ]
}
```
