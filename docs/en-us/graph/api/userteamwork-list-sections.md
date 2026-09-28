<!-- Source: https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# List sections

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the list of [sections](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) in a user's [teamwork](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamworkSection.Read | TeamworkSection.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamworkSection.Read.All | TeamworkSection.ReadWrite.All |

## HTTP request

```http
GET /users/{user-id}/teamwork/sections
```

## Optional query parameters

This method supports the `$expand` OData query parameter to help customize the response. Only the **items** relationship can be expanded, and only one level of expansion is supported. For more information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

When `$expand=items` is specified, the response includes the **items** collection inline on each section:

- For [user-defined sections](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta#sectiontype-values), the **items** collection contains the chats, channels, meetings, and communities organized within the section.
- For [system-defined sections](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta#system-defined-sections), the **items** collection is always returned as an empty array \(`[]`\). System-defined section contents aren't exposed through the public Graph API. To enumerate items in a user-defined section without using `$expand`, use [List items](https://learn.microsoft.com/en-us/graph/api/teamworksection-list-items?view=graph-rest-beta).

When `$expand=items` is specified, the response doesn't include the **@microsoft.graph.sectionsOrder** and **@microsoft.graph.sectionsVersion** instance annotations. To obtain both the items and these annotations, issue a separate request without `$expand`.

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [teamworkSection](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) objects in the response body.

The response includes the following OData instance annotations on the collection.

| Annotation | Type | Description |
| :--- | :--- | :--- |
| @microsoft.graph.sectionsOrder | String collection | An ordered array of section IDs that represent the user's preferred section order. |
| @microsoft.graph.sectionsVersion | String | The current section hierarchy version. Use this value as the `If-Match` header for optimistic concurrency control on mutation operations \(create, update, delete, or reorder sections, and add, remove, move, or reorder items\). |

## Examples

### Example 1: List sections

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

```msgraph
GET https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.Sections.GetAsync();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sections, err := graphClient.Users().ByUserId("user-id").Teamwork().Sections().Get(context.Background(), nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TeamworkSectionCollectionResponse result = graphClient.users().byUserId("{user-id}").teamwork().sections().get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let sections = await client.api('/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->sections()->get()->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

Get-MgBetaUserTeamworkSection -UserId $userId
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').teamwork.sections.get()
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@microsoft.graph.sectionsOrder": [
    "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
    "b2c3d4e5-f6a7-8901-bcde-f12345678901"
  ],
  "@microsoft.graph.sectionsVersion": "1742515200",
  "value": [
    {
      "@odata.type": "#microsoft.graph.teamworkSection",
      "@odata.etag": "\"1742515200\"",
      "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
      "displayName": "Favorites",
      "displayIcon": {
        "iconType": "⭐",
        "displayName": "Star",
        "contentUrl": null,
        "skinTone": null
      },
      "sectionType": "userDefined",
      "sortType": "mostRecent",
      "isExpanded": true,
      "isHierarchicalViewEnabled": false,
      "createdDateTime": "2025-01-15T10:30:00Z",
      "lastModifiedDateTime": "2025-03-01T14:22:00Z"
    },
    {
      "@odata.type": "#microsoft.graph.teamworkSection",
      "@odata.etag": "\"1742515200\"",
      "id": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
      "displayName": "Teams and Channels",
      "displayIcon": null,
      "sectionType": "systemDefined",
      "sortType": "unreadThenMostRecent",
      "isExpanded": true,
      "isHierarchicalViewEnabled": true,
      "createdDateTime": "2024-06-10T08:00:00Z",
      "lastModifiedDateTime": "2025-02-28T16:45:00Z"
    }
  ]
}
```

### Example 2: List sections with items expanded

The following example uses `$expand=items` to return each section together with its items collection in a single request. The user-defined section returns its items inline, while the system-defined section returns an empty **items** array because system-defined section contents aren't exposed through the public Graph API.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```msgraph
GET https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections?$expand=items
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.Sections.GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "items" };
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
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-beta-sdk-go/users"
	  //other-imports
)

requestParameters := &graphusers.ItemTeamworkSectionsRequestBuilderGetQueryParameters{
	Expand: [] string {"items"},
}
configuration := &graphusers.ItemTeamworkSectionsRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sections, err := graphClient.Users().ByUserId("user-id").Teamwork().Sections().Get(context.Background(), configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TeamworkSectionCollectionResponse result = graphClient.users().byUserId("{user-id}").teamwork().sections().get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"items"};
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

let sections = await client.api('/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections')
	.version('beta')
	.expand('items')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Teamwork\Sections\SectionsRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new SectionsRequestBuilderGetRequestConfiguration();
$queryParameters = SectionsRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["items"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->sections()->get($requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

Get-MgBetaUserTeamworkSection -UserId $userId -ExpandProperty "items" 
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.teamwork.sections.sections_request_builder import SectionsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = SectionsRequestBuilder.SectionsRequestBuilderGetQueryParameters(
		expand = ["items"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.by_user_id('user-id').teamwork.sections.get(request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.teamworkSection",
      "@odata.etag": "\"1742515200\"",
      "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
      "displayName": "Favorites",
      "sectionType": "userDefined",
      "sortType": "mostRecent",
      "isExpanded": true,
      "isHierarchicalViewEnabled": false,
      "createdDateTime": "2025-01-15T10:30:00Z",
      "lastModifiedDateTime": "2025-03-01T14:22:00Z",
      "items": [
        {
          "@odata.type": "#microsoft.graph.teamworkSectionItem",
          "id": "19:d5b2c3a4-e6f7-8901-abcd-ef3456789012@thread.v2",
          "itemType": "chat",
          "createdDateTime": "2025-02-10T09:15:00Z",
          "lastModifiedDateTime": "2025-03-05T11:30:00Z"
        },
        {
          "@odata.type": "#microsoft.graph.teamworkSectionItem",
          "id": "19:e6f7a8b9-0123-4567-89ab-cdef01234567@thread.tacv2",
          "itemType": "channel",
          "createdDateTime": "2025-01-20T14:00:00Z",
          "lastModifiedDateTime": "2025-03-01T08:45:00Z"
        }
      ]
    },
    {
      "@odata.type": "#microsoft.graph.teamworkSection",
      "@odata.etag": "\"1742515200\"",
      "id": "b2c3d4e5-f6a7-8901-bcde-f12345678901",
      "displayName": "Teams and Channels",
      "sectionType": "systemDefined",
      "sortType": "nameAlphabetical",
      "isExpanded": true,
      "isHierarchicalViewEnabled": true,
      "createdDateTime": "2024-06-10T08:00:00Z",
      "lastModifiedDateTime": "2025-02-28T16:45:00Z",
      "items": []
    }
  ]
}
```
