<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworksectionitem-reorder?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# teamworkSectionItem: reorder

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Reorder the items in a user-defined section in a user's teamwork. The section must have **sortType** set to `userDefinedCustomOrder`, and the **itemsOrder** collection must contain every item ID returned by [List items](https://learn.microsoft.com/en-us/graph/api/teamworksection-list-items?view=graph-rest-beta), exactly once.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamworkSection.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamworkSection.ReadWrite.All | Teamwork.Migrate.All |

## HTTP request

```http
POST /me/teamwork/sections/{teamworkSection-id}/items/reorder
POST /users/{user-id}/teamwork/sections/{teamworkSection-id}/items/reorder
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | \*\*\*\*\*\* Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | The value of the **@microsoft.graph.sectionsVersion** annotation returned when you [list sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta), or the **@odata.etag** value from any previously retrieved [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta). Required for optimistic concurrency control. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameter that is required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| itemsOrder | String collection | The complete ordered list of item IDs in the section. Include every ID returned by [List items](https://learn.microsoft.com/en-us/graph/api/teamworksection-list-items?view=graph-rest-beta), exactly once. Required. |

## Response

If successful, this action returns a `200 OK` response code and a [teamworkSectionItem](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) collection in the response body, in the requested order.

Note

Each returned item includes an updated **@odata.etag** value. Use this value as the `If-Match` header for any subsequent mutation operation.

The following errors are possible.

| Response code | Message |
| :--- | :--- |
| `400 Bad Request` | The **itemsOrder** property is missing, empty, exceeds the supported maximum, or contains null, empty, or duplicate IDs. |
| `400 Bad Request` | The reorder list doesn't contain every item in the section exactly once, or it contains an item ID that isn't in the section. |
| `403 Forbidden` | This section is system-generated and can't be modified. Reorder items only in user-defined sections. |
| `404 Not Found` | The specified section wasn't found. |
| `409 Conflict` | Reordering is only supported when the section **sortType** is `userDefinedCustomOrder`. [Update the section](https://learn.microsoft.com/en-us/graph/api/teamworksection-update?view=graph-rest-beta) to use this sort type, then retry. |
| `409 Conflict` | The target section was deleted concurrently with the reorder request. [List sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta) again and retry with a current section ID and version. |
| `412 Precondition Failed` | The `If-Match` header value doesn't match the current section hierarchy version. [List sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta) again to retrieve the latest **@microsoft.graph.sectionsVersion** annotation and retry. |
| `428 Precondition Required` | The `If-Match` header is required for this operation. |

## Examples

### Request

The following example reorders three items in the "Project Alpha" section.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890/items/reorder
Content-Type: application/json
If-Match: "1742515200"

{
  "itemsOrder": [
    "19:meeting_MTUxMjg0OGItZTY3MC00NTkyLTg1NzMtZTVkZTcyZDU5ZGVi@thread.v2",
    "19:978e3806-38a4-4104-a07f-57abfa8cdf9a_bdf9c93b-12ea-4e8f-8383-d0ca66d5ff48@unq.gbl.spaces",
    "19:94961b6eacc04e2392e34709c66cb610@thread.v2"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Users.Item.Teamwork.Sections.Item.Items.Reorder;

var requestBody = new ReorderPostRequestBody
{
	ItemsOrder = new List<string>
	{
		"19:meeting_MTUxMjg0OGItZTY3MC00NTkyLTg1NzMtZTVkZTcyZDU5ZGVi@thread.v2",
		"19:978e3806-38a4-4104-a07f-57abfa8cdf9a_bdf9c93b-12ea-4e8f-8383-d0ca66d5ff48@unq.gbl.spaces",
		"19:94961b6eacc04e2392e34709c66cb610@thread.v2",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.Sections["{teamworkSection-id}"].Items.Reorder.PostAsReorderPostResponseAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("If-Match", "\"1742515200\"");
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-beta-sdk-go/users"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("If-Match", "\"1742515200\"")

configuration := &graphusers.ItemTeamworkSectionsItemItemsReorderRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphusers.NewReorderPostRequestBody()
itemsOrder := []string {
	"19:meeting_MTUxMjg0OGItZTY3MC00NTkyLTg1NzMtZTVkZTcyZDU5ZGVi@thread.v2",
	"19:978e3806-38a4-4104-a07f-57abfa8cdf9a_bdf9c93b-12ea-4e8f-8383-d0ca66d5ff48@unq.gbl.spaces",
	"19:94961b6eacc04e2392e34709c66cb610@thread.v2",
}
requestBody.SetItemsOrder(itemsOrder)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
reorder, err := graphClient.Users().ByUserId("user-id").Teamwork().Sections().ByTeamworkSectionId("teamworkSection-id").Items().Reorder().PostAsReorderPostResponse(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.users.item.teamwork.sections.item.items.reorder.ReorderPostRequestBody reorderPostRequestBody = new com.microsoft.graph.beta.users.item.teamwork.sections.item.items.reorder.ReorderPostRequestBody();
LinkedList<String> itemsOrder = new LinkedList<String>();
itemsOrder.add("19:meeting_MTUxMjg0OGItZTY3MC00NTkyLTg1NzMtZTVkZTcyZDU5ZGVi@thread.v2");
itemsOrder.add("19:978e3806-38a4-4104-a07f-57abfa8cdf9a_bdf9c93b-12ea-4e8f-8383-d0ca66d5ff48@unq.gbl.spaces");
itemsOrder.add("19:94961b6eacc04e2392e34709c66cb610@thread.v2");
reorderPostRequestBody.setItemsOrder(itemsOrder);
var result = graphClient.users().byUserId("{user-id}").teamwork().sections().byTeamworkSectionId("{teamworkSection-id}").items().reorder().post(reorderPostRequestBody, requestConfiguration -> {
	requestConfiguration.headers.add("If-Match", "\"1742515200\"");
});
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const teamworkSectionItem = {
  itemsOrder: [
    '19:meeting_MTUxMjg0OGItZTY3MC00NTkyLTg1NzMtZTVkZTcyZDU5ZGVi@thread.v2',
    '19:978e3806-38a4-4104-a07f-57abfa8cdf9a_bdf9c93b-12ea-4e8f-8383-d0ca66d5ff48@unq.gbl.spaces',
    '19:94961b6eacc04e2392e34709c66cb610@thread.v2'
  ]
};

await client.api('/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890/items/reorder')
	.version('beta')
	.post(teamworkSectionItem);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Teamwork\Sections\Item\Items\Reorder\ReorderRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Users\Item\Teamwork\Sections\Item\Items\Reorder\ReorderPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReorderPostRequestBody();
$requestBody->setItemsOrder(['19:meeting_MTUxMjg0OGItZTY3MC00NTkyLTg1NzMtZTVkZTcyZDU5ZGVi@thread.v2', '19:978e3806-38a4-4104-a07f-57abfa8cdf9a_bdf9c93b-12ea-4e8f-8383-d0ca66d5ff48@unq.gbl.spaces', '19:94961b6eacc04e2392e34709c66cb610@thread.v2', 	]);
$requestConfiguration = new ReorderRequestBuilderPostRequestConfiguration();
$headers = [
		'If-Match' => '"1742515200"',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->sections()->byTeamworkSectionId('teamworkSection-id')->items()->reorder()->post($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.teamwork.sections.item.items.reorder.reorder_request_builder import ReorderRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.users.item.teamwork.sections.item.items.reorder.reorder_post_request_body import ReorderPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReorderPostRequestBody(
	items_order = [
		"19:meeting_MTUxMjg0OGItZTY3MC00NTkyLTg1NzMtZTVkZTcyZDU5ZGVi@thread.v2",
		"19:978e3806-38a4-4104-a07f-57abfa8cdf9a_bdf9c93b-12ea-4e8f-8383-d0ca66d5ff48@unq.gbl.spaces",
		"19:94961b6eacc04e2392e34709c66cb610@thread.v2",
	],
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("If-Match", "\"1742515200\"")


result = await graph_client.users.by_user_id('user-id').teamwork.sections.by_teamwork_section_id('teamworkSection-id').items.reorder.post(request_body, request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.teamworkSectionItem",
      "@odata.etag": "\"1742515210\"",
      "id": "19:meeting_MTUxMjg0OGItZTY3MC00NTkyLTg1NzMtZTVkZTcyZDU5ZGVi@thread.v2",
      "itemType": "meeting",
      "lastModifiedDateTime": "2026-08-06T14:40:00Z"
    },
    {
      "@odata.type": "#microsoft.graph.teamworkSectionItem",
      "@odata.etag": "\"1742515210\"",
      "id": "19:978e3806-38a4-4104-a07f-57abfa8cdf9a_bdf9c93b-12ea-4e8f-8383-d0ca66d5ff48@unq.gbl.spaces",
      "itemType": "channel",
      "lastModifiedDateTime": "2026-08-06T14:40:00Z"
    },
    {
      "@odata.type": "#microsoft.graph.teamworkSectionItem",
      "@odata.etag": "\"1742515210\"",
      "id": "19:94961b6eacc04e2392e34709c66cb610@thread.v2",
      "itemType": "chat",
      "lastModifiedDateTime": "2026-08-06T14:40:00Z"
    }
  ]
}
```
