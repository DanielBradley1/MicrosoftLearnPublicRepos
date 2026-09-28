<!-- Source: https://learn.microsoft.com/en-us/graph/api/mailboxitem-delta?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# mailboxItem: delta

Namespace: microsoft.graph

Get a set of [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) objects that were added, deleted, or updated in a specified [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0).

A **delta** function call for items in a folder is similar to a GET request, except that by appropriately applying [state tokens](https://learn.microsoft.com/en-us/graph/delta-query-overview) in one or more of these calls, you can [query for incremental changes in the items in that folder](https://learn.microsoft.com/en-us/graph/delta-query-messages). This approach allows you to maintain and synchronize a local store of a user's mailbox items without having to fetch the entire set of items from the server every time.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | MailboxItem.Read | MailboxItem.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | MailboxItem.Read.All | MailboxItem.ReadWrite.All |

## HTTP request

```http
GET /admin/exchange/mailboxes/{mailboxId}/folders/{mailboxFolderId}/items/delta
```

## Query parameters

Tracking changes in items incurs a round of one or more **delta** function calls. If you use any query parameter \(other than `$deltaToken` and `$skipToken`\), you must specify it in the initial **delta** request. Microsoft Graph automatically encodes any specified parameters into the token portion of the `nextLink` or `deltaLink` URL provided in the response. You only need to specify any desired query parameters once upfront. In subsequent requests, simply copy and apply the `nextLink` or `deltaLink` URL from the previous response, as that URL already includes the encoded, desired parameters.

| Parameter | Description |
| :--- | :--- |
| $deltaToken | A [state token](https://learn.microsoft.com/en-us/graph/delta-query-overview) returned in the `deltaLink` URL of the previous **delta** function call for the same item collection, which indicates the completion of that round of change tracking. Save and apply the entire `deltaLink` URL including this token in the first request of the next round of change tracking for that collection. |
| $skipToken | A [state token](https://learn.microsoft.com/en-us/graph/delta-query-overview) returned in the `nextLink` URL of the previous **delta** function call, indicating further changes are available to be tracked in the same item collection. |

### OData query parameters

- You can use the `$select` query parameter to specify only the properties you need for best performance. The **id** property is always returned.
- This delta query supports the `$select` and `$top` query parameters for items.
- Limited support exists for `$filter` and `$orderby`:

  - The only supported `$filter` expressions are `$filter=receivedDateTime+ge+{value}` and `$filter=receivedDateTime+gt+{value}`.
  - The only supported `$orderby` expression is `$orderby=receivedDateTime+desc`. If you don't include an `$orderby` expression, the return order isn't guaranteed.

- The `$search` query parameter isn't supported.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Prefer | odata.maxpagesize={x}. Optional. Controls page size. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a collection of [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows how to make a single **delta** function call and limit the maximum number of items in the response body to two.

To track changes in the items in a folder, you make one or more **delta** function calls to get the set of incremental changes since the last delta query.

For an example that shows a round of delta query calls, see [Get incremental changes to items in a folder](https://learn.microsoft.com/en-us/graph/delta-query-messages).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0643f21@a7809c93/folders/AAMkAGUwNjQ4ZyTAAA=/items/delta
Prefer: odata.maxpagesize=2
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Admin.Exchange.Mailboxes["{mailbox-id}"].Folders["{mailboxFolder-id}"].Items.Delta.GetAsDeltaGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Prefer", "odata.maxpagesize=2");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphadmin "github.com/microsoftgraph/msgraph-sdk-go/admin"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "odata.maxpagesize=2")

configuration := &graphadmin.ExchangeMailboxesItemFoldersItemItemsDeltaRequestBuilderGetRequestConfiguration{
	Headers: headers,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
delta, err := graphClient.Admin().Exchange().Mailboxes().ByMailboxId("mailbox-id").Folders().ByMailboxFolderId("mailboxFolder-id").Items().Delta().GetAsDeltaGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.admin().exchange().mailboxes().byMailboxId("{mailbox-id}").folders().byMailboxFolderId("{mailboxFolder-id}").items().delta().get(requestConfiguration -> {
	requestConfiguration.headers.add("Prefer", "odata.maxpagesize=2");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let delta = await client.api('/admin/exchange/mailboxes/MBX:e0643f21@a7809c93/folders/AAMkAGUwNjQ4ZyTAAA=/items/delta')
	.header('Prefer','odata.maxpagesize=2')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Admin\Exchange\Mailboxes\Item\Folders\Item\Items\Delta\DeltaRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new DeltaRequestBuilderGetRequestConfiguration();
$headers = [
		'Prefer' => 'odata.maxpagesize=2',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->admin()->exchange()->mailboxes()->byMailboxId('mailbox-id')->folders()->byMailboxFolderId('mailboxFolder-id')->items()->delta()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.admin.exchange.mailboxes.item.folders.item.items.delta.delta_request_builder import DeltaRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

request_configuration = RequestConfiguration()
request_configuration.headers.add("Prefer", "odata.maxpagesize=2")


result = await graph_client.admin.exchange.mailboxes.by_mailbox_id('mailbox-id').folders.by_mailbox_folder_id('mailboxFolder-id').items.delta.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

If the request is successful, the response includes a state token that is either a `$skipToken` \(in an **@odata.nextLink** response header\) or a `$deltaToken` \(in an **@odata.deltaLink** response header\). Respectively, they indicate whether you should continue with the round or you completed getting all the changes for that round.

The following example shows a `$skipToken` in an **@odata.nextLink** response header.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-length: 337

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(mailboxItem)",
    "@odata.nextLink": "https://graph.microsoft.com/v1.0/admin/exchange/mailboxes/MBX:e0643f21@a7809c93/folders/AAMkAGUwNjQ4ZyTAAA=/items/delta?$skiptoken={_skipToken_}",
    "value": [
        {
            "@odata.type": "#microsoft.graph.mailboxItem",
            "@odata.etag": "W/\"CQAAABYAAACQ2fKdhq8oSKEDSVrdi3lRAAFR+6ZT\"",
            "createdDateTime": "2021-10-19T06:30:30Z",
            "lastModifiedDateTime": "2021-10-19T07:17:06Z",
            "changeKey": "CQAAABYAAACQ2fKdhq8oSKEDSVrdi3lRAAFR+6ZT",
            "categories": [],
            "type": "IPM.Note",
            "size": 75329,
            "id": "AAMkAGUwNjQ4ZyTAACQ2fKdhq8oSKEDSVrdi3lRAAFSX03WAAA="
        }
    ]
}
```

## Related content

- [Use delta query to track changes in Microsoft Graph data](https://learn.microsoft.com/en-us/graph/delta-query-overview)
- [Get incremental changes to folders in a mailbox](https://learn.microsoft.com/en-us/graph/api/mailboxfolder-delta?view=graph-rest-1.0)
