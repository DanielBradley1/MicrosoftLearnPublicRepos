<!-- Source: https://learn.microsoft.com/en-us/graph/api/team-clone?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-19 -->

# team: clone

Namespace: microsoft.graph

Create a copy of a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). This operation also creates a copy of the corresponding [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0). You can specify which parts of the team to clone:

- **apps** - Copies Microsoft Teams apps that are installed in the team.
- **channels** – Copies the channel structure \(but not the messages in the channel\).
- **members** – Copies the members and owners of the group.
- **settings** – Copies all settings within the team, along with key group settings.
- **tabs** – Copies the tabs within channels.

Note

This method isn't supported for organization-wide teams.

Note

A known issue related to owners of cloned teams is associated with this method. For details, see [Known issues](https://developer.microsoft.com/graph/known-issues).

When tabs are cloned, they aren't configured. The tabs are displayed on the tab bar in Microsoft Teams, and the first time a user opens them, they must go through the configuration screen. If the user who opens the tab doesn't have permission to configure apps, they see a message that says that the tab isn't configured.

Cloning is a long-running operation. After the POST clone returns, you need to GET the [operation](https://learn.microsoft.com/en-us/graph/api/resources/teamsasyncoperation?view=graph-rest-1.0) returned by the `Location:` header to see if it's `running`, `succeeded`, or `failed`. You should continue to GET until the status isn't `running`. The recommended delay between GETs is 5 seconds.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Team.Create | Directory.ReadWrite.All, Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Team.Create | Directory.ReadWrite.All, Group.ReadWrite.All |

Note

The Group.ReadWrite.All and Directory.ReadWrite.All are supported only for backward compatibility. We recommend that you update your solutions to use an alternative permission listed in the previous table and avoid using these permissions going forward.

## HTTP request

```http
POST /teams/{id}/clone
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

| Property | Type | Description |
| :--- | :--- | :--- |
| classification | String \(optional\) | Describes a classification for the group \(such as low, medium, or high business impact\). If classification isn't specified, the classification is copied from the original team/group. |
| description | String \(optional\) | An optional description for the group. If this property isn't specified, it's left blank. |
| displayName | String | The display name for the group. This property is required when a group is created and it can't be cleared during updates. Supports $filter and $orderby. |
| mailNickname | String | The mail alias for the group, unique in the organization. This property must be specified when a group is created. Supports `filter`. If this property isn't specified, it's computed from the displayName. This property is currently ignored. |
| partsToClone | [clonableTeamParts](https://learn.microsoft.com/en-us/graph/api/resources/clonableteamparts?view=graph-rest-1.0) | A comma-separated list of the parts to clone. Legal parts are "apps, tabs, settings, channels, members". |
| visibility | [teamVisibilityType](https://learn.microsoft.com/en-us/graph/api/resources/teamvisibilitytype?view=graph-rest-1.0) \(optional\) | Specifies the visibility of the group. The possible values are: **Private**, **Public**. If visibility isn't specified, the visibility is copied from the original team/group. If the team being cloned is an **educationClass** team, the visibility parameter is ignored, and the new group's visibility will be set to HiddenMembership. |

Note

If the **description** property isn't specified in the request body, it takes the value of the **displayName** property from the request payload.

## Response

If successful, this method returns a `202 Accepted` response code with a Location: header pointing to the [operation](https://learn.microsoft.com/en-us/graph/api/resources/teamsasyncoperation?view=graph-rest-1.0) resource. When the operation is complete, the operation resource tells you the ID of the created team.

## Example

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
POST https://graph.microsoft.com/v1.0/teams/{id}/clone
Content-Type: application/json

{  
     "displayName": "Library Assist",
     "description": "Self help community for library",
     "mailNickname": "libassist",
     "partsToClone": "apps,tabs,settings,channels,members",
     "visibility": "public"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.Clone;
using Microsoft.Graph.Models;

var requestBody = new ClonePostRequestBody
{
	DisplayName = "Library Assist",
	Description = "Self help community for library",
	MailNickname = "libassist",
	PartsToClone = ClonableTeamParts.Apps | ClonableTeamParts.Tabs | ClonableTeamParts.Settings | ClonableTeamParts.Channels | ClonableTeamParts.Members,
	Visibility = TeamVisibilityType.Public,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teams["{team-id}"].Clone.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphteams "github.com/microsoftgraph/msgraph-sdk-go/teams"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphteams.NewClonePostRequestBody()
displayName := "Library Assist"
requestBody.SetDisplayName(&displayName) 
description := "Self help community for library"
requestBody.SetDescription(&description) 
mailNickname := "libassist"
requestBody.SetMailNickname(&mailNickname) 
partsToClone := graphmodels.APPS,TABS,SETTINGS,CHANNELS,MEMBERS_CLONABLETEAMPARTS 
requestBody.SetPartsToClone(&partsToClone) 
visibility := graphmodels.PUBLIC_TEAMVISIBILITYTYPE 
requestBody.SetVisibility(&visibility) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Teams().ByTeamId("team-id").Clone().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.clone.ClonePostRequestBody clonePostRequestBody = new com.microsoft.graph.teams.item.clone.ClonePostRequestBody();
clonePostRequestBody.setDisplayName("Library Assist");
clonePostRequestBody.setDescription("Self help community for library");
clonePostRequestBody.setMailNickname("libassist");
clonePostRequestBody.setPartsToClone(EnumSet.of(ClonableTeamParts.Apps, ClonableTeamParts.Tabs, ClonableTeamParts.Settings, ClonableTeamParts.Channels, ClonableTeamParts.Members));
clonePostRequestBody.setVisibility(TeamVisibilityType.Public);
graphClient.teams().byTeamId("{team-id}").clone().post(clonePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const clone = {
     displayName: 'Library Assist',
     description: 'Self help community for library',
     mailNickname: 'libassist',
     partsToClone: 'apps,tabs,settings,channels,members',
     visibility: 'public'
};

await client.api('/teams/{id}/clone')
	.post(clone);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\Clone\ClonePostRequestBody;
use Microsoft\Graph\Generated\Models\ClonableTeamParts;
use Microsoft\Graph\Generated\Models\TeamVisibilityType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ClonePostRequestBody();
$requestBody->setDisplayName('Library Assist');
$requestBody->setDescription('Self help community for library');
$requestBody->setMailNickname('libassist');
$requestBody->setPartsToClone(new ClonableTeamParts('apps,tabs,settings,channels,members'));
$requestBody->setVisibility(new TeamVisibilityType('public'));

$graphServiceClient->teams()->byTeamId('team-id')->escapedClone()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	displayName = "Library Assist"
	description = "Self help community for library"
	mailNickname = "libassist"
	partsToClone = "apps,tabs,settings,channels,members"
	visibility = "public"
}

Copy-MgTeam -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.clone.clone_post_request_body import ClonePostRequestBody
from msgraph.generated.models.clonable_team_parts import ClonableTeamParts
from msgraph.generated.models.team_visibility_type import TeamVisibilityType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ClonePostRequestBody(
	display_name = "Library Assist",
	description = "Self help community for library",
	mail_nickname = "libassist",
	parts_to_clone = ClonableTeamParts.Apps | ClonableTeamParts.Tabs | ClonableTeamParts.Settings | ClonableTeamParts.Channels | ClonableTeamParts.Members,
	visibility = TeamVisibilityType.Public,
)

await graph_client.teams.by_team_id('team-id').clone.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Location: /teams({id})/operations({opId})
Content-Type: text/plain
Content-Length: 0
```

## Related content

[Microsoft Graph service-specific throttling limits](https://learn.microsoft.com/en-us/graph/throttling-limits#microsoft-teams-service-limits)
