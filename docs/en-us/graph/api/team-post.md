<!-- Source: https://learn.microsoft.com/en-us/graph/api/team-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create team

Namespace: microsoft.graph

Create a new [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0).

Note

When you create a team, the SharePoint site of the general channel might fail to provision. If the site fails to provision after 5 minutes, use the [Get filesFolder](https://learn.microsoft.com/en-us/graph/api/channel-get-filesfolder) API to trigger provisioning.

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
| Application | Team.Create | Directory.ReadWrite.All, Group.ReadWrite.All, Teamwork.Migrate.All |

Note

- The Teamwork.Migrate.All permission is only supported for [migration](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/import-messages/import-external-messages-to-teams). In the future, Microsoft may require you or your customers to pay additional fees based on the amount of data imported.
- The Group.ReadWrite.All and Directory.ReadWrite.All permissions are supported only for backward compatibility. We recommend that you update your solutions to use an alternative permission listed in the previous table and avoid using these permissions going forward.

## HTTP request

```http
POST /teams
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) object. Optionally, specify a value for the **firstChannelName** property to name the first channel that is created. The default value of the first channel is `General`.

## Response

If successful, this API returns a `202 Accepted` response that contains a link to the [teamsAsyncOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsasyncoperation?view=graph-rest-1.0).

## Examples

### Example 1: Delegated permissions

Here's an example of a minimal request. By omitting other properties, the client is implicitly taking defaults from the pre-defined template represented by `template`.

#### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/teams
Content-Type: application/json

{
  "template@odata.bind": "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
  "displayName": "My Sample Team",
  "description": "My sample team’s description",
  "firstChannelName": "My first channel of the sample team",
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Team
{
	DisplayName = "My Sample Team",
	Description = "My sample team’s description",
	FirstChannelName = "My first channel of the sample team",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"template@odata.bind" , "https://graph.microsoft.com/v1.0/teamsTemplates('standard')"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams.PostAsync(requestBody);
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
displayName := "My Sample Team"
requestBody.SetDisplayName(&displayName) 
description := "My sample team’s description"
requestBody.SetDescription(&description) 
firstChannelName := "My first channel of the sample team"
requestBody.SetFirstChannelName(&firstChannelName) 
additionalData := map[string]interface{}{
	"template@odata.bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('standard')", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
teams, err := graphClient.Teams().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Team team = new Team();
team.setDisplayName("My Sample Team");
team.setDescription("My sample team’s description");
team.setFirstChannelName("My first channel of the sample team");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("template@odata.bind", "https://graph.microsoft.com/v1.0/teamsTemplates('standard')");
team.setAdditionalData(additionalData);
Team result = graphClient.teams().post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const team = {
  'template@odata.bind': 'https://graph.microsoft.com/v1.0/teamsTemplates(\'standard\')',
  displayName: 'My Sample Team',
  description: 'My sample team’s description',
  firstChannelName: 'My first channel of the sample team',
};

await client.api('/teams')
	.post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Team;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Team();
$requestBody->setDisplayName('My Sample Team');
$requestBody->setDescription('My sample team’s description');
$requestBody->setFirstChannelName('My first channel of the sample team');
$additionalData = [
	'template@odata.bind' => 'https://graph.microsoft.com/v1.0/teamsTemplates(\'standard\')',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->teams()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	"template@odata.bind" = "https://graph.microsoft.com/v1.0/teamsTemplates('standard')"
	displayName = "My Sample Team"
	description = "My sample team’s description"
	firstChannelName = "My first channel of the sample team"
}

New-MgTeam -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.team import Team
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Team(
	display_name = "My Sample Team",
	description = "My sample team’s description",
	first_channel_name = "My first channel of the sample team",
	additional_data = {
			"template@odata_bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
	}
)

result = await graph_client.teams.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Location: /teams('dbd8de4f-5d47-48da-87f1-594bed003375')/operations('3a6fdce1-c261-48bc-89de-1cfef658c0d5')
Content-Location: /teams('dbd8de4f-5d47-48da-87f1-594bed003375')
Content-Length: 0
```

### Example 2: Application permissions

Here's an example of a minimal request using application permissions. By omitting other properties, the client is implicitly taking defaults from the predefined template represented by `template`. When issuing a request with application permissions, a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) must be specified in the `members` collection.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/teams
Content-Type: application/json

{
   "template@odata.bind":"https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
   "displayName":"My Sample Team",
   "description":"My sample team’s description",
   "firstChannelName": "My first channel of the sample team",
   "members":[
      {
         "@odata.type":"#microsoft.graph.aadUserConversationMember",
         "roles":[
            "owner"
         ],
         "user@odata.bind":"https://graph.microsoft.com/v1.0/users('0040b377-61d8-43db-94f5-81374122dc7e')"
      }
   ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Team
{
	DisplayName = "My Sample Team",
	Description = "My sample team’s description",
	FirstChannelName = "My first channel of the sample team",
	Members = new List<ConversationMember>
	{
		new AadUserConversationMember
		{
			OdataType = "#microsoft.graph.aadUserConversationMember",
			Roles = new List<string>
			{
				"owner",
			},
			AdditionalData = new Dictionary<string, object>
			{
				{
					"user@odata.bind" , "https://graph.microsoft.com/v1.0/users('0040b377-61d8-43db-94f5-81374122dc7e')"
				},
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"template@odata.bind" , "https://graph.microsoft.com/v1.0/teamsTemplates('standard')"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams.PostAsync(requestBody);
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
displayName := "My Sample Team"
requestBody.SetDisplayName(&displayName) 
description := "My sample team’s description"
requestBody.SetDescription(&description) 
firstChannelName := "My first channel of the sample team"
requestBody.SetFirstChannelName(&firstChannelName) 


conversationMember := graphmodels.NewAadUserConversationMember()
roles := []string {
	"owner",
}
conversationMember.SetRoles(roles)
additionalData := map[string]interface{}{
	"user@odata.bind" : "https://graph.microsoft.com/v1.0/users('0040b377-61d8-43db-94f5-81374122dc7e')", 
}
conversationMember.SetAdditionalData(additionalData)

members := []graphmodels.ConversationMemberable {
	conversationMember,
}
requestBody.SetMembers(members)
additionalData := map[string]interface{}{
	"template@odata.bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('standard')", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
teams, err := graphClient.Teams().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Team team = new Team();
team.setDisplayName("My Sample Team");
team.setDescription("My sample team’s description");
team.setFirstChannelName("My first channel of the sample team");
LinkedList<ConversationMember> members = new LinkedList<ConversationMember>();
AadUserConversationMember conversationMember = new AadUserConversationMember();
conversationMember.setOdataType("#microsoft.graph.aadUserConversationMember");
LinkedList<String> roles = new LinkedList<String>();
roles.add("owner");
conversationMember.setRoles(roles);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("user@odata.bind", "https://graph.microsoft.com/v1.0/users('0040b377-61d8-43db-94f5-81374122dc7e')");
conversationMember.setAdditionalData(additionalData);
members.add(conversationMember);
team.setMembers(members);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("template@odata.bind", "https://graph.microsoft.com/v1.0/teamsTemplates('standard')");
team.setAdditionalData(additionalData1);
Team result = graphClient.teams().post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const team = {
   'template@odata.bind':'https://graph.microsoft.com/v1.0/teamsTemplates(\'standard\')',
   displayName: 'My Sample Team',
   description: 'My sample team’s description',
   firstChannelName: 'My first channel of the sample team',
   members: [
      {
         '@odata.type':'#microsoft.graph.aadUserConversationMember',
         roles: [
            'owner'
         ],
         'user@odata.bind':'https://graph.microsoft.com/v1.0/users(\'0040b377-61d8-43db-94f5-81374122dc7e\')'
      }
   ]
};

await client.api('/teams')
	.post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Team;
use Microsoft\Graph\Generated\Models\ConversationMember;
use Microsoft\Graph\Generated\Models\AadUserConversationMember;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Team();
$requestBody->setDisplayName('My Sample Team');
$requestBody->setDescription('My sample team’s description');
$requestBody->setFirstChannelName('My first channel of the sample team');
$membersConversationMember1 = new AadUserConversationMember();
$membersConversationMember1->setOdataType('#microsoft.graph.aadUserConversationMember');
$membersConversationMember1->setRoles(['owner', 	]);
$additionalData = [
	'user@odata.bind' => 'https://graph.microsoft.com/v1.0/users(\'0040b377-61d8-43db-94f5-81374122dc7e\')',
];
$membersConversationMember1->setAdditionalData($additionalData);
$membersArray []= $membersConversationMember1;
$requestBody->setMembers($membersArray);

$additionalData = [
'template@odata.bind' => 'https://graph.microsoft.com/v1.0/teamsTemplates(\'standard\')',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->teams()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	"template@odata.bind" = "https://graph.microsoft.com/v1.0/teamsTemplates('standard')"
	displayName = "My Sample Team"
	description = "My sample team’s description"
	firstChannelName = "My first channel of the sample team"
	members = @(
		@{
			"@odata.type" = "#microsoft.graph.aadUserConversationMember"
			roles = @(
			"owner"
		)
		"user@odata.bind" = "https://graph.microsoft.com/v1.0/users('0040b377-61d8-43db-94f5-81374122dc7e')"
	}
)
}

New-MgTeam -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.team import Team
from msgraph.generated.models.conversation_member import ConversationMember
from msgraph.generated.models.aad_user_conversation_member import AadUserConversationMember
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Team(
	display_name = "My Sample Team",
	description = "My sample team’s description",
	first_channel_name = "My first channel of the sample team",
	members = [
		AadUserConversationMember(
			odata_type = "#microsoft.graph.aadUserConversationMember",
			roles = [
				"owner",
			],
			additional_data = {
					"user@odata_bind" : "https://graph.microsoft.com/v1.0/users('0040b377-61d8-43db-94f5-81374122dc7e')",
			}
		),
	],
	additional_data = {
			"template@odata_bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
	}
)

result = await graph_client.teams.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Location: /teams('dbd8de4f-5d47-48da-87f1-594bed003375')/operations('3a6fdce1-c261-48bc-89de-1cfef658c0d5')
Content-Location: /teams('dbd8de4f-5d47-48da-87f1-594bed003375')
Content-Length: 0
```

### Example 3: Create a team with multiple channels, installed apps, and pinned tabs using delegated permissions

Here's a request with a full payload. The client can override values in the base template and add to array-valued items to the extent allowed by validation rules for the `specialization`.

#### Request

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/teams
Content-Type: application/json

{
    "template@odata.bind": "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
    "visibility": "Private",
    "displayName": "Sample Engineering Team",
    "description": "This is a sample engineering team, used to showcase the range of properties supported by this API",
    "firstChannelName": "My First Channel of the team",
    "channels": [
        {
            "displayName": "Announcements 📢",
            "isFavoriteByDefault": true,
            "description": "This is a sample announcements channel that is favorited by default. Use this channel to make important team, product, and service announcements."
        },
        {
            "displayName": "Training 🏋️",
            "isFavoriteByDefault": true,
            "description": "This is a sample training channel, that is favorited by default, and contains an example of pinned website and YouTube tabs.",
            "tabs": [
                {
                    "teamsApp@odata.bind": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.web')",
                    "displayName": "A Pinned Website",
                    "configuration": {
                        "contentUrl": "https://learn.microsoft.com/microsoftteams/microsoft-teams"
                    }
                },
                {
                    "teamsApp@odata.bind": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.youtube')",
                    "displayName": "A Pinned YouTube Video",
                    "configuration": {
                        "contentUrl": "https://tabs.teams.microsoft.com/Youtube/Home/YoutubeTab?videoId=X8krAMdGvCQ",
                        "websiteUrl": "https://www.youtube.com/watch?v=X8krAMdGvCQ"
                    }
                }
            ]
        },
        {
            "displayName": "Planning 📅 ",
            "description": "This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu.",
            "isFavoriteByDefault": false
        },
        {
            "displayName": "Issues and Feedback 🐞",
            "description": "This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu."
        }
    ],
    "memberSettings": {
        "allowCreateUpdateChannels": true,
        "allowDeleteChannels": true,
        "allowAddRemoveApps": true,
        "allowCreateUpdateRemoveTabs": true,
        "allowCreateUpdateRemoveConnectors": true
    },
    "guestSettings": {
        "allowCreateUpdateChannels": false,
        "allowDeleteChannels": false
    },
    "funSettings": {
        "allowGiphy": true,
        "giphyContentRating": "Moderate",
        "allowStickersAndMemes": true,
        "allowCustomMemes": true
    },
    "messagingSettings": {
        "allowUserEditMessages": true,
        "allowUserDeleteMessages": true,
        "allowOwnerDeleteMessages": true,
        "allowTeamMentions": true,
        "allowChannelMentions": true
    },
    "discoverySettings": {
        "showInTeamsSearchAndSuggestions": true
    },
    "installedApps": [
        {
            "teamsApp@odata.bind": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')"
        },
        {
            "teamsApp@odata.bind": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new Team
{
	Visibility = TeamVisibilityType.Private,
	DisplayName = "Sample Engineering Team",
	Description = "This is a sample engineering team, used to showcase the range of properties supported by this API",
	FirstChannelName = "My First Channel of the team",
	Channels = new List<Channel>
	{
		new Channel
		{
			DisplayName = "Announcements 📢",
			IsFavoriteByDefault = true,
			Description = "This is a sample announcements channel that is favorited by default. Use this channel to make important team, product, and service announcements.",
		},
		new Channel
		{
			DisplayName = "Training 🏋️",
			IsFavoriteByDefault = true,
			Description = "This is a sample training channel, that is favorited by default, and contains an example of pinned website and YouTube tabs.",
			Tabs = new List<TeamsTab>
			{
				new TeamsTab
				{
					DisplayName = "A Pinned Website",
					Configuration = new TeamsTabConfiguration
					{
						ContentUrl = "https://learn.microsoft.com/microsoftteams/microsoft-teams",
					},
					AdditionalData = new Dictionary<string, object>
					{
						{
							"teamsApp@odata.bind" , "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.web')"
						},
					},
				},
				new TeamsTab
				{
					DisplayName = "A Pinned YouTube Video",
					Configuration = new TeamsTabConfiguration
					{
						ContentUrl = "https://tabs.teams.microsoft.com/Youtube/Home/YoutubeTab?videoId=X8krAMdGvCQ",
						WebsiteUrl = "https://www.youtube.com/watch?v=X8krAMdGvCQ",
					},
					AdditionalData = new Dictionary<string, object>
					{
						{
							"teamsApp@odata.bind" , "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.youtube')"
						},
					},
				},
			},
		},
		new Channel
		{
			DisplayName = "Planning 📅 ",
			Description = "This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu.",
			IsFavoriteByDefault = false,
		},
		new Channel
		{
			DisplayName = "Issues and Feedback 🐞",
			Description = "This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu.",
		},
	},
	MemberSettings = new TeamMemberSettings
	{
		AllowCreateUpdateChannels = true,
		AllowDeleteChannels = true,
		AllowAddRemoveApps = true,
		AllowCreateUpdateRemoveTabs = true,
		AllowCreateUpdateRemoveConnectors = true,
	},
	GuestSettings = new TeamGuestSettings
	{
		AllowCreateUpdateChannels = false,
		AllowDeleteChannels = false,
	},
	FunSettings = new TeamFunSettings
	{
		AllowGiphy = true,
		GiphyContentRating = GiphyRatingType.Moderate,
		AllowStickersAndMemes = true,
		AllowCustomMemes = true,
	},
	MessagingSettings = new TeamMessagingSettings
	{
		AllowUserEditMessages = true,
		AllowUserDeleteMessages = true,
		AllowOwnerDeleteMessages = true,
		AllowTeamMentions = true,
		AllowChannelMentions = true,
	},
	InstalledApps = new List<TeamsAppInstallation>
	{
		new TeamsAppInstallation
		{
			AdditionalData = new Dictionary<string, object>
			{
				{
					"teamsApp@odata.bind" , "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')"
				},
			},
		},
		new TeamsAppInstallation
		{
			AdditionalData = new Dictionary<string, object>
			{
				{
					"teamsApp@odata.bind" , "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')"
				},
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"template@odata.bind" , "https://graph.microsoft.com/v1.0/teamsTemplates('standard')"
		},
		{
			"discoverySettings" , new UntypedObject(new Dictionary<string, UntypedNode>
			{
				{
					"showInTeamsSearchAndSuggestions", new UntypedBoolean(true)
				},
			})
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams.PostAsync(requestBody);
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
visibility := graphmodels.PRIVATE_TEAMVISIBILITYTYPE 
requestBody.SetVisibility(&visibility) 
displayName := "Sample Engineering Team"
requestBody.SetDisplayName(&displayName) 
description := "This is a sample engineering team, used to showcase the range of properties supported by this API"
requestBody.SetDescription(&description) 
firstChannelName := "My First Channel of the team"
requestBody.SetFirstChannelName(&firstChannelName) 


channel := graphmodels.NewChannel()
displayName := "Announcements 📢"
channel.SetDisplayName(&displayName) 
isFavoriteByDefault := true
channel.SetIsFavoriteByDefault(&isFavoriteByDefault) 
description := "This is a sample announcements channel that is favorited by default. Use this channel to make important team, product, and service announcements."
channel.SetDescription(&description) 
channel1 := graphmodels.NewChannel()
displayName := "Training 🏋️"
channel1.SetDisplayName(&displayName) 
isFavoriteByDefault := true
channel1.SetIsFavoriteByDefault(&isFavoriteByDefault) 
description := "This is a sample training channel, that is favorited by default, and contains an example of pinned website and YouTube tabs."
channel1.SetDescription(&description) 


teamsTab := graphmodels.NewTeamsTab()
displayName := "A Pinned Website"
teamsTab.SetDisplayName(&displayName) 
configuration := graphmodels.NewTeamsTabConfiguration()
contentUrl := "https://learn.microsoft.com/microsoftteams/microsoft-teams"
configuration.SetContentUrl(&contentUrl) 
teamsTab.SetConfiguration(configuration)
additionalData := map[string]interface{}{
	"teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.web')", 
}
teamsTab.SetAdditionalData(additionalData)
teamsTab1 := graphmodels.NewTeamsTab()
displayName := "A Pinned YouTube Video"
teamsTab1.SetDisplayName(&displayName) 
configuration := graphmodels.NewTeamsTabConfiguration()
contentUrl := "https://tabs.teams.microsoft.com/Youtube/Home/YoutubeTab?videoId=X8krAMdGvCQ"
configuration.SetContentUrl(&contentUrl) 
websiteUrl := "https://www.youtube.com/watch?v=X8krAMdGvCQ"
configuration.SetWebsiteUrl(&websiteUrl) 
teamsTab1.SetConfiguration(configuration)
additionalData := map[string]interface{}{
	"teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.youtube')", 
}
teamsTab1.SetAdditionalData(additionalData)

tabs := []graphmodels.TeamsTabable {
	teamsTab,
	teamsTab1,
}
channel1.SetTabs(tabs)
channel2 := graphmodels.NewChannel()
displayName := "Planning 📅 "
channel2.SetDisplayName(&displayName) 
description := "This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu."
channel2.SetDescription(&description) 
isFavoriteByDefault := false
channel2.SetIsFavoriteByDefault(&isFavoriteByDefault) 
channel3 := graphmodels.NewChannel()
displayName := "Issues and Feedback 🐞"
channel3.SetDisplayName(&displayName) 
description := "This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu."
channel3.SetDescription(&description) 

channels := []graphmodels.Channelable {
	channel,
	channel1,
	channel2,
	channel3,
}
requestBody.SetChannels(channels)
memberSettings := graphmodels.NewTeamMemberSettings()
allowCreateUpdateChannels := true
memberSettings.SetAllowCreateUpdateChannels(&allowCreateUpdateChannels) 
allowDeleteChannels := true
memberSettings.SetAllowDeleteChannels(&allowDeleteChannels) 
allowAddRemoveApps := true
memberSettings.SetAllowAddRemoveApps(&allowAddRemoveApps) 
allowCreateUpdateRemoveTabs := true
memberSettings.SetAllowCreateUpdateRemoveTabs(&allowCreateUpdateRemoveTabs) 
allowCreateUpdateRemoveConnectors := true
memberSettings.SetAllowCreateUpdateRemoveConnectors(&allowCreateUpdateRemoveConnectors) 
requestBody.SetMemberSettings(memberSettings)
guestSettings := graphmodels.NewTeamGuestSettings()
allowCreateUpdateChannels := false
guestSettings.SetAllowCreateUpdateChannels(&allowCreateUpdateChannels) 
allowDeleteChannels := false
guestSettings.SetAllowDeleteChannels(&allowDeleteChannels) 
requestBody.SetGuestSettings(guestSettings)
funSettings := graphmodels.NewTeamFunSettings()
allowGiphy := true
funSettings.SetAllowGiphy(&allowGiphy) 
giphyContentRating := graphmodels.MODERATE_GIPHYRATINGTYPE 
funSettings.SetGiphyContentRating(&giphyContentRating) 
allowStickersAndMemes := true
funSettings.SetAllowStickersAndMemes(&allowStickersAndMemes) 
allowCustomMemes := true
funSettings.SetAllowCustomMemes(&allowCustomMemes) 
requestBody.SetFunSettings(funSettings)
messagingSettings := graphmodels.NewTeamMessagingSettings()
allowUserEditMessages := true
messagingSettings.SetAllowUserEditMessages(&allowUserEditMessages) 
allowUserDeleteMessages := true
messagingSettings.SetAllowUserDeleteMessages(&allowUserDeleteMessages) 
allowOwnerDeleteMessages := true
messagingSettings.SetAllowOwnerDeleteMessages(&allowOwnerDeleteMessages) 
allowTeamMentions := true
messagingSettings.SetAllowTeamMentions(&allowTeamMentions) 
allowChannelMentions := true
messagingSettings.SetAllowChannelMentions(&allowChannelMentions) 
requestBody.SetMessagingSettings(messagingSettings)


teamsAppInstallation := graphmodels.NewTeamsAppInstallation()
additionalData := map[string]interface{}{
	"teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')", 
}
teamsAppInstallation.SetAdditionalData(additionalData)
teamsAppInstallation1 := graphmodels.NewTeamsAppInstallation()
additionalData := map[string]interface{}{
	"teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')", 
}
teamsAppInstallation1.SetAdditionalData(additionalData)

installedApps := []graphmodels.TeamsAppInstallationable {
	teamsAppInstallation,
	teamsAppInstallation1,
}
requestBody.SetInstalledApps(installedApps)
additionalData := map[string]interface{}{
	"template@odata.bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('standard')", 
discoverySettings := graph.New()
	showInTeamsSearchAndSuggestions := true
discoverySettings.SetShowInTeamsSearchAndSuggestions(&showInTeamsSearchAndSuggestions) 
	requestBody.SetDiscoverySettings(discoverySettings)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
teams, err := graphClient.Teams().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Team team = new Team();
team.setVisibility(TeamVisibilityType.Private);
team.setDisplayName("Sample Engineering Team");
team.setDescription("This is a sample engineering team, used to showcase the range of properties supported by this API");
team.setFirstChannelName("My First Channel of the team");
LinkedList<Channel> channels = new LinkedList<Channel>();
Channel channel = new Channel();
channel.setDisplayName("Announcements 📢");
channel.setIsFavoriteByDefault(true);
channel.setDescription("This is a sample announcements channel that is favorited by default. Use this channel to make important team, product, and service announcements.");
channels.add(channel);
Channel channel1 = new Channel();
channel1.setDisplayName("Training 🏋️");
channel1.setIsFavoriteByDefault(true);
channel1.setDescription("This is a sample training channel, that is favorited by default, and contains an example of pinned website and YouTube tabs.");
LinkedList<TeamsTab> tabs = new LinkedList<TeamsTab>();
TeamsTab teamsTab = new TeamsTab();
teamsTab.setDisplayName("A Pinned Website");
TeamsTabConfiguration configuration = new TeamsTabConfiguration();
configuration.setContentUrl("https://learn.microsoft.com/microsoftteams/microsoft-teams");
teamsTab.setConfiguration(configuration);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("teamsApp@odata.bind", "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.web')");
teamsTab.setAdditionalData(additionalData);
tabs.add(teamsTab);
TeamsTab teamsTab1 = new TeamsTab();
teamsTab1.setDisplayName("A Pinned YouTube Video");
TeamsTabConfiguration configuration1 = new TeamsTabConfiguration();
configuration1.setContentUrl("https://tabs.teams.microsoft.com/Youtube/Home/YoutubeTab?videoId=X8krAMdGvCQ");
configuration1.setWebsiteUrl("https://www.youtube.com/watch?v=X8krAMdGvCQ");
teamsTab1.setConfiguration(configuration1);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("teamsApp@odata.bind", "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.youtube')");
teamsTab1.setAdditionalData(additionalData1);
tabs.add(teamsTab1);
channel1.setTabs(tabs);
channels.add(channel1);
Channel channel2 = new Channel();
channel2.setDisplayName("Planning 📅 ");
channel2.setDescription("This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu.");
channel2.setIsFavoriteByDefault(false);
channels.add(channel2);
Channel channel3 = new Channel();
channel3.setDisplayName("Issues and Feedback 🐞");
channel3.setDescription("This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu.");
channels.add(channel3);
team.setChannels(channels);
TeamMemberSettings memberSettings = new TeamMemberSettings();
memberSettings.setAllowCreateUpdateChannels(true);
memberSettings.setAllowDeleteChannels(true);
memberSettings.setAllowAddRemoveApps(true);
memberSettings.setAllowCreateUpdateRemoveTabs(true);
memberSettings.setAllowCreateUpdateRemoveConnectors(true);
team.setMemberSettings(memberSettings);
TeamGuestSettings guestSettings = new TeamGuestSettings();
guestSettings.setAllowCreateUpdateChannels(false);
guestSettings.setAllowDeleteChannels(false);
team.setGuestSettings(guestSettings);
TeamFunSettings funSettings = new TeamFunSettings();
funSettings.setAllowGiphy(true);
funSettings.setGiphyContentRating(GiphyRatingType.Moderate);
funSettings.setAllowStickersAndMemes(true);
funSettings.setAllowCustomMemes(true);
team.setFunSettings(funSettings);
TeamMessagingSettings messagingSettings = new TeamMessagingSettings();
messagingSettings.setAllowUserEditMessages(true);
messagingSettings.setAllowUserDeleteMessages(true);
messagingSettings.setAllowOwnerDeleteMessages(true);
messagingSettings.setAllowTeamMentions(true);
messagingSettings.setAllowChannelMentions(true);
team.setMessagingSettings(messagingSettings);
LinkedList<TeamsAppInstallation> installedApps = new LinkedList<TeamsAppInstallation>();
TeamsAppInstallation teamsAppInstallation = new TeamsAppInstallation();
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
additionalData2.put("teamsApp@odata.bind", "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')");
teamsAppInstallation.setAdditionalData(additionalData2);
installedApps.add(teamsAppInstallation);
TeamsAppInstallation teamsAppInstallation1 = new TeamsAppInstallation();
HashMap<String, Object> additionalData3 = new HashMap<String, Object>();
additionalData3.put("teamsApp@odata.bind", "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')");
teamsAppInstallation1.setAdditionalData(additionalData3);
installedApps.add(teamsAppInstallation1);
team.setInstalledApps(installedApps);
HashMap<String, Object> additionalData4 = new HashMap<String, Object>();
additionalData4.put("template@odata.bind", "https://graph.microsoft.com/v1.0/teamsTemplates('standard')");
 discoverySettings = new ();
discoverySettings.setShowInTeamsSearchAndSuggestions(true);
additionalData4.put("discoverySettings", discoverySettings);
team.setAdditionalData(additionalData4);
Team result = graphClient.teams().post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const team = {
    'template@odata.bind': 'https://graph.microsoft.com/v1.0/teamsTemplates(\'standard\')',
    visibility: 'Private',
    displayName: 'Sample Engineering Team',
    description: 'This is a sample engineering team, used to showcase the range of properties supported by this API',
    firstChannelName: 'My First Channel of the team',
    channels: [
        {
            displayName: 'Announcements 📢',
            isFavoriteByDefault: true,
            description: 'This is a sample announcements channel that is favorited by default. Use this channel to make important team, product, and service announcements.'
        },
        {
            displayName: 'Training 🏋️',
            isFavoriteByDefault: true,
            description: 'This is a sample training channel, that is favorited by default, and contains an example of pinned website and YouTube tabs.',
            tabs: [
                {
                    'teamsApp@odata.bind': 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'com.microsoft.teamspace.tab.web\')',
                    displayName: 'A Pinned Website',
                    configuration: {
                        contentUrl: 'https://learn.microsoft.com/microsoftteams/microsoft-teams'
                    }
                },
                {
                    'teamsApp@odata.bind': 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'com.microsoft.teamspace.tab.youtube\')',
                    displayName: 'A Pinned YouTube Video',
                    configuration: {
                        contentUrl: 'https://tabs.teams.microsoft.com/Youtube/Home/YoutubeTab?videoId=X8krAMdGvCQ',
                        websiteUrl: 'https://www.youtube.com/watch?v=X8krAMdGvCQ'
                    }
                }
            ]
        },
        {
            displayName: 'Planning 📅 ',
            description: 'This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu.',
            isFavoriteByDefault: false
        },
        {
            displayName: 'Issues and Feedback 🐞',
            description: 'This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu.'
        }
    ],
    memberSettings: {
        allowCreateUpdateChannels: true,
        allowDeleteChannels: true,
        allowAddRemoveApps: true,
        allowCreateUpdateRemoveTabs: true,
        allowCreateUpdateRemoveConnectors: true
    },
    guestSettings: {
        allowCreateUpdateChannels: false,
        allowDeleteChannels: false
    },
    funSettings: {
        allowGiphy: true,
        giphyContentRating: 'Moderate',
        allowStickersAndMemes: true,
        allowCustomMemes: true
    },
    messagingSettings: {
        allowUserEditMessages: true,
        allowUserDeleteMessages: true,
        allowOwnerDeleteMessages: true,
        allowTeamMentions: true,
        allowChannelMentions: true
    },
    discoverySettings: {
        showInTeamsSearchAndSuggestions: true
    },
    installedApps: [
        {
            'teamsApp@odata.bind': 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'com.microsoft.teamspace.tab.vsts\')'
        },
        {
            'teamsApp@odata.bind': 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'1542629c-01b3-4a6d-8f76-1938b779e48d\')'
        }
    ]
};

await client.api('/teams')
	.post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Team;
use Microsoft\Graph\Generated\Models\TeamVisibilityType;
use Microsoft\Graph\Generated\Models\Channel;
use Microsoft\Graph\Generated\Models\TeamsTab;
use Microsoft\Graph\Generated\Models\TeamsTabConfiguration;
use Microsoft\Graph\Generated\Models\TeamMemberSettings;
use Microsoft\Graph\Generated\Models\TeamGuestSettings;
use Microsoft\Graph\Generated\Models\TeamFunSettings;
use Microsoft\Graph\Generated\Models\GiphyRatingType;
use Microsoft\Graph\Generated\Models\TeamMessagingSettings;
use Microsoft\Graph\Generated\Models\TeamsAppInstallation;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Team();
$requestBody->setVisibility(new TeamVisibilityType('private'));
$requestBody->setDisplayName('Sample Engineering Team');
$requestBody->setDescription('This is a sample engineering team, used to showcase the range of properties supported by this API');
$requestBody->setFirstChannelName('My First Channel of the team');
$channelsChannel1 = new Channel();
$channelsChannel1->setDisplayName('Announcements 📢');
$channelsChannel1->setIsFavoriteByDefault(true);
$channelsChannel1->setDescription('This is a sample announcements channel that is favorited by default. Use this channel to make important team, product, and service announcements.');
$channelsArray []= $channelsChannel1;
$channelsChannel2 = new Channel();
$channelsChannel2->setDisplayName('Training 🏋️');
$channelsChannel2->setIsFavoriteByDefault(true);
$channelsChannel2->setDescription('This is a sample training channel, that is favorited by default, and contains an example of pinned website and YouTube tabs.');
$tabsTeamsTab1 = new TeamsTab();
$tabsTeamsTab1->setDisplayName('A Pinned Website');
$tabsTeamsTab1Configuration = new TeamsTabConfiguration();
$tabsTeamsTab1Configuration->setContentUrl('https://learn.microsoft.com/microsoftteams/microsoft-teams');
$tabsTeamsTab1->setConfiguration($tabsTeamsTab1Configuration);
$additionalData = [
	'teamsApp@odata.bind' => 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'com.microsoft.teamspace.tab.web\')',
];
$tabsTeamsTab1->setAdditionalData($additionalData);
$tabsArray []= $tabsTeamsTab1;
$tabsTeamsTab2 = new TeamsTab();
$tabsTeamsTab2->setDisplayName('A Pinned YouTube Video');
$tabsTeamsTab2Configuration = new TeamsTabConfiguration();
$tabsTeamsTab2Configuration->setContentUrl('https://tabs.teams.microsoft.com/Youtube/Home/YoutubeTab?videoId=X8krAMdGvCQ');
$tabsTeamsTab2Configuration->setWebsiteUrl('https://www.youtube.com/watch?v=X8krAMdGvCQ');
$tabsTeamsTab2->setConfiguration($tabsTeamsTab2Configuration);
$additionalData = [
	'teamsApp@odata.bind' => 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'com.microsoft.teamspace.tab.youtube\')',
];
$tabsTeamsTab2->setAdditionalData($additionalData);
$tabsArray []= $tabsTeamsTab2;
$channelsChannel2->setTabs($tabsArray);

$channelsArray []= $channelsChannel2;
$channelsChannel3 = new Channel();
$channelsChannel3->setDisplayName('Planning 📅 ');
$channelsChannel3->setDescription('This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu.');
$channelsChannel3->setIsFavoriteByDefault(false);
$channelsArray []= $channelsChannel3;
$channelsChannel4 = new Channel();
$channelsChannel4->setDisplayName('Issues and Feedback 🐞');
$channelsChannel4->setDescription('This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu.');
$channelsArray []= $channelsChannel4;
$requestBody->setChannels($channelsArray);

$memberSettings = new TeamMemberSettings();
$memberSettings->setAllowCreateUpdateChannels(true);
$memberSettings->setAllowDeleteChannels(true);
$memberSettings->setAllowAddRemoveApps(true);
$memberSettings->setAllowCreateUpdateRemoveTabs(true);
$memberSettings->setAllowCreateUpdateRemoveConnectors(true);
$requestBody->setMemberSettings($memberSettings);
$guestSettings = new TeamGuestSettings();
$guestSettings->setAllowCreateUpdateChannels(false);
$guestSettings->setAllowDeleteChannels(false);
$requestBody->setGuestSettings($guestSettings);
$funSettings = new TeamFunSettings();
$funSettings->setAllowGiphy(true);
$funSettings->setGiphyContentRating(new GiphyRatingType('moderate'));
$funSettings->setAllowStickersAndMemes(true);
$funSettings->setAllowCustomMemes(true);
$requestBody->setFunSettings($funSettings);
$messagingSettings = new TeamMessagingSettings();
$messagingSettings->setAllowUserEditMessages(true);
$messagingSettings->setAllowUserDeleteMessages(true);
$messagingSettings->setAllowOwnerDeleteMessages(true);
$messagingSettings->setAllowTeamMentions(true);
$messagingSettings->setAllowChannelMentions(true);
$requestBody->setMessagingSettings($messagingSettings);
$installedAppsTeamsAppInstallation1 = new TeamsAppInstallation();
$additionalData = [
'teamsApp@odata.bind' => 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'com.microsoft.teamspace.tab.vsts\')',
];
$installedAppsTeamsAppInstallation1->setAdditionalData($additionalData);
$installedAppsArray []= $installedAppsTeamsAppInstallation1;
$installedAppsTeamsAppInstallation2 = new TeamsAppInstallation();
$additionalData = [
'teamsApp@odata.bind' => 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'1542629c-01b3-4a6d-8f76-1938b779e48d\')',
];
$installedAppsTeamsAppInstallation2->setAdditionalData($additionalData);
$installedAppsArray []= $installedAppsTeamsAppInstallation2;
$requestBody->setInstalledApps($installedAppsArray);

$additionalData = [
'template@odata.bind' => 'https://graph.microsoft.com/v1.0/teamsTemplates(\'standard\')',
'discoverySettings' => [
'showInTeamsSearchAndSuggestions' => true,
],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->teams()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	"template@odata.bind" = "https://graph.microsoft.com/v1.0/teamsTemplates('standard')"
	visibility = "Private"
	displayName = "Sample Engineering Team"
	description = "This is a sample engineering team, used to showcase the range of properties supported by this API"
	firstChannelName = "My First Channel of the team"
	channels = @(
		@{
			displayName = "Announcements 📢"
			isFavoriteByDefault = $true
			description = "This is a sample announcements channel that is favorited by default. Use this channel to make important team, product, and service announcements."
		}
		@{
			displayName = "Training 🏋️"
			isFavoriteByDefault = $true
			description = "This is a sample training channel, that is favorited by default, and contains an example of pinned website and YouTube tabs."
			tabs = @(
				@{
					"teamsApp@odata.bind" = "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.web')"
					displayName = "A Pinned Website"
					configuration = @{
						contentUrl = "https://learn.microsoft.com/microsoftteams/microsoft-teams"
					}
				}
				@{
					"teamsApp@odata.bind" = "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.youtube')"
					displayName = "A Pinned YouTube Video"
					configuration = @{
						contentUrl = "https://tabs.teams.microsoft.com/Youtube/Home/YoutubeTab?videoId=X8krAMdGvCQ"
						websiteUrl = "https://www.youtube.com/watch?v=X8krAMdGvCQ"
					}
				}
			)
		}
		@{
			displayName = "Planning 📅 "
			description = "This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu."
			isFavoriteByDefault = $false
		}
		@{
			displayName = "Issues and Feedback 🐞"
			description = "This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu."
		}
	)
	memberSettings = @{
		allowCreateUpdateChannels = $true
		allowDeleteChannels = $true
		allowAddRemoveApps = $true
		allowCreateUpdateRemoveTabs = $true
		allowCreateUpdateRemoveConnectors = $true
	}
	guestSettings = @{
		allowCreateUpdateChannels = $false
		allowDeleteChannels = $false
	}
	funSettings = @{
		allowGiphy = $true
		giphyContentRating = "Moderate"
		allowStickersAndMemes = $true
		allowCustomMemes = $true
	}
	messagingSettings = @{
		allowUserEditMessages = $true
		allowUserDeleteMessages = $true
		allowOwnerDeleteMessages = $true
		allowTeamMentions = $true
		allowChannelMentions = $true
	}
	discoverySettings = @{
		showInTeamsSearchAndSuggestions = $true
	}
	installedApps = @(
		@{
			"teamsApp@odata.bind" = "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')"
		}
		@{
			"teamsApp@odata.bind" = "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')"
		}
	)
}

New-MgTeam -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.team import Team
from msgraph.generated.models.team_visibility_type import TeamVisibilityType
from msgraph.generated.models.channel import Channel
from msgraph.generated.models.teams_tab import TeamsTab
from msgraph.generated.models.teams_tab_configuration import TeamsTabConfiguration
from msgraph.generated.models.team_member_settings import TeamMemberSettings
from msgraph.generated.models.team_guest_settings import TeamGuestSettings
from msgraph.generated.models.team_fun_settings import TeamFunSettings
from msgraph.generated.models.giphy_rating_type import GiphyRatingType
from msgraph.generated.models.team_messaging_settings import TeamMessagingSettings
from msgraph.generated.models.teams_app_installation import TeamsAppInstallation
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Team(
	visibility = TeamVisibilityType.Private,
	display_name = "Sample Engineering Team",
	description = "This is a sample engineering team, used to showcase the range of properties supported by this API",
	first_channel_name = "My First Channel of the team",
	channels = [
		Channel(
			display_name = "Announcements 📢",
			is_favorite_by_default = True,
			description = "This is a sample announcements channel that is favorited by default. Use this channel to make important team, product, and service announcements.",
		),
		Channel(
			display_name = "Training 🏋️",
			is_favorite_by_default = True,
			description = "This is a sample training channel, that is favorited by default, and contains an example of pinned website and YouTube tabs.",
			tabs = [
				TeamsTab(
					display_name = "A Pinned Website",
					configuration = TeamsTabConfiguration(
						content_url = "https://learn.microsoft.com/microsoftteams/microsoft-teams",
					),
					additional_data = {
							"teams_app@odata_bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.web')",
					}
				),
				TeamsTab(
					display_name = "A Pinned YouTube Video",
					configuration = TeamsTabConfiguration(
						content_url = "https://tabs.teams.microsoft.com/Youtube/Home/YoutubeTab?videoId=X8krAMdGvCQ",
						website_url = "https://www.youtube.com/watch?v=X8krAMdGvCQ",
					),
					additional_data = {
							"teams_app@odata_bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.youtube')",
					}
				),
			],
		),
		Channel(
			display_name = "Planning 📅 ",
			description = "This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu.",
			is_favorite_by_default = False,
		),
		Channel(
			display_name = "Issues and Feedback 🐞",
			description = "This is a sample of a channel that is not favorited by default, these channels will appear in the more channels overflow menu.",
		),
	],
	member_settings = TeamMemberSettings(
		allow_create_update_channels = True,
		allow_delete_channels = True,
		allow_add_remove_apps = True,
		allow_create_update_remove_tabs = True,
		allow_create_update_remove_connectors = True,
	),
	guest_settings = TeamGuestSettings(
		allow_create_update_channels = False,
		allow_delete_channels = False,
	),
	fun_settings = TeamFunSettings(
		allow_giphy = True,
		giphy_content_rating = GiphyRatingType.Moderate,
		allow_stickers_and_memes = True,
		allow_custom_memes = True,
	),
	messaging_settings = TeamMessagingSettings(
		allow_user_edit_messages = True,
		allow_user_delete_messages = True,
		allow_owner_delete_messages = True,
		allow_team_mentions = True,
		allow_channel_mentions = True,
	),
	installed_apps = [
		TeamsAppInstallation(
			additional_data = {
					"teams_app@odata_bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')",
			}
		),
		TeamsAppInstallation(
			additional_data = {
					"teams_app@odata_bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')",
			}
		),
	],
	additional_data = {
			"template@odata_bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
			"discovery_settings" : {
					"show_in_teams_search_and_suggestions" : True,
			},
	}
)

result = await graph_client.teams.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Location: /teams('958e8cf8-169a-42aa-8599-5c1c5479c0ca')/operations('00000000-0000-0000-0000-000000000000')
Content-Location: /teams('958e8cf8-169a-42aa-8599-5c1c5479c0ca')
Content-Length: 0
```

### Example 4: Create a team from group

The following example shows how you can create a new [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) from a [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0), given a **groupId**.

A few things to note about this call:

- To create a team, the group you create it from must have at least one owner.
- The team that's created always inherits properties such as display name, visibility, specialization, and members from the group. Therefore, when you make this call with the **group@odata.bind** property, the inclusion of team **displayName**, **visibility**, **specialization**, or **members@odata.bind** properties return an error.
- If the group was created less than 15 minutes ago, it's possible for the Create team call to fail with a 404 error code due to replication delays. We recommend that you retry the Create team call three times, with a 10-second delay between calls. Learn more in [Designing for eventual consistency for Microsoft Entra](https://devblogs.microsoft.com/identity/designing-for-eventual-consistency-for-microsoft-entra/).
- Specifying a first channel name with the **firstChannelName** property isn't supported when you create a team from a group.

#### Request

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/teams
Content-Type: application/json

{
  "template@odata.bind": "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
  "group@odata.bind": "https://graph.microsoft.com/v1.0/groups('71392b2f-1765-406e-86af-5907d9bdb2ab')"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Team
{
	AdditionalData = new Dictionary<string, object>
	{
		{
			"template@odata.bind" , "https://graph.microsoft.com/v1.0/teamsTemplates('standard')"
		},
		{
			"group@odata.bind" , "https://graph.microsoft.com/v1.0/groups('71392b2f-1765-406e-86af-5907d9bdb2ab')"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams.PostAsync(requestBody);
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
additionalData := map[string]interface{}{
	"template@odata.bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('standard')", 
	"group@odata.bind" : "https://graph.microsoft.com/v1.0/groups('71392b2f-1765-406e-86af-5907d9bdb2ab')", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
teams, err := graphClient.Teams().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Team team = new Team();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("template@odata.bind", "https://graph.microsoft.com/v1.0/teamsTemplates('standard')");
additionalData.put("group@odata.bind", "https://graph.microsoft.com/v1.0/groups('71392b2f-1765-406e-86af-5907d9bdb2ab')");
team.setAdditionalData(additionalData);
Team result = graphClient.teams().post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const team = {
  'template@odata.bind': 'https://graph.microsoft.com/v1.0/teamsTemplates(\'standard\')',
  'group@odata.bind': 'https://graph.microsoft.com/v1.0/groups(\'71392b2f-1765-406e-86af-5907d9bdb2ab\')'
};

await client.api('/teams')
	.post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Team;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Team();
$additionalData = [
	'template@odata.bind' => 'https://graph.microsoft.com/v1.0/teamsTemplates(\'standard\')',
	'group@odata.bind' => 'https://graph.microsoft.com/v1.0/groups(\'71392b2f-1765-406e-86af-5907d9bdb2ab\')',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->teams()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	"template@odata.bind" = "https://graph.microsoft.com/v1.0/teamsTemplates('standard')"
	"group@odata.bind" = "https://graph.microsoft.com/v1.0/groups('71392b2f-1765-406e-86af-5907d9bdb2ab')"
}

New-MgTeam -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.team import Team
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Team(
	additional_data = {
			"template@odata_bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
			"group@odata_bind" : "https://graph.microsoft.com/v1.0/groups('71392b2f-1765-406e-86af-5907d9bdb2ab')",
	}
)

result = await graph_client.teams.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Location: /teams('71392b2f-1765-406e-86af-5907d9bdb2ab')/operations('9698b2b8-9636-4f49-b7a8-10dadfa7062a')
Content-Location: /teams('71392b2f-1765-406e-86af-5907d9bdb2ab')
Content-Length: 0
```

### Example 5: Create a team from a group with multiple channels, installed apps, and pinned tabs

Here's a request that converts an existing group with extended properties that will create the team with multiple channels, installed apps, and pinned tabs.

To learn more about supported base template types and supported properties, see [Get started with Teams templates](https://learn.microsoft.com/en-us/MicrosoftTeams/get-started-with-teams-templates).

#### Request

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/teams
Content-Type: application/json

{
   "template@odata.bind":"https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
   "group@odata.bind":"https://graph.microsoft.com/v1.0/groups('dbd8de4f-5d47-48da-87f1-594bed003375')",
   "channels":[
      {
         "displayName":"Class Announcements 📢",
         "isFavoriteByDefault":true
      },
      {
         "displayName":"Homework 🏋️",
         "isFavoriteByDefault":true
      }
   ],
   "memberSettings":{
      "allowCreateUpdateChannels":false,
      "allowDeleteChannels":false,
      "allowAddRemoveApps":false,
      "allowCreateUpdateRemoveTabs":false,
      "allowCreateUpdateRemoveConnectors":false
   },
   "installedApps":[
      {
         "teamsApp@odata.bind":"https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')"
      },
      {
         "teamsApp@odata.bind":"https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')"
      }
   ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Team
{
	Channels = new List<Channel>
	{
		new Channel
		{
			DisplayName = "Class Announcements 📢",
			IsFavoriteByDefault = true,
		},
		new Channel
		{
			DisplayName = "Homework 🏋️",
			IsFavoriteByDefault = true,
		},
	},
	MemberSettings = new TeamMemberSettings
	{
		AllowCreateUpdateChannels = false,
		AllowDeleteChannels = false,
		AllowAddRemoveApps = false,
		AllowCreateUpdateRemoveTabs = false,
		AllowCreateUpdateRemoveConnectors = false,
	},
	InstalledApps = new List<TeamsAppInstallation>
	{
		new TeamsAppInstallation
		{
			AdditionalData = new Dictionary<string, object>
			{
				{
					"teamsApp@odata.bind" , "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')"
				},
			},
		},
		new TeamsAppInstallation
		{
			AdditionalData = new Dictionary<string, object>
			{
				{
					"teamsApp@odata.bind" , "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')"
				},
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"template@odata.bind" , "https://graph.microsoft.com/v1.0/teamsTemplates('standard')"
		},
		{
			"group@odata.bind" , "https://graph.microsoft.com/v1.0/groups('dbd8de4f-5d47-48da-87f1-594bed003375')"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams.PostAsync(requestBody);
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


channel := graphmodels.NewChannel()
displayName := "Class Announcements 📢"
channel.SetDisplayName(&displayName) 
isFavoriteByDefault := true
channel.SetIsFavoriteByDefault(&isFavoriteByDefault) 
channel1 := graphmodels.NewChannel()
displayName := "Homework 🏋️"
channel1.SetDisplayName(&displayName) 
isFavoriteByDefault := true
channel1.SetIsFavoriteByDefault(&isFavoriteByDefault) 

channels := []graphmodels.Channelable {
	channel,
	channel1,
}
requestBody.SetChannels(channels)
memberSettings := graphmodels.NewTeamMemberSettings()
allowCreateUpdateChannels := false
memberSettings.SetAllowCreateUpdateChannels(&allowCreateUpdateChannels) 
allowDeleteChannels := false
memberSettings.SetAllowDeleteChannels(&allowDeleteChannels) 
allowAddRemoveApps := false
memberSettings.SetAllowAddRemoveApps(&allowAddRemoveApps) 
allowCreateUpdateRemoveTabs := false
memberSettings.SetAllowCreateUpdateRemoveTabs(&allowCreateUpdateRemoveTabs) 
allowCreateUpdateRemoveConnectors := false
memberSettings.SetAllowCreateUpdateRemoveConnectors(&allowCreateUpdateRemoveConnectors) 
requestBody.SetMemberSettings(memberSettings)


teamsAppInstallation := graphmodels.NewTeamsAppInstallation()
additionalData := map[string]interface{}{
	"teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')", 
}
teamsAppInstallation.SetAdditionalData(additionalData)
teamsAppInstallation1 := graphmodels.NewTeamsAppInstallation()
additionalData := map[string]interface{}{
	"teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')", 
}
teamsAppInstallation1.SetAdditionalData(additionalData)

installedApps := []graphmodels.TeamsAppInstallationable {
	teamsAppInstallation,
	teamsAppInstallation1,
}
requestBody.SetInstalledApps(installedApps)
additionalData := map[string]interface{}{
	"template@odata.bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('standard')", 
	"group@odata.bind" : "https://graph.microsoft.com/v1.0/groups('dbd8de4f-5d47-48da-87f1-594bed003375')", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
teams, err := graphClient.Teams().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Team team = new Team();
LinkedList<Channel> channels = new LinkedList<Channel>();
Channel channel = new Channel();
channel.setDisplayName("Class Announcements 📢");
channel.setIsFavoriteByDefault(true);
channels.add(channel);
Channel channel1 = new Channel();
channel1.setDisplayName("Homework 🏋️");
channel1.setIsFavoriteByDefault(true);
channels.add(channel1);
team.setChannels(channels);
TeamMemberSettings memberSettings = new TeamMemberSettings();
memberSettings.setAllowCreateUpdateChannels(false);
memberSettings.setAllowDeleteChannels(false);
memberSettings.setAllowAddRemoveApps(false);
memberSettings.setAllowCreateUpdateRemoveTabs(false);
memberSettings.setAllowCreateUpdateRemoveConnectors(false);
team.setMemberSettings(memberSettings);
LinkedList<TeamsAppInstallation> installedApps = new LinkedList<TeamsAppInstallation>();
TeamsAppInstallation teamsAppInstallation = new TeamsAppInstallation();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("teamsApp@odata.bind", "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')");
teamsAppInstallation.setAdditionalData(additionalData);
installedApps.add(teamsAppInstallation);
TeamsAppInstallation teamsAppInstallation1 = new TeamsAppInstallation();
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("teamsApp@odata.bind", "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')");
teamsAppInstallation1.setAdditionalData(additionalData1);
installedApps.add(teamsAppInstallation1);
team.setInstalledApps(installedApps);
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
additionalData2.put("template@odata.bind", "https://graph.microsoft.com/v1.0/teamsTemplates('standard')");
additionalData2.put("group@odata.bind", "https://graph.microsoft.com/v1.0/groups('dbd8de4f-5d47-48da-87f1-594bed003375')");
team.setAdditionalData(additionalData2);
Team result = graphClient.teams().post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const team = {
   'template@odata.bind':'https://graph.microsoft.com/v1.0/teamsTemplates(\'standard\')',
   'group@odata.bind':'https://graph.microsoft.com/v1.0/groups(\'dbd8de4f-5d47-48da-87f1-594bed003375\')',
   channels: [
      {
         displayName: 'Class Announcements 📢',
         isFavoriteByDefault: true
      },
      {
         displayName: 'Homework 🏋️',
         isFavoriteByDefault: true
      }
   ],
   memberSettings: {
      allowCreateUpdateChannels: false,
      allowDeleteChannels: false,
      allowAddRemoveApps: false,
      allowCreateUpdateRemoveTabs: false,
      allowCreateUpdateRemoveConnectors: false
   },
   installedApps: [
      {
         'teamsApp@odata.bind':'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'com.microsoft.teamspace.tab.vsts\')'
      },
      {
         'teamsApp@odata.bind':'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'1542629c-01b3-4a6d-8f76-1938b779e48d\')'
      }
   ]
};

await client.api('/teams')
	.post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Team;
use Microsoft\Graph\Generated\Models\Channel;
use Microsoft\Graph\Generated\Models\TeamMemberSettings;
use Microsoft\Graph\Generated\Models\TeamsAppInstallation;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Team();
$channelsChannel1 = new Channel();
$channelsChannel1->setDisplayName('Class Announcements 📢');
$channelsChannel1->setIsFavoriteByDefault(true);
$channelsArray []= $channelsChannel1;
$channelsChannel2 = new Channel();
$channelsChannel2->setDisplayName('Homework 🏋️');
$channelsChannel2->setIsFavoriteByDefault(true);
$channelsArray []= $channelsChannel2;
$requestBody->setChannels($channelsArray);

$memberSettings = new TeamMemberSettings();
$memberSettings->setAllowCreateUpdateChannels(false);
$memberSettings->setAllowDeleteChannels(false);
$memberSettings->setAllowAddRemoveApps(false);
$memberSettings->setAllowCreateUpdateRemoveTabs(false);
$memberSettings->setAllowCreateUpdateRemoveConnectors(false);
$requestBody->setMemberSettings($memberSettings);
$installedAppsTeamsAppInstallation1 = new TeamsAppInstallation();
$additionalData = [
'teamsApp@odata.bind' => 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'com.microsoft.teamspace.tab.vsts\')',
];
$installedAppsTeamsAppInstallation1->setAdditionalData($additionalData);
$installedAppsArray []= $installedAppsTeamsAppInstallation1;
$installedAppsTeamsAppInstallation2 = new TeamsAppInstallation();
$additionalData = [
'teamsApp@odata.bind' => 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'1542629c-01b3-4a6d-8f76-1938b779e48d\')',
];
$installedAppsTeamsAppInstallation2->setAdditionalData($additionalData);
$installedAppsArray []= $installedAppsTeamsAppInstallation2;
$requestBody->setInstalledApps($installedAppsArray);

$additionalData = [
'template@odata.bind' => 'https://graph.microsoft.com/v1.0/teamsTemplates(\'standard\')',
'group@odata.bind' => 'https://graph.microsoft.com/v1.0/groups(\'dbd8de4f-5d47-48da-87f1-594bed003375\')',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->teams()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	"template@odata.bind" = "https://graph.microsoft.com/v1.0/teamsTemplates('standard')"
	"group@odata.bind" = "https://graph.microsoft.com/v1.0/groups('dbd8de4f-5d47-48da-87f1-594bed003375')"
	channels = @(
		@{
			displayName = "Class Announcements 📢"
			isFavoriteByDefault = $true
		}
		@{
			displayName = "Homework 🏋️"
			isFavoriteByDefault = $true
		}
	)
	memberSettings = @{
		allowCreateUpdateChannels = $false
		allowDeleteChannels = $false
		allowAddRemoveApps = $false
		allowCreateUpdateRemoveTabs = $false
		allowCreateUpdateRemoveConnectors = $false
	}
	installedApps = @(
		@{
			"teamsApp@odata.bind" = "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')"
		}
		@{
			"teamsApp@odata.bind" = "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')"
		}
	)
}

New-MgTeam -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.team import Team
from msgraph.generated.models.channel import Channel
from msgraph.generated.models.team_member_settings import TeamMemberSettings
from msgraph.generated.models.teams_app_installation import TeamsAppInstallation
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Team(
	channels = [
		Channel(
			display_name = "Class Announcements 📢",
			is_favorite_by_default = True,
		),
		Channel(
			display_name = "Homework 🏋️",
			is_favorite_by_default = True,
		),
	],
	member_settings = TeamMemberSettings(
		allow_create_update_channels = False,
		allow_delete_channels = False,
		allow_add_remove_apps = False,
		allow_create_update_remove_tabs = False,
		allow_create_update_remove_connectors = False,
	),
	installed_apps = [
		TeamsAppInstallation(
			additional_data = {
					"teams_app@odata_bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')",
			}
		),
		TeamsAppInstallation(
			additional_data = {
					"teams_app@odata_bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')",
			}
		),
	],
	additional_data = {
			"template@odata_bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
			"group@odata_bind" : "https://graph.microsoft.com/v1.0/groups('dbd8de4f-5d47-48da-87f1-594bed003375')",
	}
)

result = await graph_client.teams.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Location: /teams('dbd8de4f-5d47-48da-87f1-594bed003375')/operations('3a6fdce1-c261-48bc-89de-1cfef658c0d5')
Content-Location: /teams('dbd8de4f-5d47-48da-87f1-594bed003375')
Content-Length: 0
```

### Example 6: Create a team with a non-standard base template type

Base template types are special templates that Microsoft created for specific industries. These base templates often contain proprietary apps that aren't available in the store and team properties that aren't yet supported individually in Microsoft Teams templates.

To create a team from a non-standard base template, you want to change the `template@odata.bind` property in the request body from `standard` to point to the specific base template you’d like to create.

To learn more about supported base template types, see [Get started with Teams templates](https://learn.microsoft.com/en-us/MicrosoftTeams/get-started-with-teams-templates).

Note

It can take up to 24 hours for Teams users to see a custom template change in the gallery.

#### Request

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/v1.0/teams
Content-Type: application/json

{
  "template@odata.bind": "https://graph.microsoft.com/v1.0/teamsTemplates('educationClass')",
  "displayName": "My Class Team",
  "description": "My Class Team’s Description"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Team
{
	DisplayName = "My Class Team",
	Description = "My Class Team’s Description",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"template@odata.bind" , "https://graph.microsoft.com/v1.0/teamsTemplates('educationClass')"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams.PostAsync(requestBody);
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
displayName := "My Class Team"
requestBody.SetDisplayName(&displayName) 
description := "My Class Team’s Description"
requestBody.SetDescription(&description) 
additionalData := map[string]interface{}{
	"template@odata.bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('educationClass')", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
teams, err := graphClient.Teams().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Team team = new Team();
team.setDisplayName("My Class Team");
team.setDescription("My Class Team’s Description");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("template@odata.bind", "https://graph.microsoft.com/v1.0/teamsTemplates('educationClass')");
team.setAdditionalData(additionalData);
Team result = graphClient.teams().post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const team = {
  'template@odata.bind': 'https://graph.microsoft.com/v1.0/teamsTemplates(\'educationClass\')',
  displayName: 'My Class Team',
  description: 'My Class Team’s Description'
};

await client.api('/teams')
	.post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Team;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Team();
$requestBody->setDisplayName('My Class Team');
$requestBody->setDescription('My Class Team’s Description');
$additionalData = [
	'template@odata.bind' => 'https://graph.microsoft.com/v1.0/teamsTemplates(\'educationClass\')',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->teams()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	"template@odata.bind" = "https://graph.microsoft.com/v1.0/teamsTemplates('educationClass')"
	displayName = "My Class Team"
	description = "My Class Team’s Description"
}

New-MgTeam -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.team import Team
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Team(
	display_name = "My Class Team",
	description = "My Class Team’s Description",
	additional_data = {
			"template@odata_bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('educationClass')",
	}
)

result = await graph_client.teams.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Location: /teams('dbd8de4f-5d47-48da-87f1-594bed003375')/operations('3a6fdce1-c261-48bc-89de-1cfef658c0d5')
Content-Location: /teams('dbd8de4f-5d47-48da-87f1-594bed003375')
Content-Length: 0
```

### Example 7: Create a team with a non-standard base template type with extended properties

Base template types can be extended with additional properties, enabling you to build on an existing base template with additional team settings, channels, apps, or tabs.

To learn more about supported base template types and supported properties, see [Get started with Teams templates](https://learn.microsoft.com/en-us/MicrosoftTeams/get-started-with-teams-templates).

#### Request

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
POST https://graph.microsoft.com/v1.0/teams
Content-Type: application/json

{
   "template@odata.bind":"https://graph.microsoft.com/v1.0/teamsTemplates('educationClass')",
   "displayName":"My Class Team",
   "description":"My Class Team’s Description",
   "channels":[
      {
         "displayName":"Class Announcements 📢",
         "isFavoriteByDefault":true
      },
      {
         "displayName":"Homework 🏋️",
         "isFavoriteByDefault":true
      }
   ],
   "memberSettings":{
      "allowCreateUpdateChannels":false,
      "allowDeleteChannels":false,
      "allowAddRemoveApps":false,
      "allowCreateUpdateRemoveTabs":false,
      "allowCreateUpdateRemoveConnectors":false
   },
   "installedApps":[
      {
         "teamsApp@odata.bind":"https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')"
      },
      {
         "teamsApp@odata.bind":"https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')"
      }
   ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Team
{
	DisplayName = "My Class Team",
	Description = "My Class Team’s Description",
	Channels = new List<Channel>
	{
		new Channel
		{
			DisplayName = "Class Announcements 📢",
			IsFavoriteByDefault = true,
		},
		new Channel
		{
			DisplayName = "Homework 🏋️",
			IsFavoriteByDefault = true,
		},
	},
	MemberSettings = new TeamMemberSettings
	{
		AllowCreateUpdateChannels = false,
		AllowDeleteChannels = false,
		AllowAddRemoveApps = false,
		AllowCreateUpdateRemoveTabs = false,
		AllowCreateUpdateRemoveConnectors = false,
	},
	InstalledApps = new List<TeamsAppInstallation>
	{
		new TeamsAppInstallation
		{
			AdditionalData = new Dictionary<string, object>
			{
				{
					"teamsApp@odata.bind" , "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')"
				},
			},
		},
		new TeamsAppInstallation
		{
			AdditionalData = new Dictionary<string, object>
			{
				{
					"teamsApp@odata.bind" , "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')"
				},
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"template@odata.bind" , "https://graph.microsoft.com/v1.0/teamsTemplates('educationClass')"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams.PostAsync(requestBody);
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
displayName := "My Class Team"
requestBody.SetDisplayName(&displayName) 
description := "My Class Team’s Description"
requestBody.SetDescription(&description) 


channel := graphmodels.NewChannel()
displayName := "Class Announcements 📢"
channel.SetDisplayName(&displayName) 
isFavoriteByDefault := true
channel.SetIsFavoriteByDefault(&isFavoriteByDefault) 
channel1 := graphmodels.NewChannel()
displayName := "Homework 🏋️"
channel1.SetDisplayName(&displayName) 
isFavoriteByDefault := true
channel1.SetIsFavoriteByDefault(&isFavoriteByDefault) 

channels := []graphmodels.Channelable {
	channel,
	channel1,
}
requestBody.SetChannels(channels)
memberSettings := graphmodels.NewTeamMemberSettings()
allowCreateUpdateChannels := false
memberSettings.SetAllowCreateUpdateChannels(&allowCreateUpdateChannels) 
allowDeleteChannels := false
memberSettings.SetAllowDeleteChannels(&allowDeleteChannels) 
allowAddRemoveApps := false
memberSettings.SetAllowAddRemoveApps(&allowAddRemoveApps) 
allowCreateUpdateRemoveTabs := false
memberSettings.SetAllowCreateUpdateRemoveTabs(&allowCreateUpdateRemoveTabs) 
allowCreateUpdateRemoveConnectors := false
memberSettings.SetAllowCreateUpdateRemoveConnectors(&allowCreateUpdateRemoveConnectors) 
requestBody.SetMemberSettings(memberSettings)


teamsAppInstallation := graphmodels.NewTeamsAppInstallation()
additionalData := map[string]interface{}{
	"teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')", 
}
teamsAppInstallation.SetAdditionalData(additionalData)
teamsAppInstallation1 := graphmodels.NewTeamsAppInstallation()
additionalData := map[string]interface{}{
	"teamsApp@odata.bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')", 
}
teamsAppInstallation1.SetAdditionalData(additionalData)

installedApps := []graphmodels.TeamsAppInstallationable {
	teamsAppInstallation,
	teamsAppInstallation1,
}
requestBody.SetInstalledApps(installedApps)
additionalData := map[string]interface{}{
	"template@odata.bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('educationClass')", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
teams, err := graphClient.Teams().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Team team = new Team();
team.setDisplayName("My Class Team");
team.setDescription("My Class Team’s Description");
LinkedList<Channel> channels = new LinkedList<Channel>();
Channel channel = new Channel();
channel.setDisplayName("Class Announcements 📢");
channel.setIsFavoriteByDefault(true);
channels.add(channel);
Channel channel1 = new Channel();
channel1.setDisplayName("Homework 🏋️");
channel1.setIsFavoriteByDefault(true);
channels.add(channel1);
team.setChannels(channels);
TeamMemberSettings memberSettings = new TeamMemberSettings();
memberSettings.setAllowCreateUpdateChannels(false);
memberSettings.setAllowDeleteChannels(false);
memberSettings.setAllowAddRemoveApps(false);
memberSettings.setAllowCreateUpdateRemoveTabs(false);
memberSettings.setAllowCreateUpdateRemoveConnectors(false);
team.setMemberSettings(memberSettings);
LinkedList<TeamsAppInstallation> installedApps = new LinkedList<TeamsAppInstallation>();
TeamsAppInstallation teamsAppInstallation = new TeamsAppInstallation();
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("teamsApp@odata.bind", "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')");
teamsAppInstallation.setAdditionalData(additionalData);
installedApps.add(teamsAppInstallation);
TeamsAppInstallation teamsAppInstallation1 = new TeamsAppInstallation();
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("teamsApp@odata.bind", "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')");
teamsAppInstallation1.setAdditionalData(additionalData1);
installedApps.add(teamsAppInstallation1);
team.setInstalledApps(installedApps);
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
additionalData2.put("template@odata.bind", "https://graph.microsoft.com/v1.0/teamsTemplates('educationClass')");
team.setAdditionalData(additionalData2);
Team result = graphClient.teams().post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const team = {
   'template@odata.bind':'https://graph.microsoft.com/v1.0/teamsTemplates(\'educationClass\')',
   displayName: 'My Class Team',
   description: 'My Class Team’s Description',
   channels: [
      {
         displayName: 'Class Announcements 📢',
         isFavoriteByDefault: true
      },
      {
         displayName: 'Homework 🏋️',
         isFavoriteByDefault: true
      }
   ],
   memberSettings: {
      allowCreateUpdateChannels: false,
      allowDeleteChannels: false,
      allowAddRemoveApps: false,
      allowCreateUpdateRemoveTabs: false,
      allowCreateUpdateRemoveConnectors: false
   },
   installedApps: [
      {
         'teamsApp@odata.bind':'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'com.microsoft.teamspace.tab.vsts\')'
      },
      {
         'teamsApp@odata.bind':'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'1542629c-01b3-4a6d-8f76-1938b779e48d\')'
      }
   ]
};

await client.api('/teams')
	.post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Team;
use Microsoft\Graph\Generated\Models\Channel;
use Microsoft\Graph\Generated\Models\TeamMemberSettings;
use Microsoft\Graph\Generated\Models\TeamsAppInstallation;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Team();
$requestBody->setDisplayName('My Class Team');
$requestBody->setDescription('My Class Team’s Description');
$channelsChannel1 = new Channel();
$channelsChannel1->setDisplayName('Class Announcements 📢');
$channelsChannel1->setIsFavoriteByDefault(true);
$channelsArray []= $channelsChannel1;
$channelsChannel2 = new Channel();
$channelsChannel2->setDisplayName('Homework 🏋️');
$channelsChannel2->setIsFavoriteByDefault(true);
$channelsArray []= $channelsChannel2;
$requestBody->setChannels($channelsArray);

$memberSettings = new TeamMemberSettings();
$memberSettings->setAllowCreateUpdateChannels(false);
$memberSettings->setAllowDeleteChannels(false);
$memberSettings->setAllowAddRemoveApps(false);
$memberSettings->setAllowCreateUpdateRemoveTabs(false);
$memberSettings->setAllowCreateUpdateRemoveConnectors(false);
$requestBody->setMemberSettings($memberSettings);
$installedAppsTeamsAppInstallation1 = new TeamsAppInstallation();
$additionalData = [
'teamsApp@odata.bind' => 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'com.microsoft.teamspace.tab.vsts\')',
];
$installedAppsTeamsAppInstallation1->setAdditionalData($additionalData);
$installedAppsArray []= $installedAppsTeamsAppInstallation1;
$installedAppsTeamsAppInstallation2 = new TeamsAppInstallation();
$additionalData = [
'teamsApp@odata.bind' => 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps(\'1542629c-01b3-4a6d-8f76-1938b779e48d\')',
];
$installedAppsTeamsAppInstallation2->setAdditionalData($additionalData);
$installedAppsArray []= $installedAppsTeamsAppInstallation2;
$requestBody->setInstalledApps($installedAppsArray);

$additionalData = [
'template@odata.bind' => 'https://graph.microsoft.com/v1.0/teamsTemplates(\'educationClass\')',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->teams()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	"template@odata.bind" = "https://graph.microsoft.com/v1.0/teamsTemplates('educationClass')"
	displayName = "My Class Team"
	description = "My Class Team’s Description"
	channels = @(
		@{
			displayName = "Class Announcements 📢"
			isFavoriteByDefault = $true
		}
		@{
			displayName = "Homework 🏋️"
			isFavoriteByDefault = $true
		}
	)
	memberSettings = @{
		allowCreateUpdateChannels = $false
		allowDeleteChannels = $false
		allowAddRemoveApps = $false
		allowCreateUpdateRemoveTabs = $false
		allowCreateUpdateRemoveConnectors = $false
	}
	installedApps = @(
		@{
			"teamsApp@odata.bind" = "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')"
		}
		@{
			"teamsApp@odata.bind" = "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')"
		}
	)
}

New-MgTeam -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.team import Team
from msgraph.generated.models.channel import Channel
from msgraph.generated.models.team_member_settings import TeamMemberSettings
from msgraph.generated.models.teams_app_installation import TeamsAppInstallation
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Team(
	display_name = "My Class Team",
	description = "My Class Team’s Description",
	channels = [
		Channel(
			display_name = "Class Announcements 📢",
			is_favorite_by_default = True,
		),
		Channel(
			display_name = "Homework 🏋️",
			is_favorite_by_default = True,
		),
	],
	member_settings = TeamMemberSettings(
		allow_create_update_channels = False,
		allow_delete_channels = False,
		allow_add_remove_apps = False,
		allow_create_update_remove_tabs = False,
		allow_create_update_remove_connectors = False,
	),
	installed_apps = [
		TeamsAppInstallation(
			additional_data = {
					"teams_app@odata_bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('com.microsoft.teamspace.tab.vsts')",
			}
		),
		TeamsAppInstallation(
			additional_data = {
					"teams_app@odata_bind" : "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps('1542629c-01b3-4a6d-8f76-1938b779e48d')",
			}
		),
	],
	additional_data = {
			"template@odata_bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('educationClass')",
	}
)

result = await graph_client.teams.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Location: /teams('dbd8de4f-5d47-48da-87f1-594bed003375')/operations('3a6fdce1-c261-48bc-89de-1cfef658c0d5')
Content-Location: /teams('dbd8de4f-5d47-48da-87f1-594bed003375')
Content-Length: 0
```

### Example 8: Create a team in migration mode

#### Request

The following example shows how to create a team for imported messages.

> **Note:** In the future, Microsoft may require you or your customers to pay additional fees based on the amount of data imported.

> **Note:** Teams created in migration mode only supports the `standard` template.

```http
POST https://graph.microsoft.com/v1.0/teams
Content-Type: application/json

{
  "@microsoft.graph.teamCreationMode": "migration",
  "template@odata.bind": "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
  "displayName": "My Sample Team",
  "description": "My Sample Team’s Description",
  "createdDateTime": "2020-03-14T11:22:17.067Z"
}
```

#### Response

```http
HTTP/1.1 202 Accepted
Location: /teams('dbd8de4f-5d47-48da-87f1-594bed003375')/operations('3a6fdce1-c261-48bc-89de-1cfef658c0d5')
Content-Location: /teams('dbd8de4f-5d47-48da-87f1-594bed003375')
```

#### Error response

If the request is unsuccessful, this method returns a `400 Bad Request` response code.

```http
400 Bad Request
```

The following are common reasons for this response:

- **createdDateTime** is set in the future.
- **createdDateTime** is correctly specified but the **teamCreationMode** instance attribute is missing or set to an invalid value.

### Example 9: Application permissions using user principal name

Here's an example of a minimal request using application permissions. By omitting other properties, the client is implicitly taking defaults from the predefined template represented by `template`. When issuing a request with application permissions, a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) must be specified in the `members` collection.

#### Request

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```http
POST https://graph.microsoft.com/v1.0/teams
Content-Type: application/json

{
   "template@odata.bind":"https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
   "displayName":"My Sample Team",
   "description":"My Sample Team’s Description",
   "members":[
      {
         "@odata.type":"#microsoft.graph.aadUserConversationMember",
         "roles":[
            "owner"
         ],
         "user@odata.bind":"https://graph.microsoft.com/v1.0/users('jacob@contoso.com')"
      }
   ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Team
{
	DisplayName = "My Sample Team",
	Description = "My Sample Team’s Description",
	Members = new List<ConversationMember>
	{
		new AadUserConversationMember
		{
			OdataType = "#microsoft.graph.aadUserConversationMember",
			Roles = new List<string>
			{
				"owner",
			},
			AdditionalData = new Dictionary<string, object>
			{
				{
					"user@odata.bind" , "https://graph.microsoft.com/v1.0/users('jacob@contoso.com')"
				},
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"template@odata.bind" , "https://graph.microsoft.com/v1.0/teamsTemplates('standard')"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams.PostAsync(requestBody);
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
displayName := "My Sample Team"
requestBody.SetDisplayName(&displayName) 
description := "My Sample Team’s Description"
requestBody.SetDescription(&description) 


conversationMember := graphmodels.NewAadUserConversationMember()
roles := []string {
	"owner",
}
conversationMember.SetRoles(roles)
additionalData := map[string]interface{}{
	"user@odata.bind" : "https://graph.microsoft.com/v1.0/users('jacob@contoso.com')", 
}
conversationMember.SetAdditionalData(additionalData)

members := []graphmodels.ConversationMemberable {
	conversationMember,
}
requestBody.SetMembers(members)
additionalData := map[string]interface{}{
	"template@odata.bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('standard')", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
teams, err := graphClient.Teams().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Team team = new Team();
team.setDisplayName("My Sample Team");
team.setDescription("My Sample Team’s Description");
LinkedList<ConversationMember> members = new LinkedList<ConversationMember>();
AadUserConversationMember conversationMember = new AadUserConversationMember();
conversationMember.setOdataType("#microsoft.graph.aadUserConversationMember");
LinkedList<String> roles = new LinkedList<String>();
roles.add("owner");
conversationMember.setRoles(roles);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("user@odata.bind", "https://graph.microsoft.com/v1.0/users('jacob@contoso.com')");
conversationMember.setAdditionalData(additionalData);
members.add(conversationMember);
team.setMembers(members);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("template@odata.bind", "https://graph.microsoft.com/v1.0/teamsTemplates('standard')");
team.setAdditionalData(additionalData1);
Team result = graphClient.teams().post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const team = {
   'template@odata.bind':'https://graph.microsoft.com/v1.0/teamsTemplates(\'standard\')',
   displayName: 'My Sample Team',
   description: 'My Sample Team’s Description',
   members: [
      {
         '@odata.type':'#microsoft.graph.aadUserConversationMember',
         roles: [
            'owner'
         ],
         'user@odata.bind':'https://graph.microsoft.com/v1.0/users(\'jacob@contoso.com\')'
      }
   ]
};

await client.api('/teams')
	.post(team);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Team;
use Microsoft\Graph\Generated\Models\ConversationMember;
use Microsoft\Graph\Generated\Models\AadUserConversationMember;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Team();
$requestBody->setDisplayName('My Sample Team');
$requestBody->setDescription('My Sample Team’s Description');
$membersConversationMember1 = new AadUserConversationMember();
$membersConversationMember1->setOdataType('#microsoft.graph.aadUserConversationMember');
$membersConversationMember1->setRoles(['owner', 	]);
$additionalData = [
	'user@odata.bind' => 'https://graph.microsoft.com/v1.0/users(\'jacob@contoso.com\')',
];
$membersConversationMember1->setAdditionalData($additionalData);
$membersArray []= $membersConversationMember1;
$requestBody->setMembers($membersArray);

$additionalData = [
'template@odata.bind' => 'https://graph.microsoft.com/v1.0/teamsTemplates(\'standard\')',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->teams()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	"template@odata.bind" = "https://graph.microsoft.com/v1.0/teamsTemplates('standard')"
	displayName = "My Sample Team"
	description = "My Sample Team’s Description"
	members = @(
		@{
			"@odata.type" = "#microsoft.graph.aadUserConversationMember"
			roles = @(
			"owner"
		)
		"user@odata.bind" = "https://graph.microsoft.com/v1.0/users('jacob@contoso.com')"
	}
)
}

New-MgTeam -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.team import Team
from msgraph.generated.models.conversation_member import ConversationMember
from msgraph.generated.models.aad_user_conversation_member import AadUserConversationMember
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Team(
	display_name = "My Sample Team",
	description = "My Sample Team’s Description",
	members = [
		AadUserConversationMember(
			odata_type = "#microsoft.graph.aadUserConversationMember",
			roles = [
				"owner",
			],
			additional_data = {
					"user@odata_bind" : "https://graph.microsoft.com/v1.0/users('jacob@contoso.com')",
			}
		),
	],
	additional_data = {
			"template@odata_bind" : "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
	}
)

result = await graph_client.teams.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Location: /teams('dbd8de4f-5d47-48da-87f1-594bed003375')/operations('3a6fdce1-c261-48bc-89de-1cfef658c0d5')
Content-Location: /teams('dbd8de4f-5d47-48da-87f1-594bed003375')
Content-Length: 0
```

## Related content

- [Complete migration for a team](https://learn.microsoft.com/en-us/graph/api/team-completemigration?view=graph-rest-1.0)
- [Import third-party platform messages to Teams using Microsoft Graph](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/import-messages/import-external-messages-to-teams)
- [Create channel](https://learn.microsoft.com/en-us/graph/api/channel-post?view=graph-rest-1.0)
- [Available templates](https://learn.microsoft.com/en-us/MicrosoftTeams/get-started-with-teams-templates)
- [Getting started with Retail Teams templates](https://learn.microsoft.com/en-us/MicrosoftTeams/get-started-with-retail-teams-templates)
- [Getting started with Healthcare Teams templates](https://learn.microsoft.com/en-us/MicrosoftTeams/healthcare/healthcare-templates)
- [Creating a group with a team](https://learn.microsoft.com/en-us/graph/teams-create-group-and-team)
- [Microsoft Graph service-specific throttling limits](https://learn.microsoft.com/en-us/graph/throttling-limits#microsoft-teams-service-limits)
