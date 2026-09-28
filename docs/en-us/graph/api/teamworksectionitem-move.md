<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworksectionitem-move?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# teamworkSectionItem: move

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Move an [item](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) from one user-defined [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) to another user-defined section in a user's [teamwork](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-beta). Each item can belong to only one section at a time. This action removes the item from its current section and adds it to the target section. Use this action instead of [add](https://learn.microsoft.com/en-us/graph/api/teamworksection-post-items?view=graph-rest-beta) when the item is already in a user-defined section.

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
POST /users/{user-id}/teamwork/sections/{teamworkSection-id}/items/{teamworkSectionItem-id}/move
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | The value of the **@microsoft.graph.sectionsVersion** annotation returned when you [list sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta), or the **@odata.etag** value from any previously retrieved [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta). Required for optimistic concurrency control. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| targetSectionId | String | The ID of the section to move the item to. Required. |

## Response

If successful, this action returns a `200 OK` response code and a [teamworkSectionItem](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) in the response body that represents the item in the target section.

Note

The response includes an updated **@odata.etag** value. Use this value as the `If-Match` header for any subsequent mutation operations.

The following errors are possible.

| Response code | Message |
| :--- | :--- |
| `400 Bad Request` | The 'targetSectionId' property is required and must not be empty. |
| `400 Bad Request` | The source and target sections must be different. |
| `403 Forbidden` | This section is system-generated and cannot be modified. Items can't be moved into or out of system-defined sections by using this action. |
| `404 Not Found` | The specified section was not found, or the specified item was not found in this section. |
| `412 Precondition Failed` | The `If-Match` header value doesn't match the current section hierarchy version. [List sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta) again to retrieve the current **@microsoft.graph.sectionsVersion** annotation and retry. |
| `428 Precondition Required` | The `If-Match` header is required for this operation. |

## Examples

### Request

The following example shows a request to move a chat from the "Favorites" section to the "Project Alpha" section.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890/items/19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2/move
Content-type: application/json
If-Match: "1742515200"

{
  "targetSectionId": "c3d4e5f6-a7b8-9012-cdef-123456789012"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Users.Item.Teamwork.Sections.Item.Items.Item.Move;

var requestBody = new MovePostRequestBody
{
	TargetSectionId = "c3d4e5f6-a7b8-9012-cdef-123456789012",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.Sections["{teamworkSection-id}"].Items["{teamworkSectionItem-id}"].Move.PostAsync(requestBody, (requestConfiguration) =>
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

configuration := &graphusers.ItemTeamworkSectionsItemItemsItemMoveRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphusers.NewMovePostRequestBody()
targetSectionId := "c3d4e5f6-a7b8-9012-cdef-123456789012"
requestBody.SetTargetSectionId(&targetSectionId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
move, err := graphClient.Users().ByUserId("user-id").Teamwork().Sections().ByTeamworkSectionId("teamworkSection-id").Items().ByTeamworkSectionItemId("teamworkSectionItem-id").Move().Post(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.users.item.teamwork.sections.item.items.item.move.MovePostRequestBody movePostRequestBody = new com.microsoft.graph.beta.users.item.teamwork.sections.item.items.item.move.MovePostRequestBody();
movePostRequestBody.setTargetSectionId("c3d4e5f6-a7b8-9012-cdef-123456789012");
var result = graphClient.users().byUserId("{user-id}").teamwork().sections().byTeamworkSectionId("{teamworkSection-id}").items().byTeamworkSectionItemId("{teamworkSectionItem-id}").move().post(movePostRequestBody, requestConfiguration -> {
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
  targetSectionId: 'c3d4e5f6-a7b8-9012-cdef-123456789012'
};

await client.api('/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890/items/19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2/move')
	.version('beta')
	.post(teamworkSectionItem);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Teamwork\Sections\Item\Items\Item\Move\MoveRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Users\Item\Teamwork\Sections\Item\Items\Item\Move\MovePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MovePostRequestBody();
$requestBody->setTargetSectionId('c3d4e5f6-a7b8-9012-cdef-123456789012');
$requestConfiguration = new MoveRequestBuilderPostRequestConfiguration();
$headers = [
		'If-Match' => '"1742515200"',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->sections()->byTeamworkSectionId('teamworkSection-id')->items()->byTeamworkSectionItemId('teamworkSectionItem-id')->move()->post($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	targetSectionId = "c3d4e5f6-a7b8-9012-cdef-123456789012"
}

Move-MgBetaUserTeamworkSectionItem -UserId $userId -TeamworkSectionId $teamworkSectionId -TeamworkSectionItemId $teamworkSectionItemId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.teamwork.sections.item.items.item.move.move_request_builder import MoveRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.users.item.teamwork.sections.item.items.item.move.move_post_request_body import MovePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MovePostRequestBody(
	target_section_id = "c3d4e5f6-a7b8-9012-cdef-123456789012",
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("If-Match", "\"1742515200\"")


result = await graph_client.users.by_user_id('user-id').teamwork.sections.by_teamwork_section_id('teamworkSection-id').items.by_teamwork_section_item_id('teamworkSectionItem-id').move.post(request_body, request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.type": "#microsoft.graph.teamworkSectionItem",
  "@odata.etag": "\"1742515210\"",
  "id": "19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2",
  "itemType": "chat",
  "createdDateTime": "2026-03-08T10:30:00Z",
  "lastModifiedDateTime": null
}
```
