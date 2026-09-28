<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworksection-post-items?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Add teamworkSectionItem

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Add an [item](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta), such as a chat, channel, meeting, or community, to a user-defined [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) in a user's [teamwork](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-beta). Each item can belong to only one section at a time. You can only add items that are currently in a system-defined section. If the item is already in another user-defined section, use the [move](https://learn.microsoft.com/en-us/graph/api/teamworksectionitem-move?view=graph-rest-beta) action to relocate it.

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
POST /users/{user-id}/teamwork/sections/{teamworkSection-id}/items
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | The value of the **@microsoft.graph.sectionsVersion** annotation returned when you [list sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta), or the **@odata.etag** value from any previously retrieved [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta). Required for optimistic concurrency control. |

## Request body

In the request body, supply a JSON representation of a [teamworkSectionItem](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) object.

The following table lists the properties that you can set when you add a **teamworkSectionItem**.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The conversation ID of the chat, channel, meeting, or community to add to the section. For a community \(Viva Engage\) item, you can provide either the bare community ID returned when you [list communities](https://learn.microsoft.com/en-us/graph/api/employeeexperience-list-communities?view=graph-rest-beta) \(for example, `eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzMzYyMTIyMTAifQ`\) or the full `19:{communityId}@EngageCommunity` thread ID. When you provide a bare community ID, the service automatically normalizes it to the `19:{communityId}@EngageCommunity` format; an ID that already includes the thread prefix is used as-is. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [teamworkSectionItem](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) object in the response body.

Note

The response includes an updated **@odata.etag** value. Use this value as the `If-Match` header for any subsequent mutation operations.

The following errors are possible.

| Response code | Message |
| :--- | :--- |
| `400 Bad Request` | The 'id' property is required and must not be empty. |
| `400 Bad Request` | The specified item ID is not valid. Provide a valid chat, channel, meeting, or community ID. |
| `400 Bad Request` | The maximum number of items in this section has been reached. |
| `403 Forbidden` | Access to this resource is denied. The caller must be a member of the conversation being added. |
| `404 Not Found` | The specified section was not found. |
| `409 Conflict` | This item is already in this section. |
| `409 Conflict` | This item is already associated with another section. Use the [move](https://learn.microsoft.com/en-us/graph/api/teamworksectionitem-move?view=graph-rest-beta) API to relocate it. The response includes a `conflictingSectionId` detail with the ID of the section that currently holds the item. |
| `412 Precondition Failed` | The `If-Match` header value doesn't match the current section hierarchy version. [List sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta) again to retrieve the current **@microsoft.graph.sectionsVersion** annotation and retry. |
| `428 Precondition Required` | The `If-Match` header is required for this operation. |

## Examples

### Example 1: Add a chat to a section

The following example shows how to add a chat to a section.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890/items
Content-type: application/json
If-Match: "1742515200"

{
  "id": "19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new TeamworkSectionItem
{
	Id = "19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.Sections["{teamworkSection-id}"].Items.PostAsync(requestBody, (requestConfiguration) =>
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  graphusers "github.com/microsoftgraph/msgraph-beta-sdk-go/users"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("If-Match", "\"1742515200\"")

configuration := &graphusers.ItemTeamworkSectionsItemItemsRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewTeamworkSectionItem()
id := "19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2"
requestBody.SetId(&id) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
items, err := graphClient.Users().ByUserId("user-id").Teamwork().Sections().ByTeamworkSectionId("teamworkSection-id").Items().Post(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TeamworkSectionItem teamworkSectionItem = new TeamworkSectionItem();
teamworkSectionItem.setId("19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2");
TeamworkSectionItem result = graphClient.users().byUserId("{user-id}").teamwork().sections().byTeamworkSectionId("{teamworkSection-id}").items().post(teamworkSectionItem, requestConfiguration -> {
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
  id: '19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2'
};

await client.api('/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890/items')
	.version('beta')
	.post(teamworkSectionItem);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Teamwork\Sections\Item\Items\ItemsRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Models\TeamworkSectionItem;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TeamworkSectionItem();
$requestBody->setId('19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2');
$requestConfiguration = new ItemsRequestBuilderPostRequestConfiguration();
$headers = [
		'If-Match' => '"1742515200"',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->sections()->byTeamworkSectionId('teamworkSection-id')->items()->post($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	id = "19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2"
}

New-MgBetaUserTeamworkSectionItem -UserId $userId -TeamworkSectionId $teamworkSectionId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.teamwork.sections.item.items.items_request_builder import ItemsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.models.teamwork_section_item import TeamworkSectionItem
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TeamworkSectionItem(
	id = "19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2",
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("If-Match", "\"1742515200\"")


result = await graph_client.users.by_user_id('user-id').teamwork.sections.by_teamwork_section_id('teamworkSection-id').items.post(request_body, request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json
Location: https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890/items/19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2

{
  "@odata.type": "#microsoft.graph.teamworkSectionItem",
  "@odata.etag": "\"1742515210\"",
  "id": "19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2",
  "itemType": "chat",
  "createdDateTime": "2026-03-08T10:00:00Z",
  "lastModifiedDateTime": null
}
```

### Example 2: Add a community to a section

The following example shows how to add a Viva Engage community to a section. The request provides the bare community ID returned when you [list communities](https://learn.microsoft.com/en-us/graph/api/employeeexperience-list-communities?view=graph-rest-beta). The service normalizes the community ID to the `19:{communityId}@EngageCommunity` format that is returned in the response.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890/items
Content-type: application/json
If-Match: "1742515210"

{
  "id": "eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzMzYyMTIyMTAifQ"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new TeamworkSectionItem
{
	Id = "eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzMzYyMTIyMTAifQ",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.Sections["{teamworkSection-id}"].Items.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("If-Match", "\"1742515210\"");
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
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  graphusers "github.com/microsoftgraph/msgraph-beta-sdk-go/users"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("If-Match", "\"1742515210\"")

configuration := &graphusers.ItemTeamworkSectionsItemItemsRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewTeamworkSectionItem()
id := "eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzMzYyMTIyMTAifQ"
requestBody.SetId(&id) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
items, err := graphClient.Users().ByUserId("user-id").Teamwork().Sections().ByTeamworkSectionId("teamworkSection-id").Items().Post(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TeamworkSectionItem teamworkSectionItem = new TeamworkSectionItem();
teamworkSectionItem.setId("eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzMzYyMTIyMTAifQ");
TeamworkSectionItem result = graphClient.users().byUserId("{user-id}").teamwork().sections().byTeamworkSectionId("{teamworkSection-id}").items().post(teamworkSectionItem, requestConfiguration -> {
	requestConfiguration.headers.add("If-Match", "\"1742515210\"");
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
  id: 'eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzMzYyMTIyMTAifQ'
};

await client.api('/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890/items')
	.version('beta')
	.post(teamworkSectionItem);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Teamwork\Sections\Item\Items\ItemsRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Models\TeamworkSectionItem;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TeamworkSectionItem();
$requestBody->setId('eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzMzYyMTIyMTAifQ');
$requestConfiguration = new ItemsRequestBuilderPostRequestConfiguration();
$headers = [
		'If-Match' => '"1742515210"',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->sections()->byTeamworkSectionId('teamworkSection-id')->items()->post($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	id = "eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzMzYyMTIyMTAifQ"
}

New-MgBetaUserTeamworkSectionItem -UserId $userId -TeamworkSectionId $teamworkSectionId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.teamwork.sections.item.items.items_request_builder import ItemsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.models.teamwork_section_item import TeamworkSectionItem
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TeamworkSectionItem(
	id = "eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzMzYyMTIyMTAifQ",
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("If-Match", "\"1742515210\"")


result = await graph_client.users.by_user_id('user-id').teamwork.sections.by_teamwork_section_id('teamworkSection-id').items.post(request_body, request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response. The **id** property is returned in the normalized `19:{communityId}@EngageCommunity` format.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json
Location: https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890/items/19:eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzMzYyMTIyMTAifQ@EngageCommunity

{
  "@odata.type": "#microsoft.graph.teamworkSectionItem",
  "@odata.etag": "\"1742515220\"",
  "id": "19:eyJfdHlwZSI6Ikdyb3VwIiwiaWQiOiIxOTAzMzYyMTIyMTAifQ@EngageCommunity",
  "itemType": "community",
  "createdDateTime": "2026-03-08T10:05:00Z",
  "lastModifiedDateTime": null
}
```
