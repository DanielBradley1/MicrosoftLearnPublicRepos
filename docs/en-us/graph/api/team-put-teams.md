<!-- Source: https://learn.microsoft.com/en-us/graph/api/team-put-teams?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-31 -->

# Create team from group

Namespace: microsoft.graph

Create a new [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) under a [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0). In order to create a team, the group must have at least one owner.

If the group was created less than 15 minutes ago, calls to create a team might fail with a `404 Not Found` error code because the group information didn't fully replicate.

Tip

We recommend that you retry this API call up to three times, with a 10‑second delay between attempts. If the call still fails after three retries, wait at least 15 minutes after the group was created before you try again.

Note

SharePoint provisioning doesn't occur in real time, it's a background process. The completion of the provisioning can't be determined.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group.ReadWrite.All | Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group.ReadWrite.All | Directory.ReadWrite.All |

> **Note**: This API supports admin permissions. Microsoft Teams service admins can access groups that they are not a member of.

## HTTP request

```http
PUT /groups/{id}/team
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

In the request body, supply a JSON representation of a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) object.

## Response

If successful, this method should return a `201 Created` response code and a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) object in the response body.

## Example

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
PUT https://graph.microsoft.com/v1.0/groups/{id}/team
Content-type: application/json

{
  "memberSettings": {
    "allowCreatePrivateChannels": true,
    "allowCreateUpdateChannels": true
  },
  "messagingSettings": {
    "allowUserEditMessages": true,
    "allowUserDeleteMessages": true
  },
  "funSettings": {
    "allowGiphy": true,
    "giphyContentRating": "strict"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Team
{
	MemberSettings = new TeamMemberSettings
	{
		AllowCreatePrivateChannels = true,
		AllowCreateUpdateChannels = true,
	},
	MessagingSettings = new TeamMessagingSettings
	{
		AllowUserEditMessages = true,
		AllowUserDeleteMessages = true,
	},
	FunSettings = new TeamFunSettings
	{
		AllowGiphy = true,
		GiphyContentRating = GiphyRatingType.Strict,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Groups["{group-id}"].Team.PutAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewTeam()
memberSettings := graphmodels.NewTeamMemberSettings()
allowCreatePrivateChannels := true
memberSettings.SetAllowCreatePrivateChannels(&allowCreatePrivateChannels) 
allowCreateUpdateChannels := true
memberSettings.SetAllowCreateUpdateChannels(&allowCreateUpdateChannels) 
requestBody.SetMemberSettings(memberSettings)
messagingSettings := graphmodels.NewTeamMessagingSettings()
allowUserEditMessages := true
messagingSettings.SetAllowUserEditMessages(&allowUserEditMessages) 
allowUserDeleteMessages := true
messagingSettings.SetAllowUserDeleteMessages(&allowUserDeleteMessages) 
requestBody.SetMessagingSettings(messagingSettings)
funSettings := graphmodels.NewTeamFunSettings()
allowGiphy := true
funSettings.SetAllowGiphy(&allowGiphy) 
giphyContentRating := graphmodels.STRICT_GIPHYRATINGTYPE 
funSettings.SetGiphyContentRating(&giphyContentRating) 
requestBody.SetFunSettings(funSettings)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
team, err := graphClient.Groups().ByGroupId("group-id").Team().Put(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Team team = new Team();
TeamMemberSettings memberSettings = new TeamMemberSettings();
memberSettings.setAllowCreatePrivateChannels(true);
memberSettings.setAllowCreateUpdateChannels(true);
team.setMemberSettings(memberSettings);
TeamMessagingSettings messagingSettings = new TeamMessagingSettings();
messagingSettings.setAllowUserEditMessages(true);
messagingSettings.setAllowUserDeleteMessages(true);
team.setMessagingSettings(messagingSettings);
TeamFunSettings funSettings = new TeamFunSettings();
funSettings.setAllowGiphy(true);
funSettings.setGiphyContentRating(GiphyRatingType.Strict);
team.setFunSettings(funSettings);
Team result = graphClient.groups().byGroupId("{group-id}").team().put(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const team = {
  memberSettings: {
    allowCreatePrivateChannels: true,
    allowCreateUpdateChannels: true
  },
  messagingSettings: {
    allowUserEditMessages: true,
    allowUserDeleteMessages: true
  },
  funSettings: {
    allowGiphy: true,
    giphyContentRating: 'strict'
  }
};

await client.api('/groups/{id}/team')
	.put(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Team;
use Microsoft\Graph\Generated\Models\TeamMemberSettings;
use Microsoft\Graph\Generated\Models\TeamMessagingSettings;
use Microsoft\Graph\Generated\Models\TeamFunSettings;
use Microsoft\Graph\Generated\Models\GiphyRatingType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Team();
$memberSettings = new TeamMemberSettings();
$memberSettings->setAllowCreatePrivateChannels(true);
$memberSettings->setAllowCreateUpdateChannels(true);
$requestBody->setMemberSettings($memberSettings);
$messagingSettings = new TeamMessagingSettings();
$messagingSettings->setAllowUserEditMessages(true);
$messagingSettings->setAllowUserDeleteMessages(true);
$requestBody->setMessagingSettings($messagingSettings);
$funSettings = new TeamFunSettings();
$funSettings->setAllowGiphy(true);
$funSettings->setGiphyContentRating(new GiphyRatingType('strict'));
$requestBody->setFunSettings($funSettings);

$result = $graphServiceClient->groups()->byGroupId('group-id')->team()->put($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	memberSettings = @{
		allowCreatePrivateChannels = $true
		allowCreateUpdateChannels = $true
	}
	messagingSettings = @{
		allowUserEditMessages = $true
		allowUserDeleteMessages = $true
	}
	funSettings = @{
		allowGiphy = $true
		giphyContentRating = "strict"
	}
}

Set-MgGroupTeam -GroupId $groupId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.team import Team
from msgraph.generated.models.team_member_settings import TeamMemberSettings
from msgraph.generated.models.team_messaging_settings import TeamMessagingSettings
from msgraph.generated.models.team_fun_settings import TeamFunSettings
from msgraph.generated.models.giphy_rating_type import GiphyRatingType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Team(
	member_settings = TeamMemberSettings(
		allow_create_private_channels = True,
		allow_create_update_channels = True,
	),
	messaging_settings = TeamMessagingSettings(
		allow_user_edit_messages = True,
		allow_user_delete_messages = True,
	),
	fun_settings = TeamFunSettings(
		allow_giphy = True,
		giphy_content_rating = GiphyRatingType.Strict,
	),
)

result = await graph_client.groups.by_group_id('group-id').team.put(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "memberSettings": {
    "allowCreateUpdateChannels": true,
    "allowDeleteChannels": true,
    "allowAddRemoveApps": true,
    "allowCreateUpdateRemoveTabs": true,
    "allowCreateUpdateRemoveConnectors": true
  },
  "guestSettings": {
    "allowCreateUpdateChannels": true,
    "allowDeleteChannels": true
  },
  "messagingSettings": {
    "allowUserEditMessages": true,
    "allowUserDeleteMessages": true,
    "allowOwnerDeleteMessages": true,
    "allowTeamMentions": true,
    "allowChannelMentions": true
  },
  "funSettings": {
    "allowGiphy": true,
    "giphyContentRating": "strict",
    "allowStickersAndMemes": true,
    "allowCustomMemes": true
  }
}
```

## Related content

- [Creating a group with a team](https://learn.microsoft.com/en-us/graph/teams-create-group-and-team)
- [Microsoft Graph service-specific throttling limits](https://learn.microsoft.com/en-us/graph/throttling-limits#microsoft-teams-service-limits)
