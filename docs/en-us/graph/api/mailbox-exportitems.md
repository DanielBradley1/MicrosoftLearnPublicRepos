<!-- Source: https://learn.microsoft.com/en-us/graph/api/mailbox-exportitems?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# mailbox: exportItems

Namespace: microsoft.graph

Export Exchange [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) objects in full fidelity. This API exports each item as an opaque stream. The data stream isn't intended for parsing, but can be used to import an item back into an Exchange mailbox. For more information, see [Overview of the mailbox import and export APIs in Microsoft Graph](https://learn.microsoft.com/en-us/graph/mailbox-import-export-concept-overview).

You can export up to 20 items in a single export request.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | MailboxItem.Export | MailboxItem.ImportExport |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | MailboxItem.Export.All | MailboxItem.ImportExport.All |

## HTTP request

```http
POST /admin/exchange/mailboxes/{mailboxId}/exportItems
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| itemIds | String collection | A collection of identifiers of [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) objects to export. All identifiers in the collection *must* be for items in the same mailbox. The maximum size of this collection is 20 strings. |

## Response

If successful, this action returns a `200 OK` response code and a collection of [exportItemResponse](https://learn.microsoft.com/en-us/graph/api/resources/exportitemresponse?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example exports two items present in the user's mailbox. The **itemIds** of the items to be exported are specified in the request body.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0643f21@a7809c93/exportItems
Content-type: application/json

{
    "itemIds": [
        "EDSVrdi3lRAADmpnf1AAA=",
        "EDSVrdi3lRAAD45b7RAAA="
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Admin.Exchange.Mailboxes.Item.ExportItems;

var requestBody = new ExportItemsPostRequestBody
{
	ItemIds = new List<string>
	{
		"EDSVrdi3lRAADmpnf1AAA=",
		"EDSVrdi3lRAAD45b7RAAA=",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Exchange.Mailboxes["{mailbox-id}"].ExportItems.PostAsExportItemsPostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  //other-imports
)

requestBody := graphadmin.NewExportItemsPostRequestBody()
itemIds := []string {
	"EDSVrdi3lRAADmpnf1AAA=",
	"EDSVrdi3lRAAD45b7RAAA=",
}
requestBody.SetItemIds(itemIds)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
exportItems, err := graphClient.Admin().Exchange().Mailboxes().ByMailboxId("mailbox-id").ExportItems().PostAsExportItemsPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.admin.exchange.mailboxes.item.exportitems.ExportItemsPostRequestBody exportItemsPostRequestBody = new com.microsoft.graph.admin.exchange.mailboxes.item.exportitems.ExportItemsPostRequestBody();
LinkedList<String> itemIds = new LinkedList<String>();
itemIds.add("EDSVrdi3lRAADmpnf1AAA=");
itemIds.add("EDSVrdi3lRAAD45b7RAAA=");
exportItemsPostRequestBody.setItemIds(itemIds);
var result = graphClient.admin().exchange().mailboxes().byMailboxId("{mailbox-id}").exportItems().post(exportItemsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const exportItemResponse = {
    itemIds: [
        'EDSVrdi3lRAADmpnf1AAA=',
        'EDSVrdi3lRAAD45b7RAAA='
    ]
};

await client.api('/admin/exchange/mailboxes/MBX:e0643f21@a7809c93/exportItems')
	.post(exportItemResponse);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Exchange\Mailboxes\Item\ExportItems\ExportItemsPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ExportItemsPostRequestBody();
$requestBody->setItemIds(['EDSVrdi3lRAADmpnf1AAA=', 'EDSVrdi3lRAAD45b7RAAA=', 	]);

$result = $graphServiceClient->admin()->exchange()->mailboxes()->byMailboxId('mailbox-id')->exportItems()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.exchange.mailboxes.item.export_items.export_items_post_request_body import ExportItemsPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ExportItemsPostRequestBody(
	item_ids = [
		"EDSVrdi3lRAADmpnf1AAA=",
		"EDSVrdi3lRAAD45b7RAAA=",
	],
)

result = await graph_client.admin.exchange.mailboxes.by_mailbox_id('mailbox-id').export_items.post(request_body)
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
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.exportItemResponse)",
    "value": [
        {
            "itemId": "EDSVrdi3lRAADmpnf1AAA=",
            "changeKey": "CQAAABYAAACQ2fKdhq8oSKEDSVrdi3lRAAEu4C+G",
            "data": "VGhpcyBpcyBhIHRlc3QgZGF0YSB0aGF0IHdpbGwgYmUgY29udmVydGVkIHRvIGEgQmFzZTY0IHN0cmVhbQ=="
        },
        {
            "itemId": "EDSVrdi3lRAAD45b7RAAA=",
            "changeKey": "CQAAABYAAACQ2fKdhq8oSKEDSVrdi3lRAAD4pUax",
            "data": "VGhpcyBpcyBhIHRlc3QgZGF0YSB0aGF0IHdpbGwgYmUgY29udmVydGVkIHRvIGEgQmFzZTY0IHN0cmVhbQ=="
        }
    ]
}
```
