<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworksection-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-22 -->

# Update teamworkSection

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) in a user's [teamwork](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-beta). For system-defined sections, only the **sortType** property can be updated.

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
PATCH /users/{user-id}/teamwork/sections/{teamworkSection-id}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | The value of the **@microsoft.graph.sectionsVersion** annotation returned when you [list sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta), or the **@odata.etag** value from any previously retrieved [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta). Required for optimistic concurrency control. |

## Request body

In the request body, supply a JSON representation of only the properties to update. The following properties can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayIcon | [sectionDisplayIcon](https://learn.microsoft.com/en-us/graph/api/resources/sectiondisplayicon?view=graph-rest-beta) | The icon displayed for the section. |
| displayName | String | The display name of the section. Maximum length is 50 characters. Display names are case-sensitive and must be unique within a user's sections. The reserved system-defined names \(`RecentChats`, `QuickViews`, `TeamsAndChannels`, `MutedChats`, `MeetingChats`, `EngageCommunities`\) can't be used. |
| isExpanded | Boolean | Indicates whether the section is expanded in the user interface. |
| sortType | sectionSortType | The sort order of items in the section. The possible values are: `mostRecent`, `unreadThenMostRecent`, `nameAlphabetical`, `userDefinedCustomOrder`, `unknownFutureValue`. |

Important

The valid **sortType** values depend on the section type:

- *User-defined sections*: `mostRecent`, `unreadThenMostRecent`, and `userDefinedCustomOrder` are valid. `nameAlphabetical` isn't supported.
- *System-defined sections*: The valid values depend on the specific section. For example, the *Teams* and *Channels* sections support `nameAlphabetical`, but the *RecentChats* and *MutedChats* sections don't. When the property **isHierarchicalViewEnabled** is set to `true`, only `nameAlphabetical` is valid.

## Response

If successful, this method returns a `200 OK` response code and an updated [teamworkSection](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) object in the response body.

Note

The response includes an updated **@odata.etag** value. Use this value as the `If-Match` header for any subsequent mutation operations.

The following errors are possible.

| Response code | Message |
| :--- | :--- |
| `400 Bad Request` | At least one property must be provided for update. |
| `400 Bad Request` | The 'displayName' property must not be empty or whitespace, or must not exceed 50 characters. |
| `400 Bad Request` | The property '{propertyName}' is read-only or not updatable. Only **displayName**, **displayIcon**, **isExpanded**, and **sortType** can be updated. |
| `400 Bad Request` | The specified sort type is not valid for this section. For more information, see the [Request body](#request-body) section. |
| `403 Forbidden` | This section is system-generated and cannot be modified. Only the **sortType** property can be updated on system-defined sections. |
| `404 Not Found` | The specified section was not found. |
| `409 Conflict` | A section with this display name already exists. Returned when the requested **displayName** matches an existing user-defined section or a reserved system-defined section name. The comparison is case-sensitive. |
| `412 Precondition Failed` | The `If-Match` header value doesn't match the current section hierarchy version. [List sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta) again to retrieve the current **@microsoft.graph.sectionsVersion** annotation and retry. |
| `428 Precondition Required` | The `If-Match` header is required for this operation. |

## Examples

### Example 1: Update the display name of a section

The following example shows how to update the display name of a **teamworkSection** object.

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
PATCH https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890
Content-type: application/json
If-Match: "1742515200"

{
  "displayName": "Important Conversations"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new TeamworkSection
{
	DisplayName = "Important Conversations",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.Sections["{teamworkSection-id}"].PatchAsync(requestBody, (requestConfiguration) =>
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

configuration := &graphusers.ItemTeamworkSectionsItemRequestBuilderPatchRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewTeamworkSection()
displayName := "Important Conversations"
requestBody.SetDisplayName(&displayName) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sections, err := graphClient.Users().ByUserId("user-id").Teamwork().Sections().ByTeamworkSectionId("teamworkSection-id").Patch(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TeamworkSection teamworkSection = new TeamworkSection();
teamworkSection.setDisplayName("Important Conversations");
TeamworkSection result = graphClient.users().byUserId("{user-id}").teamwork().sections().byTeamworkSectionId("{teamworkSection-id}").patch(teamworkSection, requestConfiguration -> {
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
  displayName: 'Important Conversations'
};

await client.api('/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890')
	.version('beta')
	.update(teamworkSection);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Teamwork\Sections\Item\TeamworkSectionItemRequestBuilderPatchRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Models\TeamworkSection;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TeamworkSection();
$requestBody->setDisplayName('Important Conversations');
$requestConfiguration = new TeamworkSectionItemRequestBuilderPatchRequestConfiguration();
$headers = [
		'If-Match' => '"1742515200"',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->sections()->byTeamworkSectionId('teamworkSection-id')->patch($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	displayName = "Important Conversations"
}

Update-MgBetaUserTeamworkSection -UserId $userId -TeamworkSectionId $teamworkSectionId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.teamwork.sections.item.teamwork_section_item_request_builder import TeamworkSectionItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.models.teamwork_section import TeamworkSection
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TeamworkSection(
	display_name = "Important Conversations",
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("If-Match", "\"1742515200\"")


result = await graph_client.users.by_user_id('user-id').teamwork.sections.by_teamwork_section_id('teamworkSection-id').patch(request_body, request_configuration = request_configuration)
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
  "@odata.type": "#microsoft.graph.teamworkSection",
  "@odata.etag": "\"1742515210\"",
  "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
  "displayName": "Important Conversations",
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
  "lastModifiedDateTime": "2026-03-08T09:15:00Z"
}
```

### Example 2: Update the sort order of a section

The following example shows how to update the sort order of a **teamworkSection** object.

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
PATCH https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890
Content-type: application/json
If-Match: "1742515210"

{
  "sortType": "unreadThenMostRecent"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new TeamworkSection
{
	SortType = SectionSortType.UnreadThenMostRecent,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.Sections["{teamworkSection-id}"].PatchAsync(requestBody, (requestConfiguration) =>
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

configuration := &graphusers.ItemTeamworkSectionsItemRequestBuilderPatchRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewTeamworkSection()
sortType := graphmodels.UNREADTHENMOSTRECENT_SECTIONSORTTYPE 
requestBody.SetSortType(&sortType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sections, err := graphClient.Users().ByUserId("user-id").Teamwork().Sections().ByTeamworkSectionId("teamworkSection-id").Patch(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TeamworkSection teamworkSection = new TeamworkSection();
teamworkSection.setSortType(SectionSortType.UnreadThenMostRecent);
TeamworkSection result = graphClient.users().byUserId("{user-id}").teamwork().sections().byTeamworkSectionId("{teamworkSection-id}").patch(teamworkSection, requestConfiguration -> {
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

const teamworkSection = {
  sortType: 'unreadThenMostRecent'
};

await client.api('/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890')
	.version('beta')
	.update(teamworkSection);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Teamwork\Sections\Item\TeamworkSectionItemRequestBuilderPatchRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Models\TeamworkSection;
use Microsoft\Graph\Beta\Generated\Models\SectionSortType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TeamworkSection();
$requestBody->setSortType(new SectionSortType('unreadThenMostRecent'));
$requestConfiguration = new TeamworkSectionItemRequestBuilderPatchRequestConfiguration();
$headers = [
		'If-Match' => '"1742515210"',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->sections()->byTeamworkSectionId('teamworkSection-id')->patch($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	sortType = "unreadThenMostRecent"
}

Update-MgBetaUserTeamworkSection -UserId $userId -TeamworkSectionId $teamworkSectionId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.teamwork.sections.item.teamwork_section_item_request_builder import TeamworkSectionItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.models.teamwork_section import TeamworkSection
from msgraph_beta.generated.models.section_sort_type import SectionSortType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TeamworkSection(
	sort_type = SectionSortType.UnreadThenMostRecent,
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("If-Match", "\"1742515210\"")


result = await graph_client.users.by_user_id('user-id').teamwork.sections.by_teamwork_section_id('teamworkSection-id').patch(request_body, request_configuration = request_configuration)
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
  "@odata.type": "#microsoft.graph.teamworkSection",
  "@odata.etag": "\"1742515220\"",
  "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
  "displayName": "Important Conversations",
  "displayIcon": {
    "iconType": "⭐",
    "displayName": "Star",
    "contentUrl": null,
    "skinTone": null
  },
  "sectionType": "userDefined",
  "sortType": "unreadThenMostRecent",
  "isExpanded": true,
  "isHierarchicalViewEnabled": false,
  "createdDateTime": "2025-01-15T10:30:00Z",
  "lastModifiedDateTime": "2026-03-08T09:20:00Z"
}
```
