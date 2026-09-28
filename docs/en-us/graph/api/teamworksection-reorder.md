<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworksection-reorder?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# teamworkSection: reorder

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Reorder the sections in a user's teamwork. The **sectionsOrder** collection must contain every section ID returned by [List sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta), exactly once. If the collection contains the *QuickViews* system section, that section must be first.

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
POST /me/teamwork/sections/reorder
POST /users/{user-id}/teamwork/sections/reorder
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
| sectionsOrder | String collection | The complete ordered list of section IDs. Include every section ID returned by [List sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta), exactly once. If the *QuickViews* system section is included, it must be the first ID. Required. |

## Response

If successful, this action returns a `200 OK` response code and a [teamworkSection](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) collection in the response body, in the requested order.

Note

Each returned section includes an updated **@odata.etag** value. Use this value as the `If-Match` header for any subsequent mutation operation.

The following errors are possible.

| Response code | Message |
| :--- | :--- |
| `400 Bad Request` | The **sectionsOrder** property is missing, empty, exceeds the supported maximum, or contains null, empty, or duplicate IDs. |
| `400 Bad Request` | The reorder list doesn't contain every current section exactly once, contains an unknown section ID, or doesn't place the *QuickViews* system section first. |
| `404 Not Found` | The specified user wasn't found. |
| `409 Conflict` | A section in the reorder list was deleted concurrently with the reorder request. [List sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta) again and retry with the current section IDs and version. |
| `412 Precondition Failed` | The `If-Match` header value doesn't match the current section hierarchy version. [List sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta) again to retrieve the latest **@microsoft.graph.sectionsVersion** annotation and retry. |
| `428 Precondition Required` | The `If-Match` header is required for this operation. |

## Examples

### Request

The following example reorders three sections for a user.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/reorder
Content-Type: application/json
If-Match: "1742515200"

{
  "sectionsOrder": [
    "ce274158-f4f5-4ba7-bd18-0b2204dc1691~10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f~QuickViews",
    "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    "b2c3d4e5-f6a7-8901-bcde-f12345678901"
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Users.Item.Teamwork.Sections.Reorder;

var requestBody = new ReorderPostRequestBody
{
	SectionsOrder = new List<string>
	{
		"ce274158-f4f5-4ba7-bd18-0b2204dc1691~10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f~QuickViews",
		"a1b2c3d4-e5f6-7890-abcd-ef1234567890",
		"b2c3d4e5-f6a7-8901-bcde-f12345678901",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.Sections.Reorder.PostAsReorderPostResponseAsync(requestBody, (requestConfiguration) =>
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

configuration := &graphusers.ItemTeamworkSectionsReorderRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphusers.NewReorderPostRequestBody()
sectionsOrder := []string {
	"ce274158-f4f5-4ba7-bd18-0b2204dc1691~10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f~QuickViews",
	"a1b2c3d4-e5f6-7890-abcd-ef1234567890",
	"b2c3d4e5-f6a7-8901-bcde-f12345678901",
}
requestBody.SetSectionsOrder(sectionsOrder)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
reorder, err := graphClient.Users().ByUserId("user-id").Teamwork().Sections().Reorder().PostAsReorderPostResponse(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.users.item.teamwork.sections.reorder.ReorderPostRequestBody reorderPostRequestBody = new com.microsoft.graph.beta.users.item.teamwork.sections.reorder.ReorderPostRequestBody();
LinkedList<String> sectionsOrder = new LinkedList<String>();
sectionsOrder.add("ce274158-f4f5-4ba7-bd18-0b2204dc1691~10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f~QuickViews");
sectionsOrder.add("a1b2c3d4-e5f6-7890-abcd-ef1234567890");
sectionsOrder.add("b2c3d4e5-f6a7-8901-bcde-f12345678901");
reorderPostRequestBody.setSectionsOrder(sectionsOrder);
var result = graphClient.users().byUserId("{user-id}").teamwork().sections().reorder().post(reorderPostRequestBody, requestConfiguration -> {
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

const teamworkSection = {
  sectionsOrder: [
    'ce274158-f4f5-4ba7-bd18-0b2204dc1691~10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f~QuickViews',
    'a1b2c3d4-e5f6-7890-abcd-ef1234567890',
    'b2c3d4e5-f6a7-8901-bcde-f12345678901'
  ]
};

await client.api('/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/reorder')
	.version('beta')
	.post(teamworkSection);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Teamwork\Sections\Reorder\ReorderRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Users\Item\Teamwork\Sections\Reorder\ReorderPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReorderPostRequestBody();
$requestBody->setSectionsOrder(['ce274158-f4f5-4ba7-bd18-0b2204dc1691~10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f~QuickViews', 'a1b2c3d4-e5f6-7890-abcd-ef1234567890', 'b2c3d4e5-f6a7-8901-bcde-f12345678901', 	]);
$requestConfiguration = new ReorderRequestBuilderPostRequestConfiguration();
$headers = [
		'If-Match' => '"1742515200"',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->sections()->reorder()->post($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.teamwork.sections.reorder.reorder_request_builder import ReorderRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.users.item.teamwork.sections.reorder.reorder_post_request_body import ReorderPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReorderPostRequestBody(
	sections_order = [
		"ce274158-f4f5-4ba7-bd18-0b2204dc1691~10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f~QuickViews",
		"a1b2c3d4-e5f6-7890-abcd-ef1234567890",
		"b2c3d4e5-f6a7-8901-bcde-f12345678901",
	],
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("If-Match", "\"1742515200\"")


result = await graph_client.users.by_user_id('user-id').teamwork.sections.reorder.post(request_body, request_configuration = request_configuration)
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
      "@odata.type": "#microsoft.graph.teamworkSection",
      "@odata.etag": "\"1742515210\"",
      "id": "ce274158-f4f5-4ba7-bd18-0b2204dc1691~10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f~QuickViews",
      "displayName": "QuickViews",
      "sectionType": "systemDefined",
      "sortType": "nameAlphabetical"
    },
    {
      "@odata.type": "#microsoft.graph.teamworkSection",
      "@odata.etag": "\"1742515210\"",
      "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
      "displayName": "Project Alpha",
      "sectionType": "userDefined",
      "sortType": "userDefinedCustomOrder"
    },
    {
      "@odata.type": "#microsoft.graph.teamworkSection",
      "@odata.etag": "\"1742515210\"",
      "id": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
      "displayName": "Customer Escalations",
      "sectionType": "userDefined",
      "sortType": "mostRecent"
    }
  ]
}
```
