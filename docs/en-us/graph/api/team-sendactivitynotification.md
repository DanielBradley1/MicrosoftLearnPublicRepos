<!-- Source: https://learn.microsoft.com/en-us/graph/api/team-sendactivitynotification?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# team: sendActivityNotification

Namespace: microsoft.graph

Send an activity feed notification in the scope of a team. For more information about sending notifications and the requirements for doing so, see [sending Teams activity notifications](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamsActivity.Send | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamsActivity.Send.Group | TeamsActivity.Send |

Note

The TeamsActivity.Send.Group permission uses [resource-specific consent](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

## HTTP request

```http
POST /teams/{teamId}/sendActivityNotification
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| activityType | String | The activity type must be declared in the [Teams app manifest](https://learn.microsoft.com/en-us/microsoftteams/platform/overview), except for the `systemDefault` [Reserved activity type](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications/#reserved-activity-types), which provides free-form text in the `Actor+Reason` line of the notification. |
| chainId | Int64 | Optional. The chain ID for the notification. Used to override a previous notification. Use the same `chainId` in subsequent requests to override the previous notification. |
| iconId | String | Optional. The unique icon ID that allows apps to send customized icons per activity type. Icon IDs must be present in the Teams app manifest schema. If the icon ID is specified in the manifest but missing from the API request body, the icon falls back to the default icon for the app. |
| previewText | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The preview text for the notification. Microsoft Teams shows the first 150 characters. |
| recipient | [teamworkNotificationRecipient](https://learn.microsoft.com/en-us/graph/api/resources/teamworknotificationrecipient?view=graph-rest-1.0) | The recipient of the notification. For more information, see [aadUserNotificationRecipient](https://learn.microsoft.com/en-us/graph/api/resources/aadusernotificationrecipient?view=graph-rest-1.0), [channelMembersNotificationRecipient](https://learn.microsoft.com/en-us/graph/api/resources/channelmembersnotificationrecipient?view=graph-rest-1.0), and [teamMembersNotificationRecipient](https://learn.microsoft.com/en-us/graph/api/resources/teammembersnotificationrecipient?view=graph-rest-1.0). |
| teamsAppId | String | Optional. The Teams app ID of the Teams app associated with the notification. Used to disambiguate installed apps when multiple apps with the same Microsoft Entra ID app ID are installed for the same recipient user. Avoid sharing Microsoft Entra ID app IDs between Teams apps. |
| templateParameters | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-1.0) collection | The values for the template variables defined in the activity feed entry corresponding to `activityType` in the [Teams app manifest](https://learn.microsoft.com/en-us/microsoftteams/platform/overview). |
| topic | [teamworkActivityTopic](https://learn.microsoft.com/en-us/graph/api/resources/teamworkactivitytopic?view=graph-rest-1.0) | The topic of the notification. Specifies the resource being talked about. |

The following resources are supported when setting the `source` value of the **topic** property to `entityUrl`:

- [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0)
- [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0)
- [chatMesage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)
- [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0)

> **Note:** The entity URL must be same or child resource of the team in the URL. Additionally, the [Teams app](https://learn.microsoft.com/en-us/microsoftteams/platform/overview) must be installed in the team.

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Example 1: Notify a user about pending finance approval requests

This example shows how you can send an activity feed notification for a team. This example notifies the team owner about pending finance approval requests.

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
POST https://graph.microsoft.com/v1.0/teams/{teamId}/sendActivityNotification
Content-Type: application/json

{
    "topic": {
        "source": "entityUrl",
        "value": "https://graph.microsoft.com/v1.0/teams/{teamId}"
    },
    "activityType": "pendingFinanceApprovalRequests",
    "previewText": {
        "content": "Internal spending team has a pending finance approval requests"
    },
    "recipient": {
        "@odata.type": "microsoft.graph.aadUserNotificationRecipient",
        "userId": "569363e2-4e49-4661-87f2-16f245c5d66a"
    },
    "templateParameters": [
        {
            "name": "pendingRequestCount",
            "value": "5"
        }
    ] 
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.SendActivityNotification;
using Microsoft.Graph.Models;

var requestBody = new SendActivityNotificationPostRequestBody
{
	Topic = new TeamworkActivityTopic
	{
		Source = TeamworkActivityTopicSource.EntityUrl,
		Value = "https://graph.microsoft.com/v1.0/teams/{teamId}",
	},
	ActivityType = "pendingFinanceApprovalRequests",
	PreviewText = new ItemBody
	{
		Content = "Internal spending team has a pending finance approval requests",
	},
	Recipient = new AadUserNotificationRecipient
	{
		OdataType = "microsoft.graph.aadUserNotificationRecipient",
		UserId = "569363e2-4e49-4661-87f2-16f245c5d66a",
	},
	TemplateParameters = new List<KeyValuePair>
	{
		new KeyValuePair
		{
			Name = "pendingRequestCount",
			Value = "5",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teams["{team-id}"].SendActivityNotification.PostAsync(requestBody);
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

requestBody := graphteams.NewSendActivityNotificationPostRequestBody()
topic := graphmodels.NewTeamworkActivityTopic()
source := graphmodels.ENTITYURL_TEAMWORKACTIVITYTOPICSOURCE 
topic.SetSource(&source) 
value := "https://graph.microsoft.com/v1.0/teams/{teamId}"
topic.SetValue(&value) 
requestBody.SetTopic(topic)
activityType := "pendingFinanceApprovalRequests"
requestBody.SetActivityType(&activityType) 
previewText := graphmodels.NewItemBody()
content := "Internal spending team has a pending finance approval requests"
previewText.SetContent(&content) 
requestBody.SetPreviewText(previewText)
recipient := graphmodels.NewAadUserNotificationRecipient()
userId := "569363e2-4e49-4661-87f2-16f245c5d66a"
recipient.SetUserId(&userId) 
requestBody.SetRecipient(recipient)


keyValuePair := graphmodels.NewKeyValuePair()
name := "pendingRequestCount"
keyValuePair.SetName(&name) 
value := "5"
keyValuePair.SetValue(&value) 

templateParameters := []graphmodels.KeyValuePairable {
	keyValuePair,
}
requestBody.SetTemplateParameters(templateParameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Teams().ByTeamId("team-id").SendActivityNotification().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody sendActivityNotificationPostRequestBody = new com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody();
TeamworkActivityTopic topic = new TeamworkActivityTopic();
topic.setSource(TeamworkActivityTopicSource.EntityUrl);
topic.setValue("https://graph.microsoft.com/v1.0/teams/{teamId}");
sendActivityNotificationPostRequestBody.setTopic(topic);
sendActivityNotificationPostRequestBody.setActivityType("pendingFinanceApprovalRequests");
ItemBody previewText = new ItemBody();
previewText.setContent("Internal spending team has a pending finance approval requests");
sendActivityNotificationPostRequestBody.setPreviewText(previewText);
AadUserNotificationRecipient recipient = new AadUserNotificationRecipient();
recipient.setOdataType("microsoft.graph.aadUserNotificationRecipient");
recipient.setUserId("569363e2-4e49-4661-87f2-16f245c5d66a");
sendActivityNotificationPostRequestBody.setRecipient(recipient);
LinkedList<KeyValuePair> templateParameters = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("pendingRequestCount");
keyValuePair.setValue("5");
templateParameters.add(keyValuePair);
sendActivityNotificationPostRequestBody.setTemplateParameters(templateParameters);
graphClient.teams().byTeamId("{team-id}").sendActivityNotification().post(sendActivityNotificationPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sendActivityNotification = {
    topic: {
        source: 'entityUrl',
        value: 'https://graph.microsoft.com/v1.0/teams/{teamId}'
    },
    activityType: 'pendingFinanceApprovalRequests',
    previewText: {
        content: 'Internal spending team has a pending finance approval requests'
    },
    recipient: {
        '@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
        userId: '569363e2-4e49-4661-87f2-16f245c5d66a'
    },
    templateParameters: [
        {
            name: 'pendingRequestCount',
            value: '5'
        }
    ] 
};

await client.api('/teams/{teamId}/sendActivityNotification')
	.post(sendActivityNotification);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\SendActivityNotification\SendActivityNotificationPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopic;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopicSource;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\AadUserNotificationRecipient;
use Microsoft\Graph\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SendActivityNotificationPostRequestBody();
$topic = new TeamworkActivityTopic();
$topic->setSource(new TeamworkActivityTopicSource('entityUrl'));
$topic->setValue('https://graph.microsoft.com/v1.0/teams/{teamId}');
$requestBody->setTopic($topic);
$requestBody->setActivityType('pendingFinanceApprovalRequests');
$previewText = new ItemBody();
$previewText->setContent('Internal spending team has a pending finance approval requests');
$requestBody->setPreviewText($previewText);
$recipient = new AadUserNotificationRecipient();
$recipient->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipient->setUserId('569363e2-4e49-4661-87f2-16f245c5d66a');
$requestBody->setRecipient($recipient);
$templateParametersKeyValuePair1 = new KeyValuePair();
$templateParametersKeyValuePair1->setName('pendingRequestCount');
$templateParametersKeyValuePair1->setValue('5');
$templateParametersArray []= $templateParametersKeyValuePair1;
$requestBody->setTemplateParameters($templateParametersArray);


$graphServiceClient->teams()->byTeamId('team-id')->sendActivityNotification()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	topic = @{
		source = "entityUrl"
		value = "https://graph.microsoft.com/v1.0/teams/{teamId}"
	}
	activityType = "pendingFinanceApprovalRequests"
	previewText = @{
		content = "Internal spending team has a pending finance approval requests"
	}
	recipient = @{
		"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
		userId = "569363e2-4e49-4661-87f2-16f245c5d66a"
	}
	templateParameters = @(
		@{
			name = "pendingRequestCount"
			value = "5"
		}
	)
}

Send-MgTeamActivityNotification -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.send_activity_notification.send_activity_notification_post_request_body import SendActivityNotificationPostRequestBody
from msgraph.generated.models.teamwork_activity_topic import TeamworkActivityTopic
from msgraph.generated.models.teamwork_activity_topic_source import TeamworkActivityTopicSource
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.aad_user_notification_recipient import AadUserNotificationRecipient
from msgraph.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SendActivityNotificationPostRequestBody(
	topic = TeamworkActivityTopic(
		source = TeamworkActivityTopicSource.EntityUrl,
		value = "https://graph.microsoft.com/v1.0/teams/{teamId}",
	),
	activity_type = "pendingFinanceApprovalRequests",
	preview_text = ItemBody(
		content = "Internal spending team has a pending finance approval requests",
	),
	recipient = AadUserNotificationRecipient(
		odata_type = "microsoft.graph.aadUserNotificationRecipient",
		user_id = "569363e2-4e49-4661-87f2-16f245c5d66a",
	),
	template_parameters = [
		KeyValuePair(
			name = "pendingRequestCount",
			value = "5",
		),
	],
)

await graph_client.teams.by_team_id('team-id').send_activity_notification.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 2: Notify a user about a channel tab

Similar to the previous example, this example uses `entityUrl` for the `topic`. However, this example links to a [tab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) in a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0). The tab hosts a page showing the user the status of their hotel reservation. Selecting the notification takes the user to the tab, where they can check their reservation.

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
POST https://graph.microsoft.com/v1.0/teams/{teamId}/sendActivityNotification
Content-Type: application/json

{
    "topic": {
        "source": "entityUrl",
        "value": "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}"
    },
    "activityType": "reservationUpdated",
    "previewText": {
        "content": "You have moved up the queue"
    },
    "recipient": {
        "@odata.type": "microsoft.graph.aadUserNotificationRecipient",
        "userId": "569363e2-4e49-4661-87f2-16f245c5d66a"
    },
    "templateParameters": [
        {
            "name": "reservationId",
            "value": "TREEE433"
        },
        {
            "name": "currentSlot",
            "value": "23"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.SendActivityNotification;
using Microsoft.Graph.Models;

var requestBody = new SendActivityNotificationPostRequestBody
{
	Topic = new TeamworkActivityTopic
	{
		Source = TeamworkActivityTopicSource.EntityUrl,
		Value = "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}",
	},
	ActivityType = "reservationUpdated",
	PreviewText = new ItemBody
	{
		Content = "You have moved up the queue",
	},
	Recipient = new AadUserNotificationRecipient
	{
		OdataType = "microsoft.graph.aadUserNotificationRecipient",
		UserId = "569363e2-4e49-4661-87f2-16f245c5d66a",
	},
	TemplateParameters = new List<KeyValuePair>
	{
		new KeyValuePair
		{
			Name = "reservationId",
			Value = "TREEE433",
		},
		new KeyValuePair
		{
			Name = "currentSlot",
			Value = "23",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teams["{team-id}"].SendActivityNotification.PostAsync(requestBody);
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

requestBody := graphteams.NewSendActivityNotificationPostRequestBody()
topic := graphmodels.NewTeamworkActivityTopic()
source := graphmodels.ENTITYURL_TEAMWORKACTIVITYTOPICSOURCE 
topic.SetSource(&source) 
value := "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}"
topic.SetValue(&value) 
requestBody.SetTopic(topic)
activityType := "reservationUpdated"
requestBody.SetActivityType(&activityType) 
previewText := graphmodels.NewItemBody()
content := "You have moved up the queue"
previewText.SetContent(&content) 
requestBody.SetPreviewText(previewText)
recipient := graphmodels.NewAadUserNotificationRecipient()
userId := "569363e2-4e49-4661-87f2-16f245c5d66a"
recipient.SetUserId(&userId) 
requestBody.SetRecipient(recipient)


keyValuePair := graphmodels.NewKeyValuePair()
name := "reservationId"
keyValuePair.SetName(&name) 
value := "TREEE433"
keyValuePair.SetValue(&value) 
keyValuePair1 := graphmodels.NewKeyValuePair()
name := "currentSlot"
keyValuePair1.SetName(&name) 
value := "23"
keyValuePair1.SetValue(&value) 

templateParameters := []graphmodels.KeyValuePairable {
	keyValuePair,
	keyValuePair1,
}
requestBody.SetTemplateParameters(templateParameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Teams().ByTeamId("team-id").SendActivityNotification().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody sendActivityNotificationPostRequestBody = new com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody();
TeamworkActivityTopic topic = new TeamworkActivityTopic();
topic.setSource(TeamworkActivityTopicSource.EntityUrl);
topic.setValue("https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}");
sendActivityNotificationPostRequestBody.setTopic(topic);
sendActivityNotificationPostRequestBody.setActivityType("reservationUpdated");
ItemBody previewText = new ItemBody();
previewText.setContent("You have moved up the queue");
sendActivityNotificationPostRequestBody.setPreviewText(previewText);
AadUserNotificationRecipient recipient = new AadUserNotificationRecipient();
recipient.setOdataType("microsoft.graph.aadUserNotificationRecipient");
recipient.setUserId("569363e2-4e49-4661-87f2-16f245c5d66a");
sendActivityNotificationPostRequestBody.setRecipient(recipient);
LinkedList<KeyValuePair> templateParameters = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("reservationId");
keyValuePair.setValue("TREEE433");
templateParameters.add(keyValuePair);
KeyValuePair keyValuePair1 = new KeyValuePair();
keyValuePair1.setName("currentSlot");
keyValuePair1.setValue("23");
templateParameters.add(keyValuePair1);
sendActivityNotificationPostRequestBody.setTemplateParameters(templateParameters);
graphClient.teams().byTeamId("{team-id}").sendActivityNotification().post(sendActivityNotificationPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sendActivityNotification = {
    topic: {
        source: 'entityUrl',
        value: 'https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}'
    },
    activityType: 'reservationUpdated',
    previewText: {
        content: 'You have moved up the queue'
    },
    recipient: {
        '@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
        userId: '569363e2-4e49-4661-87f2-16f245c5d66a'
    },
    templateParameters: [
        {
            name: 'reservationId',
            value: 'TREEE433'
        },
        {
            name: 'currentSlot',
            value: '23'
        }
    ]
};

await client.api('/teams/{teamId}/sendActivityNotification')
	.post(sendActivityNotification);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\SendActivityNotification\SendActivityNotificationPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopic;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopicSource;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\AadUserNotificationRecipient;
use Microsoft\Graph\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SendActivityNotificationPostRequestBody();
$topic = new TeamworkActivityTopic();
$topic->setSource(new TeamworkActivityTopicSource('entityUrl'));
$topic->setValue('https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}');
$requestBody->setTopic($topic);
$requestBody->setActivityType('reservationUpdated');
$previewText = new ItemBody();
$previewText->setContent('You have moved up the queue');
$requestBody->setPreviewText($previewText);
$recipient = new AadUserNotificationRecipient();
$recipient->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipient->setUserId('569363e2-4e49-4661-87f2-16f245c5d66a');
$requestBody->setRecipient($recipient);
$templateParametersKeyValuePair1 = new KeyValuePair();
$templateParametersKeyValuePair1->setName('reservationId');
$templateParametersKeyValuePair1->setValue('TREEE433');
$templateParametersArray []= $templateParametersKeyValuePair1;
$templateParametersKeyValuePair2 = new KeyValuePair();
$templateParametersKeyValuePair2->setName('currentSlot');
$templateParametersKeyValuePair2->setValue('23');
$templateParametersArray []= $templateParametersKeyValuePair2;
$requestBody->setTemplateParameters($templateParametersArray);


$graphServiceClient->teams()->byTeamId('team-id')->sendActivityNotification()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	topic = @{
		source = "entityUrl"
		value = "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}"
	}
	activityType = "reservationUpdated"
	previewText = @{
		content = "You have moved up the queue"
	}
	recipient = @{
		"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
		userId = "569363e2-4e49-4661-87f2-16f245c5d66a"
	}
	templateParameters = @(
		@{
			name = "reservationId"
			value = "TREEE433"
		}
		@{
			name = "currentSlot"
			value = "23"
		}
	)
}

Send-MgTeamActivityNotification -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.send_activity_notification.send_activity_notification_post_request_body import SendActivityNotificationPostRequestBody
from msgraph.generated.models.teamwork_activity_topic import TeamworkActivityTopic
from msgraph.generated.models.teamwork_activity_topic_source import TeamworkActivityTopicSource
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.aad_user_notification_recipient import AadUserNotificationRecipient
from msgraph.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SendActivityNotificationPostRequestBody(
	topic = TeamworkActivityTopic(
		source = TeamworkActivityTopicSource.EntityUrl,
		value = "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}",
	),
	activity_type = "reservationUpdated",
	preview_text = ItemBody(
		content = "You have moved up the queue",
	),
	recipient = AadUserNotificationRecipient(
		odata_type = "microsoft.graph.aadUserNotificationRecipient",
		user_id = "569363e2-4e49-4661-87f2-16f245c5d66a",
	),
	template_parameters = [
		KeyValuePair(
			name = "reservationId",
			value = "TREEE433",
		),
		KeyValuePair(
			name = "currentSlot",
			value = "23",
		),
	],
)

await graph_client.teams.by_team_id('team-id').send_activity_notification.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 3: Notify a user about a channel tab using user principal name

Similar to the previous example, this example uses `entityUrl` for the `topic`. However, this example links to a [tab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) in a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0). The tab hosts a page showing the user the status of their hotel reservation. Selecting the notification takes the user to the tab, where they can check their reservation.

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
POST https://graph.microsoft.com/v1.0/teams/{teamId}/sendActivityNotification
Content-Type: application/json

{
    "topic": {
        "source": "entityUrl",
        "value": "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}"
    },
    "activityType": "reservationUpdated",
    "previewText": {
        "content": "You have moved up the queue"
    },
    "recipient": {
        "@odata.type": "microsoft.graph.aadUserNotificationRecipient",
        "userId": "jacob@contoso.com"
    },
    "templateParameters": [
        {
            "name": "reservationId",
            "value": "TREEE433"
        },
        {
            "name": "currentSlot",
            "value": "23"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.SendActivityNotification;
using Microsoft.Graph.Models;

var requestBody = new SendActivityNotificationPostRequestBody
{
	Topic = new TeamworkActivityTopic
	{
		Source = TeamworkActivityTopicSource.EntityUrl,
		Value = "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}",
	},
	ActivityType = "reservationUpdated",
	PreviewText = new ItemBody
	{
		Content = "You have moved up the queue",
	},
	Recipient = new AadUserNotificationRecipient
	{
		OdataType = "microsoft.graph.aadUserNotificationRecipient",
		UserId = "jacob@contoso.com",
	},
	TemplateParameters = new List<KeyValuePair>
	{
		new KeyValuePair
		{
			Name = "reservationId",
			Value = "TREEE433",
		},
		new KeyValuePair
		{
			Name = "currentSlot",
			Value = "23",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teams["{team-id}"].SendActivityNotification.PostAsync(requestBody);
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

requestBody := graphteams.NewSendActivityNotificationPostRequestBody()
topic := graphmodels.NewTeamworkActivityTopic()
source := graphmodels.ENTITYURL_TEAMWORKACTIVITYTOPICSOURCE 
topic.SetSource(&source) 
value := "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}"
topic.SetValue(&value) 
requestBody.SetTopic(topic)
activityType := "reservationUpdated"
requestBody.SetActivityType(&activityType) 
previewText := graphmodels.NewItemBody()
content := "You have moved up the queue"
previewText.SetContent(&content) 
requestBody.SetPreviewText(previewText)
recipient := graphmodels.NewAadUserNotificationRecipient()
userId := "jacob@contoso.com"
recipient.SetUserId(&userId) 
requestBody.SetRecipient(recipient)


keyValuePair := graphmodels.NewKeyValuePair()
name := "reservationId"
keyValuePair.SetName(&name) 
value := "TREEE433"
keyValuePair.SetValue(&value) 
keyValuePair1 := graphmodels.NewKeyValuePair()
name := "currentSlot"
keyValuePair1.SetName(&name) 
value := "23"
keyValuePair1.SetValue(&value) 

templateParameters := []graphmodels.KeyValuePairable {
	keyValuePair,
	keyValuePair1,
}
requestBody.SetTemplateParameters(templateParameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Teams().ByTeamId("team-id").SendActivityNotification().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody sendActivityNotificationPostRequestBody = new com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody();
TeamworkActivityTopic topic = new TeamworkActivityTopic();
topic.setSource(TeamworkActivityTopicSource.EntityUrl);
topic.setValue("https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}");
sendActivityNotificationPostRequestBody.setTopic(topic);
sendActivityNotificationPostRequestBody.setActivityType("reservationUpdated");
ItemBody previewText = new ItemBody();
previewText.setContent("You have moved up the queue");
sendActivityNotificationPostRequestBody.setPreviewText(previewText);
AadUserNotificationRecipient recipient = new AadUserNotificationRecipient();
recipient.setOdataType("microsoft.graph.aadUserNotificationRecipient");
recipient.setUserId("jacob@contoso.com");
sendActivityNotificationPostRequestBody.setRecipient(recipient);
LinkedList<KeyValuePair> templateParameters = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("reservationId");
keyValuePair.setValue("TREEE433");
templateParameters.add(keyValuePair);
KeyValuePair keyValuePair1 = new KeyValuePair();
keyValuePair1.setName("currentSlot");
keyValuePair1.setValue("23");
templateParameters.add(keyValuePair1);
sendActivityNotificationPostRequestBody.setTemplateParameters(templateParameters);
graphClient.teams().byTeamId("{team-id}").sendActivityNotification().post(sendActivityNotificationPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sendActivityNotification = {
    topic: {
        source: 'entityUrl',
        value: 'https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}'
    },
    activityType: 'reservationUpdated',
    previewText: {
        content: 'You have moved up the queue'
    },
    recipient: {
        '@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
        userId: 'jacob@contoso.com'
    },
    templateParameters: [
        {
            name: 'reservationId',
            value: 'TREEE433'
        },
        {
            name: 'currentSlot',
            value: '23'
        }
    ]
};

await client.api('/teams/{teamId}/sendActivityNotification')
	.post(sendActivityNotification);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\SendActivityNotification\SendActivityNotificationPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopic;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopicSource;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\AadUserNotificationRecipient;
use Microsoft\Graph\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SendActivityNotificationPostRequestBody();
$topic = new TeamworkActivityTopic();
$topic->setSource(new TeamworkActivityTopicSource('entityUrl'));
$topic->setValue('https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}');
$requestBody->setTopic($topic);
$requestBody->setActivityType('reservationUpdated');
$previewText = new ItemBody();
$previewText->setContent('You have moved up the queue');
$requestBody->setPreviewText($previewText);
$recipient = new AadUserNotificationRecipient();
$recipient->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipient->setUserId('jacob@contoso.com');
$requestBody->setRecipient($recipient);
$templateParametersKeyValuePair1 = new KeyValuePair();
$templateParametersKeyValuePair1->setName('reservationId');
$templateParametersKeyValuePair1->setValue('TREEE433');
$templateParametersArray []= $templateParametersKeyValuePair1;
$templateParametersKeyValuePair2 = new KeyValuePair();
$templateParametersKeyValuePair2->setName('currentSlot');
$templateParametersKeyValuePair2->setValue('23');
$templateParametersArray []= $templateParametersKeyValuePair2;
$requestBody->setTemplateParameters($templateParametersArray);


$graphServiceClient->teams()->byTeamId('team-id')->sendActivityNotification()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	topic = @{
		source = "entityUrl"
		value = "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}"
	}
	activityType = "reservationUpdated"
	previewText = @{
		content = "You have moved up the queue"
	}
	recipient = @{
		"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
		userId = "jacob@contoso.com"
	}
	templateParameters = @(
		@{
			name = "reservationId"
			value = "TREEE433"
		}
		@{
			name = "currentSlot"
			value = "23"
		}
	)
}

Send-MgTeamActivityNotification -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.send_activity_notification.send_activity_notification_post_request_body import SendActivityNotificationPostRequestBody
from msgraph.generated.models.teamwork_activity_topic import TeamworkActivityTopic
from msgraph.generated.models.teamwork_activity_topic_source import TeamworkActivityTopicSource
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.aad_user_notification_recipient import AadUserNotificationRecipient
from msgraph.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SendActivityNotificationPostRequestBody(
	topic = TeamworkActivityTopic(
		source = TeamworkActivityTopicSource.EntityUrl,
		value = "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/tabs/{tabId}",
	),
	activity_type = "reservationUpdated",
	preview_text = ItemBody(
		content = "You have moved up the queue",
	),
	recipient = AadUserNotificationRecipient(
		odata_type = "microsoft.graph.aadUserNotificationRecipient",
		user_id = "jacob@contoso.com",
	),
	template_parameters = [
		KeyValuePair(
			name = "reservationId",
			value = "TREEE433",
		),
		KeyValuePair(
			name = "currentSlot",
			value = "23",
		),
	],
)

await graph_client.teams.by_team_id('team-id').send_activity_notification.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 4: Notify a user about an event using custom topic

As seen in the previous examples, you can link to different aspects of the team. However, if you want to link to an aspect that isn't part of the team or isn't represented by Microsoft Graph, or you want to customize the name, you can set the source of the `topic` to `text` and pass in a custom value for it. `webUrl` is required when setting `topic` source to `text`.

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
POST https://graph.microsoft.com/v1.0/teams/{teamId}/sendActivityNotification
Content-Type: application/json

{
    "topic": {
        "source": "text",
        "value": "Deployment Approvals Channel",
        "webUrl": "https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000"
    },
    "activityType": "deploymentApprovalRequired",
    "previewText": {
        "content": "New deployment requires your approval"
    },
    "recipient": {
        "@odata.type": "microsoft.graph.aadUserNotificationRecipient",
        "userId": "569363e2-4e49-4661-87f2-16f245c5d66a"
    },
    "templateParameters": [
        {
            "name": "deploymentId",
            "value": "6788662"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.SendActivityNotification;
using Microsoft.Graph.Models;

var requestBody = new SendActivityNotificationPostRequestBody
{
	Topic = new TeamworkActivityTopic
	{
		Source = TeamworkActivityTopicSource.Text,
		Value = "Deployment Approvals Channel",
		WebUrl = "https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000",
	},
	ActivityType = "deploymentApprovalRequired",
	PreviewText = new ItemBody
	{
		Content = "New deployment requires your approval",
	},
	Recipient = new AadUserNotificationRecipient
	{
		OdataType = "microsoft.graph.aadUserNotificationRecipient",
		UserId = "569363e2-4e49-4661-87f2-16f245c5d66a",
	},
	TemplateParameters = new List<KeyValuePair>
	{
		new KeyValuePair
		{
			Name = "deploymentId",
			Value = "6788662",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teams["{team-id}"].SendActivityNotification.PostAsync(requestBody);
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

requestBody := graphteams.NewSendActivityNotificationPostRequestBody()
topic := graphmodels.NewTeamworkActivityTopic()
source := graphmodels.TEXT_TEAMWORKACTIVITYTOPICSOURCE 
topic.SetSource(&source) 
value := "Deployment Approvals Channel"
topic.SetValue(&value) 
webUrl := "https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000"
topic.SetWebUrl(&webUrl) 
requestBody.SetTopic(topic)
activityType := "deploymentApprovalRequired"
requestBody.SetActivityType(&activityType) 
previewText := graphmodels.NewItemBody()
content := "New deployment requires your approval"
previewText.SetContent(&content) 
requestBody.SetPreviewText(previewText)
recipient := graphmodels.NewAadUserNotificationRecipient()
userId := "569363e2-4e49-4661-87f2-16f245c5d66a"
recipient.SetUserId(&userId) 
requestBody.SetRecipient(recipient)


keyValuePair := graphmodels.NewKeyValuePair()
name := "deploymentId"
keyValuePair.SetName(&name) 
value := "6788662"
keyValuePair.SetValue(&value) 

templateParameters := []graphmodels.KeyValuePairable {
	keyValuePair,
}
requestBody.SetTemplateParameters(templateParameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Teams().ByTeamId("team-id").SendActivityNotification().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody sendActivityNotificationPostRequestBody = new com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody();
TeamworkActivityTopic topic = new TeamworkActivityTopic();
topic.setSource(TeamworkActivityTopicSource.Text);
topic.setValue("Deployment Approvals Channel");
topic.setWebUrl("https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000");
sendActivityNotificationPostRequestBody.setTopic(topic);
sendActivityNotificationPostRequestBody.setActivityType("deploymentApprovalRequired");
ItemBody previewText = new ItemBody();
previewText.setContent("New deployment requires your approval");
sendActivityNotificationPostRequestBody.setPreviewText(previewText);
AadUserNotificationRecipient recipient = new AadUserNotificationRecipient();
recipient.setOdataType("microsoft.graph.aadUserNotificationRecipient");
recipient.setUserId("569363e2-4e49-4661-87f2-16f245c5d66a");
sendActivityNotificationPostRequestBody.setRecipient(recipient);
LinkedList<KeyValuePair> templateParameters = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("deploymentId");
keyValuePair.setValue("6788662");
templateParameters.add(keyValuePair);
sendActivityNotificationPostRequestBody.setTemplateParameters(templateParameters);
graphClient.teams().byTeamId("{team-id}").sendActivityNotification().post(sendActivityNotificationPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sendActivityNotification = {
    topic: {
        source: 'text',
        value: 'Deployment Approvals Channel',
        webUrl: 'https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000'
    },
    activityType: 'deploymentApprovalRequired',
    previewText: {
        content: 'New deployment requires your approval'
    },
    recipient: {
        '@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
        userId: '569363e2-4e49-4661-87f2-16f245c5d66a'
    },
    templateParameters: [
        {
            name: 'deploymentId',
            value: '6788662'
        }
    ]
};

await client.api('/teams/{teamId}/sendActivityNotification')
	.post(sendActivityNotification);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\SendActivityNotification\SendActivityNotificationPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopic;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopicSource;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\AadUserNotificationRecipient;
use Microsoft\Graph\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SendActivityNotificationPostRequestBody();
$topic = new TeamworkActivityTopic();
$topic->setSource(new TeamworkActivityTopicSource('text'));
$topic->setValue('Deployment Approvals Channel');
$topic->setWebUrl('https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000');
$requestBody->setTopic($topic);
$requestBody->setActivityType('deploymentApprovalRequired');
$previewText = new ItemBody();
$previewText->setContent('New deployment requires your approval');
$requestBody->setPreviewText($previewText);
$recipient = new AadUserNotificationRecipient();
$recipient->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipient->setUserId('569363e2-4e49-4661-87f2-16f245c5d66a');
$requestBody->setRecipient($recipient);
$templateParametersKeyValuePair1 = new KeyValuePair();
$templateParametersKeyValuePair1->setName('deploymentId');
$templateParametersKeyValuePair1->setValue('6788662');
$templateParametersArray []= $templateParametersKeyValuePair1;
$requestBody->setTemplateParameters($templateParametersArray);


$graphServiceClient->teams()->byTeamId('team-id')->sendActivityNotification()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	topic = @{
		source = "text"
		value = "Deployment Approvals Channel"
		webUrl = "https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000"
	}
	activityType = "deploymentApprovalRequired"
	previewText = @{
		content = "New deployment requires your approval"
	}
	recipient = @{
		"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
		userId = "569363e2-4e49-4661-87f2-16f245c5d66a"
	}
	templateParameters = @(
		@{
			name = "deploymentId"
			value = "6788662"
		}
	)
}

Send-MgTeamActivityNotification -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.send_activity_notification.send_activity_notification_post_request_body import SendActivityNotificationPostRequestBody
from msgraph.generated.models.teamwork_activity_topic import TeamworkActivityTopic
from msgraph.generated.models.teamwork_activity_topic_source import TeamworkActivityTopicSource
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.aad_user_notification_recipient import AadUserNotificationRecipient
from msgraph.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SendActivityNotificationPostRequestBody(
	topic = TeamworkActivityTopic(
		source = TeamworkActivityTopicSource.Text,
		value = "Deployment Approvals Channel",
		web_url = "https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000",
	),
	activity_type = "deploymentApprovalRequired",
	preview_text = ItemBody(
		content = "New deployment requires your approval",
	),
	recipient = AadUserNotificationRecipient(
		odata_type = "microsoft.graph.aadUserNotificationRecipient",
		user_id = "569363e2-4e49-4661-87f2-16f245c5d66a",
	),
	template_parameters = [
		KeyValuePair(
			name = "deploymentId",
			value = "6788662",
		),
	],
)

await graph_client.teams.by_team_id('team-id').send_activity_notification.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 5: Notify the team members about pending finance approval requests

The following example shows how you can send an activity feed notification to all team members. This example is similar to previous examples. However, in this case, the **recipient** is a [teamMembersNotificationRecipient](https://learn.microsoft.com/en-us/graph/api/resources/teammembersnotificationrecipient?view=graph-rest-1.0). The **teamId** specified in the **recipient** must match the **teamId** specified in the request URL.

> **Note:** The ability to send notifications to all team members is limited to teams with 10,000 members or less. If the team exceeds 10,000 members, none of the team members will receive a notification.

#### Request

The following example shows the request.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7/sendActivityNotification
Content-Type: application/json

{
    "topic": {
        "source": "entityUrl",
        "value": "https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7"
    },
    "activityType": "pendingFinanceApprovalRequests",
    "previewText": {
        "content": "Internal spending team has a pending finance approval requests"
    },
    "recipient": {
        "@odata.type": "microsoft.graph.teamMembersNotificationRecipient",
        "teamId": "e8bece96-d393-4b9b-b8da-69cedef1a7e7"
    },
    "templateParameters": [
        {
            "name": "pendingRequestCount",
            "value": "5"
        }
    ] 
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.SendActivityNotification;
using Microsoft.Graph.Models;

var requestBody = new SendActivityNotificationPostRequestBody
{
	Topic = new TeamworkActivityTopic
	{
		Source = TeamworkActivityTopicSource.EntityUrl,
		Value = "https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7",
	},
	ActivityType = "pendingFinanceApprovalRequests",
	PreviewText = new ItemBody
	{
		Content = "Internal spending team has a pending finance approval requests",
	},
	Recipient = new TeamMembersNotificationRecipient
	{
		OdataType = "microsoft.graph.teamMembersNotificationRecipient",
		TeamId = "e8bece96-d393-4b9b-b8da-69cedef1a7e7",
	},
	TemplateParameters = new List<KeyValuePair>
	{
		new KeyValuePair
		{
			Name = "pendingRequestCount",
			Value = "5",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teams["{team-id}"].SendActivityNotification.PostAsync(requestBody);
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

requestBody := graphteams.NewSendActivityNotificationPostRequestBody()
topic := graphmodels.NewTeamworkActivityTopic()
source := graphmodels.ENTITYURL_TEAMWORKACTIVITYTOPICSOURCE 
topic.SetSource(&source) 
value := "https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7"
topic.SetValue(&value) 
requestBody.SetTopic(topic)
activityType := "pendingFinanceApprovalRequests"
requestBody.SetActivityType(&activityType) 
previewText := graphmodels.NewItemBody()
content := "Internal spending team has a pending finance approval requests"
previewText.SetContent(&content) 
requestBody.SetPreviewText(previewText)
recipient := graphmodels.NewTeamMembersNotificationRecipient()
teamId := "e8bece96-d393-4b9b-b8da-69cedef1a7e7"
recipient.SetTeamId(&teamId) 
requestBody.SetRecipient(recipient)


keyValuePair := graphmodels.NewKeyValuePair()
name := "pendingRequestCount"
keyValuePair.SetName(&name) 
value := "5"
keyValuePair.SetValue(&value) 

templateParameters := []graphmodels.KeyValuePairable {
	keyValuePair,
}
requestBody.SetTemplateParameters(templateParameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Teams().ByTeamId("team-id").SendActivityNotification().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody sendActivityNotificationPostRequestBody = new com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody();
TeamworkActivityTopic topic = new TeamworkActivityTopic();
topic.setSource(TeamworkActivityTopicSource.EntityUrl);
topic.setValue("https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7");
sendActivityNotificationPostRequestBody.setTopic(topic);
sendActivityNotificationPostRequestBody.setActivityType("pendingFinanceApprovalRequests");
ItemBody previewText = new ItemBody();
previewText.setContent("Internal spending team has a pending finance approval requests");
sendActivityNotificationPostRequestBody.setPreviewText(previewText);
TeamMembersNotificationRecipient recipient = new TeamMembersNotificationRecipient();
recipient.setOdataType("microsoft.graph.teamMembersNotificationRecipient");
recipient.setTeamId("e8bece96-d393-4b9b-b8da-69cedef1a7e7");
sendActivityNotificationPostRequestBody.setRecipient(recipient);
LinkedList<KeyValuePair> templateParameters = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("pendingRequestCount");
keyValuePair.setValue("5");
templateParameters.add(keyValuePair);
sendActivityNotificationPostRequestBody.setTemplateParameters(templateParameters);
graphClient.teams().byTeamId("{team-id}").sendActivityNotification().post(sendActivityNotificationPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sendActivityNotification = {
    topic: {
        source: 'entityUrl',
        value: 'https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7'
    },
    activityType: 'pendingFinanceApprovalRequests',
    previewText: {
        content: 'Internal spending team has a pending finance approval requests'
    },
    recipient: {
        '@odata.type': 'microsoft.graph.teamMembersNotificationRecipient',
        teamId: 'e8bece96-d393-4b9b-b8da-69cedef1a7e7'
    },
    templateParameters: [
        {
            name: 'pendingRequestCount',
            value: '5'
        }
    ] 
};

await client.api('/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7/sendActivityNotification')
	.post(sendActivityNotification);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\SendActivityNotification\SendActivityNotificationPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopic;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopicSource;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\TeamMembersNotificationRecipient;
use Microsoft\Graph\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SendActivityNotificationPostRequestBody();
$topic = new TeamworkActivityTopic();
$topic->setSource(new TeamworkActivityTopicSource('entityUrl'));
$topic->setValue('https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7');
$requestBody->setTopic($topic);
$requestBody->setActivityType('pendingFinanceApprovalRequests');
$previewText = new ItemBody();
$previewText->setContent('Internal spending team has a pending finance approval requests');
$requestBody->setPreviewText($previewText);
$recipient = new TeamMembersNotificationRecipient();
$recipient->setOdataType('microsoft.graph.teamMembersNotificationRecipient');
$recipient->setTeamId('e8bece96-d393-4b9b-b8da-69cedef1a7e7');
$requestBody->setRecipient($recipient);
$templateParametersKeyValuePair1 = new KeyValuePair();
$templateParametersKeyValuePair1->setName('pendingRequestCount');
$templateParametersKeyValuePair1->setValue('5');
$templateParametersArray []= $templateParametersKeyValuePair1;
$requestBody->setTemplateParameters($templateParametersArray);


$graphServiceClient->teams()->byTeamId('team-id')->sendActivityNotification()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	topic = @{
		source = "entityUrl"
		value = "https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7"
	}
	activityType = "pendingFinanceApprovalRequests"
	previewText = @{
		content = "Internal spending team has a pending finance approval requests"
	}
	recipient = @{
		"@odata.type" = "microsoft.graph.teamMembersNotificationRecipient"
		teamId = "e8bece96-d393-4b9b-b8da-69cedef1a7e7"
	}
	templateParameters = @(
		@{
			name = "pendingRequestCount"
			value = "5"
		}
	)
}

Send-MgTeamActivityNotification -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.send_activity_notification.send_activity_notification_post_request_body import SendActivityNotificationPostRequestBody
from msgraph.generated.models.teamwork_activity_topic import TeamworkActivityTopic
from msgraph.generated.models.teamwork_activity_topic_source import TeamworkActivityTopicSource
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.team_members_notification_recipient import TeamMembersNotificationRecipient
from msgraph.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SendActivityNotificationPostRequestBody(
	topic = TeamworkActivityTopic(
		source = TeamworkActivityTopicSource.EntityUrl,
		value = "https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7",
	),
	activity_type = "pendingFinanceApprovalRequests",
	preview_text = ItemBody(
		content = "Internal spending team has a pending finance approval requests",
	),
	recipient = TeamMembersNotificationRecipient(
		odata_type = "microsoft.graph.teamMembersNotificationRecipient",
		team_id = "e8bece96-d393-4b9b-b8da-69cedef1a7e7",
	),
	template_parameters = [
		KeyValuePair(
			name = "pendingRequestCount",
			value = "5",
		),
	],
)

await graph_client.teams.by_team_id('team-id').send_activity_notification.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 6: Notify the channel members about pending finance approval requests

The following example shows how you can send an activity feed notification to all channel members. This example is similar to the previous example. However, in this case, the **recipient** is a [channelMembersNotificationRecipient](https://learn.microsoft.com/en-us/graph/api/resources/channelmembersnotificationrecipient?view=graph-rest-1.0). The **teamId** specified in the **recipient** must match the **teamId** specified in the request URL.

#### Request

The following example shows the request.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7/sendActivityNotification
Content-Type: application/json

{
    "topic": {
        "source": "entityUrl",
        "value": "https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7"
    },
    "activityType": "pendingFinanceApprovalRequests",
    "previewText": {
        "content": "Internal spending team has a pending finance approval requests"
    },
    "recipient": {
        "@odata.type": "microsoft.graph.channelMembersNotificationRecipient",
        "teamId": "e8bece96-d393-4b9b-b8da-69cedef1a7e7",
        "channelId": "19:3d61a2309f094f4a9310b20f1db37520@thread.tacv2"
    },
    "templateParameters": [
        {
            "name": "pendingRequestCount",
            "value": "5"
        }
    ] 
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.SendActivityNotification;
using Microsoft.Graph.Models;

var requestBody = new SendActivityNotificationPostRequestBody
{
	Topic = new TeamworkActivityTopic
	{
		Source = TeamworkActivityTopicSource.EntityUrl,
		Value = "https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7",
	},
	ActivityType = "pendingFinanceApprovalRequests",
	PreviewText = new ItemBody
	{
		Content = "Internal spending team has a pending finance approval requests",
	},
	Recipient = new ChannelMembersNotificationRecipient
	{
		OdataType = "microsoft.graph.channelMembersNotificationRecipient",
		TeamId = "e8bece96-d393-4b9b-b8da-69cedef1a7e7",
		ChannelId = "19:3d61a2309f094f4a9310b20f1db37520@thread.tacv2",
	},
	TemplateParameters = new List<KeyValuePair>
	{
		new KeyValuePair
		{
			Name = "pendingRequestCount",
			Value = "5",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teams["{team-id}"].SendActivityNotification.PostAsync(requestBody);
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

requestBody := graphteams.NewSendActivityNotificationPostRequestBody()
topic := graphmodels.NewTeamworkActivityTopic()
source := graphmodels.ENTITYURL_TEAMWORKACTIVITYTOPICSOURCE 
topic.SetSource(&source) 
value := "https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7"
topic.SetValue(&value) 
requestBody.SetTopic(topic)
activityType := "pendingFinanceApprovalRequests"
requestBody.SetActivityType(&activityType) 
previewText := graphmodels.NewItemBody()
content := "Internal spending team has a pending finance approval requests"
previewText.SetContent(&content) 
requestBody.SetPreviewText(previewText)
recipient := graphmodels.NewChannelMembersNotificationRecipient()
teamId := "e8bece96-d393-4b9b-b8da-69cedef1a7e7"
recipient.SetTeamId(&teamId) 
channelId := "19:3d61a2309f094f4a9310b20f1db37520@thread.tacv2"
recipient.SetChannelId(&channelId) 
requestBody.SetRecipient(recipient)


keyValuePair := graphmodels.NewKeyValuePair()
name := "pendingRequestCount"
keyValuePair.SetName(&name) 
value := "5"
keyValuePair.SetValue(&value) 

templateParameters := []graphmodels.KeyValuePairable {
	keyValuePair,
}
requestBody.SetTemplateParameters(templateParameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Teams().ByTeamId("team-id").SendActivityNotification().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody sendActivityNotificationPostRequestBody = new com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody();
TeamworkActivityTopic topic = new TeamworkActivityTopic();
topic.setSource(TeamworkActivityTopicSource.EntityUrl);
topic.setValue("https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7");
sendActivityNotificationPostRequestBody.setTopic(topic);
sendActivityNotificationPostRequestBody.setActivityType("pendingFinanceApprovalRequests");
ItemBody previewText = new ItemBody();
previewText.setContent("Internal spending team has a pending finance approval requests");
sendActivityNotificationPostRequestBody.setPreviewText(previewText);
ChannelMembersNotificationRecipient recipient = new ChannelMembersNotificationRecipient();
recipient.setOdataType("microsoft.graph.channelMembersNotificationRecipient");
recipient.setTeamId("e8bece96-d393-4b9b-b8da-69cedef1a7e7");
recipient.setChannelId("19:3d61a2309f094f4a9310b20f1db37520@thread.tacv2");
sendActivityNotificationPostRequestBody.setRecipient(recipient);
LinkedList<KeyValuePair> templateParameters = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("pendingRequestCount");
keyValuePair.setValue("5");
templateParameters.add(keyValuePair);
sendActivityNotificationPostRequestBody.setTemplateParameters(templateParameters);
graphClient.teams().byTeamId("{team-id}").sendActivityNotification().post(sendActivityNotificationPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sendActivityNotification = {
    topic: {
        source: 'entityUrl',
        value: 'https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7'
    },
    activityType: 'pendingFinanceApprovalRequests',
    previewText: {
        content: 'Internal spending team has a pending finance approval requests'
    },
    recipient: {
        '@odata.type': 'microsoft.graph.channelMembersNotificationRecipient',
        teamId: 'e8bece96-d393-4b9b-b8da-69cedef1a7e7',
        channelId: '19:3d61a2309f094f4a9310b20f1db37520@thread.tacv2'
    },
    templateParameters: [
        {
            name: 'pendingRequestCount',
            value: '5'
        }
    ] 
};

await client.api('/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7/sendActivityNotification')
	.post(sendActivityNotification);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\SendActivityNotification\SendActivityNotificationPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopic;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopicSource;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\ChannelMembersNotificationRecipient;
use Microsoft\Graph\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SendActivityNotificationPostRequestBody();
$topic = new TeamworkActivityTopic();
$topic->setSource(new TeamworkActivityTopicSource('entityUrl'));
$topic->setValue('https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7');
$requestBody->setTopic($topic);
$requestBody->setActivityType('pendingFinanceApprovalRequests');
$previewText = new ItemBody();
$previewText->setContent('Internal spending team has a pending finance approval requests');
$requestBody->setPreviewText($previewText);
$recipient = new ChannelMembersNotificationRecipient();
$recipient->setOdataType('microsoft.graph.channelMembersNotificationRecipient');
$recipient->setTeamId('e8bece96-d393-4b9b-b8da-69cedef1a7e7');
$recipient->setChannelId('19:3d61a2309f094f4a9310b20f1db37520@thread.tacv2');
$requestBody->setRecipient($recipient);
$templateParametersKeyValuePair1 = new KeyValuePair();
$templateParametersKeyValuePair1->setName('pendingRequestCount');
$templateParametersKeyValuePair1->setValue('5');
$templateParametersArray []= $templateParametersKeyValuePair1;
$requestBody->setTemplateParameters($templateParametersArray);


$graphServiceClient->teams()->byTeamId('team-id')->sendActivityNotification()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	topic = @{
		source = "entityUrl"
		value = "https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7"
	}
	activityType = "pendingFinanceApprovalRequests"
	previewText = @{
		content = "Internal spending team has a pending finance approval requests"
	}
	recipient = @{
		"@odata.type" = "microsoft.graph.channelMembersNotificationRecipient"
		teamId = "e8bece96-d393-4b9b-b8da-69cedef1a7e7"
		channelId = "19:3d61a2309f094f4a9310b20f1db37520@thread.tacv2"
	}
	templateParameters = @(
		@{
			name = "pendingRequestCount"
			value = "5"
		}
	)
}

Send-MgTeamActivityNotification -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.send_activity_notification.send_activity_notification_post_request_body import SendActivityNotificationPostRequestBody
from msgraph.generated.models.teamwork_activity_topic import TeamworkActivityTopic
from msgraph.generated.models.teamwork_activity_topic_source import TeamworkActivityTopicSource
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.channel_members_notification_recipient import ChannelMembersNotificationRecipient
from msgraph.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SendActivityNotificationPostRequestBody(
	topic = TeamworkActivityTopic(
		source = TeamworkActivityTopicSource.EntityUrl,
		value = "https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7",
	),
	activity_type = "pendingFinanceApprovalRequests",
	preview_text = ItemBody(
		content = "Internal spending team has a pending finance approval requests",
	),
	recipient = ChannelMembersNotificationRecipient(
		odata_type = "microsoft.graph.channelMembersNotificationRecipient",
		team_id = "e8bece96-d393-4b9b-b8da-69cedef1a7e7",
		channel_id = "19:3d61a2309f094f4a9310b20f1db37520@thread.tacv2",
	),
	template_parameters = [
		KeyValuePair(
			name = "pendingRequestCount",
			value = "5",
		),
	],
)

await graph_client.teams.by_team_id('team-id').send_activity_notification.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 7: Notify about pending finance approval requests in channel message reply location

Similar to the previous example, this example uses `entityUrl` for the `topic`. However, this example links to a [channel message reply](https://learn.microsoft.com/en-us/graph/api/chatmessage-get?view=graph-rest-1.0#example-3-get-reply-to-a-message-in-a-channel). The channel message reply shows the status of the user's hotel reservation. Selecting the notification takes the user to the reply message in the channel, where they can check their reservation status.

#### Request

The following example shows the request.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
POST https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7/sendActivityNotification
Content-Type: application/json

{
    "topic": {
        "source": "entityUrl",
        "value": "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}"
    },
    "activityType": "reservationStatusUpdated",
    "previewText": {
        "content": "You have moved up the queue"
    },
    "recipient": {
        "@odata.type": "microsoft.graph.aadUserNotificationRecipient",
        "userId": "jacob@contoso.com"
    },
    "templateParameters": [
        {
            "name": "reservationId",
            "value": "TREEE433"
        },
        {
            "name": "currentSlot",
            "value": "23"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.SendActivityNotification;
using Microsoft.Graph.Models;

var requestBody = new SendActivityNotificationPostRequestBody
{
	Topic = new TeamworkActivityTopic
	{
		Source = TeamworkActivityTopicSource.EntityUrl,
		Value = "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}",
	},
	ActivityType = "reservationStatusUpdated",
	PreviewText = new ItemBody
	{
		Content = "You have moved up the queue",
	},
	Recipient = new AadUserNotificationRecipient
	{
		OdataType = "microsoft.graph.aadUserNotificationRecipient",
		UserId = "jacob@contoso.com",
	},
	TemplateParameters = new List<KeyValuePair>
	{
		new KeyValuePair
		{
			Name = "reservationId",
			Value = "TREEE433",
		},
		new KeyValuePair
		{
			Name = "currentSlot",
			Value = "23",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teams["{team-id}"].SendActivityNotification.PostAsync(requestBody);
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

requestBody := graphteams.NewSendActivityNotificationPostRequestBody()
topic := graphmodels.NewTeamworkActivityTopic()
source := graphmodels.ENTITYURL_TEAMWORKACTIVITYTOPICSOURCE 
topic.SetSource(&source) 
value := "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}"
topic.SetValue(&value) 
requestBody.SetTopic(topic)
activityType := "reservationStatusUpdated"
requestBody.SetActivityType(&activityType) 
previewText := graphmodels.NewItemBody()
content := "You have moved up the queue"
previewText.SetContent(&content) 
requestBody.SetPreviewText(previewText)
recipient := graphmodels.NewAadUserNotificationRecipient()
userId := "jacob@contoso.com"
recipient.SetUserId(&userId) 
requestBody.SetRecipient(recipient)


keyValuePair := graphmodels.NewKeyValuePair()
name := "reservationId"
keyValuePair.SetName(&name) 
value := "TREEE433"
keyValuePair.SetValue(&value) 
keyValuePair1 := graphmodels.NewKeyValuePair()
name := "currentSlot"
keyValuePair1.SetName(&name) 
value := "23"
keyValuePair1.SetValue(&value) 

templateParameters := []graphmodels.KeyValuePairable {
	keyValuePair,
	keyValuePair1,
}
requestBody.SetTemplateParameters(templateParameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Teams().ByTeamId("team-id").SendActivityNotification().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody sendActivityNotificationPostRequestBody = new com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody();
TeamworkActivityTopic topic = new TeamworkActivityTopic();
topic.setSource(TeamworkActivityTopicSource.EntityUrl);
topic.setValue("https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}");
sendActivityNotificationPostRequestBody.setTopic(topic);
sendActivityNotificationPostRequestBody.setActivityType("reservationStatusUpdated");
ItemBody previewText = new ItemBody();
previewText.setContent("You have moved up the queue");
sendActivityNotificationPostRequestBody.setPreviewText(previewText);
AadUserNotificationRecipient recipient = new AadUserNotificationRecipient();
recipient.setOdataType("microsoft.graph.aadUserNotificationRecipient");
recipient.setUserId("jacob@contoso.com");
sendActivityNotificationPostRequestBody.setRecipient(recipient);
LinkedList<KeyValuePair> templateParameters = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("reservationId");
keyValuePair.setValue("TREEE433");
templateParameters.add(keyValuePair);
KeyValuePair keyValuePair1 = new KeyValuePair();
keyValuePair1.setName("currentSlot");
keyValuePair1.setValue("23");
templateParameters.add(keyValuePair1);
sendActivityNotificationPostRequestBody.setTemplateParameters(templateParameters);
graphClient.teams().byTeamId("{team-id}").sendActivityNotification().post(sendActivityNotificationPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sendActivityNotification = {
    topic: {
        source: 'entityUrl',
        value: 'https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}'
    },
    activityType: 'reservationStatusUpdated',
    previewText: {
        content: 'You have moved up the queue'
    },
    recipient: {
        '@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
        userId: 'jacob@contoso.com'
    },
    templateParameters: [
        {
            name: 'reservationId',
            value: 'TREEE433'
        },
        {
            name: 'currentSlot',
            value: '23'
        }
    ]
};

await client.api('/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7/sendActivityNotification')
	.post(sendActivityNotification);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\SendActivityNotification\SendActivityNotificationPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopic;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopicSource;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\AadUserNotificationRecipient;
use Microsoft\Graph\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SendActivityNotificationPostRequestBody();
$topic = new TeamworkActivityTopic();
$topic->setSource(new TeamworkActivityTopicSource('entityUrl'));
$topic->setValue('https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}');
$requestBody->setTopic($topic);
$requestBody->setActivityType('reservationStatusUpdated');
$previewText = new ItemBody();
$previewText->setContent('You have moved up the queue');
$requestBody->setPreviewText($previewText);
$recipient = new AadUserNotificationRecipient();
$recipient->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipient->setUserId('jacob@contoso.com');
$requestBody->setRecipient($recipient);
$templateParametersKeyValuePair1 = new KeyValuePair();
$templateParametersKeyValuePair1->setName('reservationId');
$templateParametersKeyValuePair1->setValue('TREEE433');
$templateParametersArray []= $templateParametersKeyValuePair1;
$templateParametersKeyValuePair2 = new KeyValuePair();
$templateParametersKeyValuePair2->setName('currentSlot');
$templateParametersKeyValuePair2->setValue('23');
$templateParametersArray []= $templateParametersKeyValuePair2;
$requestBody->setTemplateParameters($templateParametersArray);


$graphServiceClient->teams()->byTeamId('team-id')->sendActivityNotification()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	topic = @{
		source = "entityUrl"
		value = "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}"
	}
	activityType = "reservationStatusUpdated"
	previewText = @{
		content = "You have moved up the queue"
	}
	recipient = @{
		"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
		userId = "jacob@contoso.com"
	}
	templateParameters = @(
		@{
			name = "reservationId"
			value = "TREEE433"
		}
		@{
			name = "currentSlot"
			value = "23"
		}
	)
}

Send-MgTeamActivityNotification -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.send_activity_notification.send_activity_notification_post_request_body import SendActivityNotificationPostRequestBody
from msgraph.generated.models.teamwork_activity_topic import TeamworkActivityTopic
from msgraph.generated.models.teamwork_activity_topic_source import TeamworkActivityTopicSource
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.aad_user_notification_recipient import AadUserNotificationRecipient
from msgraph.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SendActivityNotificationPostRequestBody(
	topic = TeamworkActivityTopic(
		source = TeamworkActivityTopicSource.EntityUrl,
		value = "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}",
	),
	activity_type = "reservationStatusUpdated",
	preview_text = ItemBody(
		content = "You have moved up the queue",
	),
	recipient = AadUserNotificationRecipient(
		odata_type = "microsoft.graph.aadUserNotificationRecipient",
		user_id = "jacob@contoso.com",
	),
	template_parameters = [
		KeyValuePair(
			name = "reservationId",
			value = "TREEE433",
		),
		KeyValuePair(
			name = "currentSlot",
			value = "23",
		),
	],
)

await graph_client.teams.by_team_id('team-id').send_activity_notification.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 8: Notify a user in a team about an event using a custom icon

If you want to notify a user in a team with a customized icon instead of the default app icon, you can set the optional **iconId** property in the request body.

> **Note:** The `activityType` in the manifest must contain the list of allowed icon IDs in order to use this parameter. The request validation fails if the app manifest is missing the customized list of icons. For more information, see [Public developer preview app manifest](https://learn.microsoft.com/en-us/microsoftteams/platform/resources/schema/manifest-schema-dev-preview).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```msgraph
POST https://graph.microsoft.com/v1.0/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7/sendActivityNotification
Content-Type: application/json

{
  "topic": {
    "source": "entityUrl",
    "value": "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}"
  },
  "activityType": "announcementPosted",
  "previewText": {
    "content": "new announcemnet posted"
  },
  "iconId": "announcementCreated",
  "recipient": {
    "@odata.type": "microsoft.graph.aadUserNotificationRecipient",
    "userId": "jacob@contoso.com"
  },
  "templateParameters": [
    {
      "name": "reservationId",
      "value": "TREEE433"
    },
    {
      "name": "currentSlot",
      "value": "23"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teams.Item.SendActivityNotification;
using Microsoft.Graph.Models;

var requestBody = new SendActivityNotificationPostRequestBody
{
	Topic = new TeamworkActivityTopic
	{
		Source = TeamworkActivityTopicSource.EntityUrl,
		Value = "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}",
	},
	ActivityType = "announcementPosted",
	PreviewText = new ItemBody
	{
		Content = "new announcemnet posted",
	},
	IconId = "announcementCreated",
	Recipient = new AadUserNotificationRecipient
	{
		OdataType = "microsoft.graph.aadUserNotificationRecipient",
		UserId = "jacob@contoso.com",
	},
	TemplateParameters = new List<KeyValuePair>
	{
		new KeyValuePair
		{
			Name = "reservationId",
			Value = "TREEE433",
		},
		new KeyValuePair
		{
			Name = "currentSlot",
			Value = "23",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teams["{team-id}"].SendActivityNotification.PostAsync(requestBody);
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

requestBody := graphteams.NewSendActivityNotificationPostRequestBody()
topic := graphmodels.NewTeamworkActivityTopic()
source := graphmodels.ENTITYURL_TEAMWORKACTIVITYTOPICSOURCE 
topic.SetSource(&source) 
value := "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}"
topic.SetValue(&value) 
requestBody.SetTopic(topic)
activityType := "announcementPosted"
requestBody.SetActivityType(&activityType) 
previewText := graphmodels.NewItemBody()
content := "new announcemnet posted"
previewText.SetContent(&content) 
requestBody.SetPreviewText(previewText)
iconId := "announcementCreated"
requestBody.SetIconId(&iconId) 
recipient := graphmodels.NewAadUserNotificationRecipient()
userId := "jacob@contoso.com"
recipient.SetUserId(&userId) 
requestBody.SetRecipient(recipient)


keyValuePair := graphmodels.NewKeyValuePair()
name := "reservationId"
keyValuePair.SetName(&name) 
value := "TREEE433"
keyValuePair.SetValue(&value) 
keyValuePair1 := graphmodels.NewKeyValuePair()
name := "currentSlot"
keyValuePair1.SetName(&name) 
value := "23"
keyValuePair1.SetValue(&value) 

templateParameters := []graphmodels.KeyValuePairable {
	keyValuePair,
	keyValuePair1,
}
requestBody.SetTemplateParameters(templateParameters)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Teams().ByTeamId("team-id").SendActivityNotification().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody sendActivityNotificationPostRequestBody = new com.microsoft.graph.teams.item.sendactivitynotification.SendActivityNotificationPostRequestBody();
TeamworkActivityTopic topic = new TeamworkActivityTopic();
topic.setSource(TeamworkActivityTopicSource.EntityUrl);
topic.setValue("https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}");
sendActivityNotificationPostRequestBody.setTopic(topic);
sendActivityNotificationPostRequestBody.setActivityType("announcementPosted");
ItemBody previewText = new ItemBody();
previewText.setContent("new announcemnet posted");
sendActivityNotificationPostRequestBody.setPreviewText(previewText);
sendActivityNotificationPostRequestBody.setIconId("announcementCreated");
AadUserNotificationRecipient recipient = new AadUserNotificationRecipient();
recipient.setOdataType("microsoft.graph.aadUserNotificationRecipient");
recipient.setUserId("jacob@contoso.com");
sendActivityNotificationPostRequestBody.setRecipient(recipient);
LinkedList<KeyValuePair> templateParameters = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("reservationId");
keyValuePair.setValue("TREEE433");
templateParameters.add(keyValuePair);
KeyValuePair keyValuePair1 = new KeyValuePair();
keyValuePair1.setName("currentSlot");
keyValuePair1.setValue("23");
templateParameters.add(keyValuePair1);
sendActivityNotificationPostRequestBody.setTemplateParameters(templateParameters);
graphClient.teams().byTeamId("{team-id}").sendActivityNotification().post(sendActivityNotificationPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sendActivityNotification = {
  topic: {
    source: 'entityUrl',
    value: 'https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}'
  },
  activityType: 'announcementPosted',
  previewText: {
    content: 'new announcemnet posted'
  },
  iconId: 'announcementCreated',
  recipient: {
    '@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
    userId: 'jacob@contoso.com'
  },
  templateParameters: [
    {
      name: 'reservationId',
      value: 'TREEE433'
    },
    {
      name: 'currentSlot',
      value: '23'
    }
  ]
};

await client.api('/teams/e8bece96-d393-4b9b-b8da-69cedef1a7e7/sendActivityNotification')
	.post(sendActivityNotification);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\SendActivityNotification\SendActivityNotificationPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopic;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopicSource;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\AadUserNotificationRecipient;
use Microsoft\Graph\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SendActivityNotificationPostRequestBody();
$topic = new TeamworkActivityTopic();
$topic->setSource(new TeamworkActivityTopicSource('entityUrl'));
$topic->setValue('https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}');
$requestBody->setTopic($topic);
$requestBody->setActivityType('announcementPosted');
$previewText = new ItemBody();
$previewText->setContent('new announcemnet posted');
$requestBody->setPreviewText($previewText);
$requestBody->setIconId('announcementCreated');
$recipient = new AadUserNotificationRecipient();
$recipient->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipient->setUserId('jacob@contoso.com');
$requestBody->setRecipient($recipient);
$templateParametersKeyValuePair1 = new KeyValuePair();
$templateParametersKeyValuePair1->setName('reservationId');
$templateParametersKeyValuePair1->setValue('TREEE433');
$templateParametersArray []= $templateParametersKeyValuePair1;
$templateParametersKeyValuePair2 = new KeyValuePair();
$templateParametersKeyValuePair2->setName('currentSlot');
$templateParametersKeyValuePair2->setValue('23');
$templateParametersArray []= $templateParametersKeyValuePair2;
$requestBody->setTemplateParameters($templateParametersArray);


$graphServiceClient->teams()->byTeamId('team-id')->sendActivityNotification()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	topic = @{
		source = "entityUrl"
		value = "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}"
	}
	activityType = "announcementPosted"
	previewText = @{
		content = "new announcemnet posted"
	}
	iconId = "announcementCreated"
	recipient = @{
		"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
		userId = "jacob@contoso.com"
	}
	templateParameters = @(
		@{
			name = "reservationId"
			value = "TREEE433"
		}
		@{
			name = "currentSlot"
			value = "23"
		}
	)
}

Send-MgTeamActivityNotification -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.send_activity_notification.send_activity_notification_post_request_body import SendActivityNotificationPostRequestBody
from msgraph.generated.models.teamwork_activity_topic import TeamworkActivityTopic
from msgraph.generated.models.teamwork_activity_topic_source import TeamworkActivityTopicSource
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.aad_user_notification_recipient import AadUserNotificationRecipient
from msgraph.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SendActivityNotificationPostRequestBody(
	topic = TeamworkActivityTopic(
		source = TeamworkActivityTopicSource.EntityUrl,
		value = "https://graph.microsoft.com/v1.0/teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/{replyId}",
	),
	activity_type = "announcementPosted",
	preview_text = ItemBody(
		content = "new announcemnet posted",
	),
	icon_id = "announcementCreated",
	recipient = AadUserNotificationRecipient(
		odata_type = "microsoft.graph.aadUserNotificationRecipient",
		user_id = "jacob@contoso.com",
	),
	template_parameters = [
		KeyValuePair(
			name = "reservationId",
			value = "TREEE433",
		),
		KeyValuePair(
			name = "currentSlot",
			value = "23",
		),
	],
)

await graph_client.teams.by_team_id('team-id').send_activity_notification.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

## Related content

- [Activity feed notification C# sample](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/graph-activity-feed/csharp)
- [Activity feed notification Node.js sample](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/graph-activity-feed/nodejs)
- [Microsoft Graph service-specific throttling limits](https://learn.microsoft.com/en-us/graph/throttling-limits#microsoft-teams-service-limits)
