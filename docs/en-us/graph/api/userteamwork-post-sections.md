<!-- Source: https://learn.microsoft.com/en-us/graph/api/userteamwork-post-sections?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# Create teamworkSection

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) in a user's [teamwork](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-beta).

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
POST /users/{user-id}/teamwork/sections
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| If-Match | The value of the **@microsoft.graph.sectionsVersion** annotation returned when you [list sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta), or the **@odata.etag** value from any previously retrieved [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta). Required for optimistic concurrency control. |

## Request body

In the request body, supply a JSON representation of a [teamworkSection](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) object.

The following table lists the properties that you can set when you create a **teamworkSection**.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayIcon | [sectionDisplayIcon](https://learn.microsoft.com/en-us/graph/api/resources/sectiondisplayicon?view=graph-rest-beta) | The icon displayed for the section. Optional. The **skinTone** property of the icon can't be set and is derived from user settings. |
| displayName | String | The display name of the section. Required. Maximum length is 50 characters. Display names are case-sensitive and must be unique within a user's sections. The following names are reserved for system-defined sections and can't be used: `RecentChats`, `QuickViews`, `TeamsAndChannels`, `MutedChats`, `MeetingChats`, `EngageCommunities`. |
| isExpanded | Boolean | Indicates whether the section is expanded in the user interface. Optional. The default value is `true`. |
| sortType | sectionSortType | The sort order of items in the section. Optional. The default value is `userDefinedCustomOrder`. The valid values for user-defined sections are: `mostRecent`, `unreadThenMostRecent`, `userDefinedCustomOrder`, `unknownFutureValue`. The `nameAlphabetical` member isn't valid for user-defined sections. |

## Response

If successful, this method returns a `201 Created` response code and a [teamworkSection](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) object in the response body.

Note

The response includes an updated **@odata.etag** value. Use this value as the `If-Match` header for any subsequent mutation operations.

The following errors are possible.

| Response code | Message |
| :--- | :--- |
| `400 Bad Request` | The 'displayName' property is required and must not be empty. |
| `400 Bad Request` | The 'displayName' property must not exceed 50 characters. |
| `400 Bad Request` | The section display name contains invalid characters or format. |
| `400 Bad Request` | The 'id', 'createdDateTime', 'lastModifiedDateTime', 'sectionType', or 'isHierarchicalViewEnabled' property is read-only and must not be provided when creating a section. |
| `400 Bad Request` | The 'displayIcon.contentUrl' property is not supported, or the 'displayIcon.displayName' or 'displayIcon.skinTone' property is read-only and must not be provided. |
| `400 Bad Request` | The maximum number of sections has been reached. |
| `409 Conflict` | A section with this display name already exists. Returned when the requested **displayName** matches an existing user-defined section or one of the reserved system-defined section names \(`RecentChats`, `QuickViews`, `TeamsAndChannels`, `MutedChats`, `MeetingChats`, `EngageCommunities`\). The comparison is case-sensitive. |
| `412 Precondition Failed` | The `If-Match` header value doesn't match the current section hierarchy version. [List sections](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-sections?view=graph-rest-beta) again to retrieve the current **@microsoft.graph.sectionsVersion** annotation and retry. |
| `428 Precondition Required` | The `If-Match` header is required for this operation. |

## Examples

### Request

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
POST https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections
Content-type: application/json
If-Match: "1742515200"

{
  "displayName": "Project Alpha",
  "displayIcon": {
    "iconType": "🚀"
  },
  "sortType": "mostRecent"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new TeamworkSection
{
	DisplayName = "Project Alpha",
	DisplayIcon = new SectionDisplayIcon
	{
		IconType = "🚀",
	},
	SortType = SectionSortType.MostRecent,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.Sections.PostAsync(requestBody, (requestConfiguration) =>
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

configuration := &graphusers.ItemTeamworkSectionsRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewTeamworkSection()
displayName := "Project Alpha"
requestBody.SetDisplayName(&displayName) 
displayIcon := graphmodels.NewSectionDisplayIcon()
iconType := "🚀"
displayIcon.SetIconType(&iconType) 
requestBody.SetDisplayIcon(displayIcon)
sortType := graphmodels.MOSTRECENT_SECTIONSORTTYPE 
requestBody.SetSortType(&sortType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
sections, err := graphClient.Users().ByUserId("user-id").Teamwork().Sections().Post(context.Background(), requestBody, configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

TeamworkSection teamworkSection = new TeamworkSection();
teamworkSection.setDisplayName("Project Alpha");
SectionDisplayIcon displayIcon = new SectionDisplayIcon();
displayIcon.setIconType("🚀");
teamworkSection.setDisplayIcon(displayIcon);
teamworkSection.setSortType(SectionSortType.MostRecent);
TeamworkSection result = graphClient.users().byUserId("{user-id}").teamwork().sections().post(teamworkSection, requestConfiguration -> {
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
  displayName: 'Project Alpha',
  displayIcon: {
    iconType: '🚀'
  },
  sortType: 'mostRecent'
};

await client.api('/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections')
	.version('beta')
	.post(teamworkSection);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Teamwork\Sections\SectionsRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Beta\Generated\Models\TeamworkSection;
use Microsoft\Graph\Beta\Generated\Models\SectionDisplayIcon;
use Microsoft\Graph\Beta\Generated\Models\SectionSortType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TeamworkSection();
$requestBody->setDisplayName('Project Alpha');
$displayIcon = new SectionDisplayIcon();
$displayIcon->setIconType('🚀');
$requestBody->setDisplayIcon($displayIcon);
$requestBody->setSortType(new SectionSortType('mostRecent'));
$requestConfiguration = new SectionsRequestBuilderPostRequestConfiguration();
$headers = [
		'If-Match' => '"1742515200"',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->sections()->post($requestBody, $requestConfiguration)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	displayName = "Project Alpha"
	displayIcon = @{
		iconType = "🚀"
	}
	sortType = "mostRecent"
}

New-MgBetaUserTeamworkSection -UserId $userId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.teamwork.sections.sections_request_builder import SectionsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph_beta.generated.models.teamwork_section import TeamworkSection
from msgraph_beta.generated.models.section_display_icon import SectionDisplayIcon
from msgraph_beta.generated.models.section_sort_type import SectionSortType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TeamworkSection(
	display_name = "Project Alpha",
	display_icon = SectionDisplayIcon(
		icon_type = "🚀",
	),
	sort_type = SectionSortType.MostRecent,
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("If-Match", "\"1742515200\"")


result = await graph_client.users.by_user_id('user-id').teamwork.sections.post(request_body, request_configuration = request_configuration)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json
Location: https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/c3d4e5f6-a7b8-9012-cdef-123456789012

{
  "@odata.type": "#microsoft.graph.teamworkSection",
  "@odata.etag": "\"1742515210\"",
  "id": "c3d4e5f6-a7b8-9012-cdef-123456789012",
  "displayName": "Project Alpha",
  "displayIcon": {
    "iconType": "🚀",
    "displayName": "Rocket",
    "contentUrl": null,
    "skinTone": null
  },
  "sectionType": "userDefined",
  "sortType": "mostRecent",
  "isExpanded": true,
  "isHierarchicalViewEnabled": false,
  "createdDateTime": "2026-03-08T10:00:00Z",
  "lastModifiedDateTime": "2026-03-08T10:00:00Z"
}
```
