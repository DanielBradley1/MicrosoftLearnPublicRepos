<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamwork-sendactivitynotificationtorecipients?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# teamwork: sendActivityNotificationToRecipients

Namespace: microsoft.graph

Send activity feed notifications to multiple users, in bulk.

For more information, see [sending Teams activity notifications](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications).

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
| Application | TeamsActivity.Send.User | TeamsActivity.Send |

> **Note:** The `TeamsActivity.Send.User` permission uses [resource-specific consent](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent). RSC permissions pertain to the individual recipients in the payload.

## HTTP request

```http
POST /teamwork/sendActivityNotificationToRecipients
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

> **Note**: The token provided must be at least 45 minutes from expiry. The API call will return a `412 Precondition Failed` response if the token expires within 45 minutes.

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| activityType | String | The activity type must be declared in the [Teams app manifest](https://learn.microsoft.com/en-us/microsoftteams/platform/overview), except for the `systemDefault` [Reserved activity type](https://learn.microsoft.com/en-us/graph/teams-send-activityfeednotifications/#reserved-activity-types), which provides free-form text in the `Actor+Reason` line of the notification. |
| chainId | Int64 | Optional. The chain ID of the notification. Used to override a previous notification. Use the same `chainId` in subsequent requests to override the previous notification. |
| iconId | String | Optional. The unique icon ID that allows apps to send customized icons per activity type. Icon IDs must be present in the Teams app manifest schema. If the icon ID is specified in the manifest but missing from the API request body, the icon falls back to the default icon for the app. |
| previewText | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The preview text for the notification. Microsoft Teams only shows the first 150 characters. |
| recipients | [teamworkNotificationRecipient](https://learn.microsoft.com/en-us/graph/api/resources/teamworknotificationrecipient?view=graph-rest-1.0) collection | Recipients of the notification. Only recipients of type [aadUserNotificationRecipient](https://learn.microsoft.com/en-us/graph/api/resources/aadusernotificationrecipient?view=graph-rest-1.0) are supported. There's an upper limit of 100 recipients in a single request. |
| teamsAppId | String | Optional. The Teams app ID of the Teams app associated with the notification. Used to disambiguate installed apps when multiple apps with the same Microsoft Entra ID app ID are installed for the same recipient user. Avoid sharing Microsoft Entra ID app IDs between Teams apps. |
| templateParameters | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-1.0) collection | The values for the template variables defined in the activity feed entry corresponding to `activityType` in the [Teams app manifest](https://learn.microsoft.com/en-us/microsoftteams/platform/overview). |
| topic | [teamworkActivityTopic](https://learn.microsoft.com/en-us/graph/api/resources/teamworkactivitytopic?view=graph-rest-1.0) | The topic of the notification. Specifies the resource being talked about. |

The following resource is supported when setting the `source` value of the **topic** property to `entityUrl`:

- [teamsCatalogApp](https://learn.microsoft.com/en-us/graph/api/resources/teamscatalogapp?view=graph-rest-1.0)

## Response

If successful, this action returns a `202 Accepted` response code.

## Examples

### Example 1: Notify multiple users about pending finance approval requests

The following example shows how to send an activity feed notification to multiple users in bulk. This example notifies multiple stakeholders about pending finance approval requests.

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
POST https://graph.microsoft.com/v1.0/teamwork/sendActivityNotificationToRecipients
Content-Type: application/json

{
    "topic": {
        "source": "entityUrl",
        "value": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
    },
    "activityType": "pendingFinanceApprovalRequests",
    "previewText": {
        "content": "Internal spending team has a pending finance approval requests"
    },
    "recipients": [
    	{
        	"@odata.type": "microsoft.graph.aadUserNotificationRecipient",
        	"userId": "569363e2-4e49-4661-87f2-16f245c5d66a"
    	},
    	{
        	"@odata.type": "microsoft.graph.aadUserNotificationRecipient",
        	"userId": "ab88234e-0874-477c-9638-d144296ed04f"
    	},
    	{
        	"@odata.type": "microsoft.graph.aadUserNotificationRecipient",
        	"userId": "01c64f53-69aa-42c7-9b7f-9f75195d6bfc"
    	}
    ],
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
using Microsoft.Graph.Teamwork.SendActivityNotificationToRecipients;
using Microsoft.Graph.Models;

var requestBody = new SendActivityNotificationToRecipientsPostRequestBody
{
	Topic = new TeamworkActivityTopic
	{
		Source = TeamworkActivityTopicSource.EntityUrl,
		Value = "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}",
	},
	ActivityType = "pendingFinanceApprovalRequests",
	PreviewText = new ItemBody
	{
		Content = "Internal spending team has a pending finance approval requests",
	},
	Recipients = new List<TeamworkNotificationRecipient>
	{
		new AadUserNotificationRecipient
		{
			OdataType = "microsoft.graph.aadUserNotificationRecipient",
			UserId = "569363e2-4e49-4661-87f2-16f245c5d66a",
		},
		new AadUserNotificationRecipient
		{
			OdataType = "microsoft.graph.aadUserNotificationRecipient",
			UserId = "ab88234e-0874-477c-9638-d144296ed04f",
		},
		new AadUserNotificationRecipient
		{
			OdataType = "microsoft.graph.aadUserNotificationRecipient",
			UserId = "01c64f53-69aa-42c7-9b7f-9f75195d6bfc",
		},
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
await graphClient.Teamwork.SendActivityNotificationToRecipients.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphteamwork "github.com/microsoftgraph/msgraph-sdk-go/teamwork"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphteamwork.NewSendActivityNotificationToRecipientsPostRequestBody()
topic := graphmodels.NewTeamworkActivityTopic()
source := graphmodels.ENTITYURL_TEAMWORKACTIVITYTOPICSOURCE 
topic.SetSource(&source) 
value := "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
topic.SetValue(&value) 
requestBody.SetTopic(topic)
activityType := "pendingFinanceApprovalRequests"
requestBody.SetActivityType(&activityType) 
previewText := graphmodels.NewItemBody()
content := "Internal spending team has a pending finance approval requests"
previewText.SetContent(&content) 
requestBody.SetPreviewText(previewText)


teamworkNotificationRecipient := graphmodels.NewAadUserNotificationRecipient()
userId := "569363e2-4e49-4661-87f2-16f245c5d66a"
teamworkNotificationRecipient.SetUserId(&userId) 
teamworkNotificationRecipient1 := graphmodels.NewAadUserNotificationRecipient()
userId := "ab88234e-0874-477c-9638-d144296ed04f"
teamworkNotificationRecipient1.SetUserId(&userId) 
teamworkNotificationRecipient2 := graphmodels.NewAadUserNotificationRecipient()
userId := "01c64f53-69aa-42c7-9b7f-9f75195d6bfc"
teamworkNotificationRecipient2.SetUserId(&userId) 

recipients := []graphmodels.TeamworkNotificationRecipientable {
	teamworkNotificationRecipient,
	teamworkNotificationRecipient1,
	teamworkNotificationRecipient2,
}
requestBody.SetRecipients(recipients)


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
graphClient.Teamwork().SendActivityNotificationToRecipients().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teamwork.sendactivitynotificationtorecipients.SendActivityNotificationToRecipientsPostRequestBody sendActivityNotificationToRecipientsPostRequestBody = new com.microsoft.graph.teamwork.sendactivitynotificationtorecipients.SendActivityNotificationToRecipientsPostRequestBody();
TeamworkActivityTopic topic = new TeamworkActivityTopic();
topic.setSource(TeamworkActivityTopicSource.EntityUrl);
topic.setValue("https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}");
sendActivityNotificationToRecipientsPostRequestBody.setTopic(topic);
sendActivityNotificationToRecipientsPostRequestBody.setActivityType("pendingFinanceApprovalRequests");
ItemBody previewText = new ItemBody();
previewText.setContent("Internal spending team has a pending finance approval requests");
sendActivityNotificationToRecipientsPostRequestBody.setPreviewText(previewText);
LinkedList<TeamworkNotificationRecipient> recipients = new LinkedList<TeamworkNotificationRecipient>();
AadUserNotificationRecipient teamworkNotificationRecipient = new AadUserNotificationRecipient();
teamworkNotificationRecipient.setOdataType("microsoft.graph.aadUserNotificationRecipient");
teamworkNotificationRecipient.setUserId("569363e2-4e49-4661-87f2-16f245c5d66a");
recipients.add(teamworkNotificationRecipient);
AadUserNotificationRecipient teamworkNotificationRecipient1 = new AadUserNotificationRecipient();
teamworkNotificationRecipient1.setOdataType("microsoft.graph.aadUserNotificationRecipient");
teamworkNotificationRecipient1.setUserId("ab88234e-0874-477c-9638-d144296ed04f");
recipients.add(teamworkNotificationRecipient1);
AadUserNotificationRecipient teamworkNotificationRecipient2 = new AadUserNotificationRecipient();
teamworkNotificationRecipient2.setOdataType("microsoft.graph.aadUserNotificationRecipient");
teamworkNotificationRecipient2.setUserId("01c64f53-69aa-42c7-9b7f-9f75195d6bfc");
recipients.add(teamworkNotificationRecipient2);
sendActivityNotificationToRecipientsPostRequestBody.setRecipients(recipients);
LinkedList<KeyValuePair> templateParameters = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("pendingRequestCount");
keyValuePair.setValue("5");
templateParameters.add(keyValuePair);
sendActivityNotificationToRecipientsPostRequestBody.setTemplateParameters(templateParameters);
graphClient.teamwork().sendActivityNotificationToRecipients().post(sendActivityNotificationToRecipientsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sendActivityNotificationToRecipients = {
    topic: {
        source: 'entityUrl',
        value: 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}'
    },
    activityType: 'pendingFinanceApprovalRequests',
    previewText: {
        content: 'Internal spending team has a pending finance approval requests'
    },
    recipients: [
    	{
        	'@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
        	userId: '569363e2-4e49-4661-87f2-16f245c5d66a'
    	},
    	{
        	'@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
        	userId: 'ab88234e-0874-477c-9638-d144296ed04f'
    	},
    	{
        	'@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
        	userId: '01c64f53-69aa-42c7-9b7f-9f75195d6bfc'
    	}
    ],
    templateParameters: [
        {
            name: 'pendingRequestCount',
            value: '5'
        }
    ] 
};

await client.api('/teamwork/sendActivityNotificationToRecipients')
	.post(sendActivityNotificationToRecipients);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teamwork\SendActivityNotificationToRecipients\SendActivityNotificationToRecipientsPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopic;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopicSource;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\TeamworkNotificationRecipient;
use Microsoft\Graph\Generated\Models\AadUserNotificationRecipient;
use Microsoft\Graph\Generated\Models\KeyValuePair;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SendActivityNotificationToRecipientsPostRequestBody();
$topic = new TeamworkActivityTopic();
$topic->setSource(new TeamworkActivityTopicSource('entityUrl'));
$topic->setValue('https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}');
$requestBody->setTopic($topic);
$requestBody->setActivityType('pendingFinanceApprovalRequests');
$previewText = new ItemBody();
$previewText->setContent('Internal spending team has a pending finance approval requests');
$requestBody->setPreviewText($previewText);
$recipientsTeamworkNotificationRecipient1 = new AadUserNotificationRecipient();
$recipientsTeamworkNotificationRecipient1->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipientsTeamworkNotificationRecipient1->setUserId('569363e2-4e49-4661-87f2-16f245c5d66a');
$recipientsArray []= $recipientsTeamworkNotificationRecipient1;
$recipientsTeamworkNotificationRecipient2 = new AadUserNotificationRecipient();
$recipientsTeamworkNotificationRecipient2->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipientsTeamworkNotificationRecipient2->setUserId('ab88234e-0874-477c-9638-d144296ed04f');
$recipientsArray []= $recipientsTeamworkNotificationRecipient2;
$recipientsTeamworkNotificationRecipient3 = new AadUserNotificationRecipient();
$recipientsTeamworkNotificationRecipient3->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipientsTeamworkNotificationRecipient3->setUserId('01c64f53-69aa-42c7-9b7f-9f75195d6bfc');
$recipientsArray []= $recipientsTeamworkNotificationRecipient3;
$requestBody->setRecipients($recipientsArray);

$templateParametersKeyValuePair1 = new KeyValuePair();
$templateParametersKeyValuePair1->setName('pendingRequestCount');
$templateParametersKeyValuePair1->setValue('5');
$templateParametersArray []= $templateParametersKeyValuePair1;
$requestBody->setTemplateParameters($templateParametersArray);


$graphServiceClient->teamwork()->sendActivityNotificationToRecipients()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	topic = @{
		source = "entityUrl"
		value = "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}"
	}
	activityType = "pendingFinanceApprovalRequests"
	previewText = @{
		content = "Internal spending team has a pending finance approval requests"
	}
	recipients = @(
		@{
			"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
			userId = "569363e2-4e49-4661-87f2-16f245c5d66a"
		}
		@{
			"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
			userId = "ab88234e-0874-477c-9638-d144296ed04f"
		}
		@{
			"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
			userId = "01c64f53-69aa-42c7-9b7f-9f75195d6bfc"
		}
	)
	templateParameters = @(
		@{
			name = "pendingRequestCount"
			value = "5"
		}
	)
}

Send-MgTeamworkActivityNotificationToRecipient -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teamwork.send_activity_notification_to_recipients.send_activity_notification_to_recipients_post_request_body import SendActivityNotificationToRecipientsPostRequestBody
from msgraph.generated.models.teamwork_activity_topic import TeamworkActivityTopic
from msgraph.generated.models.teamwork_activity_topic_source import TeamworkActivityTopicSource
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.teamwork_notification_recipient import TeamworkNotificationRecipient
from msgraph.generated.models.aad_user_notification_recipient import AadUserNotificationRecipient
from msgraph.generated.models.key_value_pair import KeyValuePair
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SendActivityNotificationToRecipientsPostRequestBody(
	topic = TeamworkActivityTopic(
		source = TeamworkActivityTopicSource.EntityUrl,
		value = "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/{teamsAppId}",
	),
	activity_type = "pendingFinanceApprovalRequests",
	preview_text = ItemBody(
		content = "Internal spending team has a pending finance approval requests",
	),
	recipients = [
		AadUserNotificationRecipient(
			odata_type = "microsoft.graph.aadUserNotificationRecipient",
			user_id = "569363e2-4e49-4661-87f2-16f245c5d66a",
		),
		AadUserNotificationRecipient(
			odata_type = "microsoft.graph.aadUserNotificationRecipient",
			user_id = "ab88234e-0874-477c-9638-d144296ed04f",
		),
		AadUserNotificationRecipient(
			odata_type = "microsoft.graph.aadUserNotificationRecipient",
			user_id = "01c64f53-69aa-42c7-9b7f-9f75195d6bfc",
		),
	],
	template_parameters = [
		KeyValuePair(
			name = "pendingRequestCount",
			value = "5",
		),
	],
)

await graph_client.teamwork.send_activity_notification_to_recipients.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

```http
HTTP/1.1 202 Accepted
```

### Example 2: Notify multiple users about an event using a custom topic

If you want to link an aspect that isn't represented by Microsoft Graph, or you want to customize the name, you can set the source of the `topic` to `text` and pass in a custom value for it. **webUrl** is required when using `topic` source as `text`.

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
POST https://graph.microsoft.com/v1.0/teamwork/sendActivityNotificationToRecipients
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
    "templateParameters": [
        {
            "name": "deploymentId",
            "value": "6788662"
        }
    ],
    "recipients": [
    	{
        	"@odata.type": "microsoft.graph.aadUserNotificationRecipient",
        	"userId": "569363e2-4e49-4661-87f2-16f245c5d66a"
    	},
    	{
        	"@odata.type": "microsoft.graph.aadUserNotificationRecipient",
        	"userId": "ab88234e-0874-477c-9638-d144296ed04f"
    	},
    	{
        	"@odata.type": "microsoft.graph.aadUserNotificationRecipient",
        	"userId": "01c64f53-69aa-42c7-9b7f-9f75195d6bfc"
    	}
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teamwork.SendActivityNotificationToRecipients;
using Microsoft.Graph.Models;

var requestBody = new SendActivityNotificationToRecipientsPostRequestBody
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
	TemplateParameters = new List<KeyValuePair>
	{
		new KeyValuePair
		{
			Name = "deploymentId",
			Value = "6788662",
		},
	},
	Recipients = new List<TeamworkNotificationRecipient>
	{
		new AadUserNotificationRecipient
		{
			OdataType = "microsoft.graph.aadUserNotificationRecipient",
			UserId = "569363e2-4e49-4661-87f2-16f245c5d66a",
		},
		new AadUserNotificationRecipient
		{
			OdataType = "microsoft.graph.aadUserNotificationRecipient",
			UserId = "ab88234e-0874-477c-9638-d144296ed04f",
		},
		new AadUserNotificationRecipient
		{
			OdataType = "microsoft.graph.aadUserNotificationRecipient",
			UserId = "01c64f53-69aa-42c7-9b7f-9f75195d6bfc",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teamwork.SendActivityNotificationToRecipients.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphteamwork "github.com/microsoftgraph/msgraph-sdk-go/teamwork"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphteamwork.NewSendActivityNotificationToRecipientsPostRequestBody()
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


keyValuePair := graphmodels.NewKeyValuePair()
name := "deploymentId"
keyValuePair.SetName(&name) 
value := "6788662"
keyValuePair.SetValue(&value) 

templateParameters := []graphmodels.KeyValuePairable {
	keyValuePair,
}
requestBody.SetTemplateParameters(templateParameters)


teamworkNotificationRecipient := graphmodels.NewAadUserNotificationRecipient()
userId := "569363e2-4e49-4661-87f2-16f245c5d66a"
teamworkNotificationRecipient.SetUserId(&userId) 
teamworkNotificationRecipient1 := graphmodels.NewAadUserNotificationRecipient()
userId := "ab88234e-0874-477c-9638-d144296ed04f"
teamworkNotificationRecipient1.SetUserId(&userId) 
teamworkNotificationRecipient2 := graphmodels.NewAadUserNotificationRecipient()
userId := "01c64f53-69aa-42c7-9b7f-9f75195d6bfc"
teamworkNotificationRecipient2.SetUserId(&userId) 

recipients := []graphmodels.TeamworkNotificationRecipientable {
	teamworkNotificationRecipient,
	teamworkNotificationRecipient1,
	teamworkNotificationRecipient2,
}
requestBody.SetRecipients(recipients)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Teamwork().SendActivityNotificationToRecipients().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teamwork.sendactivitynotificationtorecipients.SendActivityNotificationToRecipientsPostRequestBody sendActivityNotificationToRecipientsPostRequestBody = new com.microsoft.graph.teamwork.sendactivitynotificationtorecipients.SendActivityNotificationToRecipientsPostRequestBody();
TeamworkActivityTopic topic = new TeamworkActivityTopic();
topic.setSource(TeamworkActivityTopicSource.Text);
topic.setValue("Deployment Approvals Channel");
topic.setWebUrl("https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000");
sendActivityNotificationToRecipientsPostRequestBody.setTopic(topic);
sendActivityNotificationToRecipientsPostRequestBody.setActivityType("deploymentApprovalRequired");
ItemBody previewText = new ItemBody();
previewText.setContent("New deployment requires your approval");
sendActivityNotificationToRecipientsPostRequestBody.setPreviewText(previewText);
LinkedList<KeyValuePair> templateParameters = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("deploymentId");
keyValuePair.setValue("6788662");
templateParameters.add(keyValuePair);
sendActivityNotificationToRecipientsPostRequestBody.setTemplateParameters(templateParameters);
LinkedList<TeamworkNotificationRecipient> recipients = new LinkedList<TeamworkNotificationRecipient>();
AadUserNotificationRecipient teamworkNotificationRecipient = new AadUserNotificationRecipient();
teamworkNotificationRecipient.setOdataType("microsoft.graph.aadUserNotificationRecipient");
teamworkNotificationRecipient.setUserId("569363e2-4e49-4661-87f2-16f245c5d66a");
recipients.add(teamworkNotificationRecipient);
AadUserNotificationRecipient teamworkNotificationRecipient1 = new AadUserNotificationRecipient();
teamworkNotificationRecipient1.setOdataType("microsoft.graph.aadUserNotificationRecipient");
teamworkNotificationRecipient1.setUserId("ab88234e-0874-477c-9638-d144296ed04f");
recipients.add(teamworkNotificationRecipient1);
AadUserNotificationRecipient teamworkNotificationRecipient2 = new AadUserNotificationRecipient();
teamworkNotificationRecipient2.setOdataType("microsoft.graph.aadUserNotificationRecipient");
teamworkNotificationRecipient2.setUserId("01c64f53-69aa-42c7-9b7f-9f75195d6bfc");
recipients.add(teamworkNotificationRecipient2);
sendActivityNotificationToRecipientsPostRequestBody.setRecipients(recipients);
graphClient.teamwork().sendActivityNotificationToRecipients().post(sendActivityNotificationToRecipientsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sendActivityNotificationToRecipients = {
    topic: {
        source: 'text',
        value: 'Deployment Approvals Channel',
        webUrl: 'https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000'
    },
    activityType: 'deploymentApprovalRequired',
    previewText: {
        content: 'New deployment requires your approval'
    },
    templateParameters: [
        {
            name: 'deploymentId',
            value: '6788662'
        }
    ],
    recipients: [
    	{
        	'@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
        	userId: '569363e2-4e49-4661-87f2-16f245c5d66a'
    	},
    	{
        	'@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
        	userId: 'ab88234e-0874-477c-9638-d144296ed04f'
    	},
    	{
        	'@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
        	userId: '01c64f53-69aa-42c7-9b7f-9f75195d6bfc'
    	}
    ]
};

await client.api('/teamwork/sendActivityNotificationToRecipients')
	.post(sendActivityNotificationToRecipients);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teamwork\SendActivityNotificationToRecipients\SendActivityNotificationToRecipientsPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopic;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopicSource;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\KeyValuePair;
use Microsoft\Graph\Generated\Models\TeamworkNotificationRecipient;
use Microsoft\Graph\Generated\Models\AadUserNotificationRecipient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SendActivityNotificationToRecipientsPostRequestBody();
$topic = new TeamworkActivityTopic();
$topic->setSource(new TeamworkActivityTopicSource('text'));
$topic->setValue('Deployment Approvals Channel');
$topic->setWebUrl('https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000');
$requestBody->setTopic($topic);
$requestBody->setActivityType('deploymentApprovalRequired');
$previewText = new ItemBody();
$previewText->setContent('New deployment requires your approval');
$requestBody->setPreviewText($previewText);
$templateParametersKeyValuePair1 = new KeyValuePair();
$templateParametersKeyValuePair1->setName('deploymentId');
$templateParametersKeyValuePair1->setValue('6788662');
$templateParametersArray []= $templateParametersKeyValuePair1;
$requestBody->setTemplateParameters($templateParametersArray);

$recipientsTeamworkNotificationRecipient1 = new AadUserNotificationRecipient();
$recipientsTeamworkNotificationRecipient1->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipientsTeamworkNotificationRecipient1->setUserId('569363e2-4e49-4661-87f2-16f245c5d66a');
$recipientsArray []= $recipientsTeamworkNotificationRecipient1;
$recipientsTeamworkNotificationRecipient2 = new AadUserNotificationRecipient();
$recipientsTeamworkNotificationRecipient2->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipientsTeamworkNotificationRecipient2->setUserId('ab88234e-0874-477c-9638-d144296ed04f');
$recipientsArray []= $recipientsTeamworkNotificationRecipient2;
$recipientsTeamworkNotificationRecipient3 = new AadUserNotificationRecipient();
$recipientsTeamworkNotificationRecipient3->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipientsTeamworkNotificationRecipient3->setUserId('01c64f53-69aa-42c7-9b7f-9f75195d6bfc');
$recipientsArray []= $recipientsTeamworkNotificationRecipient3;
$requestBody->setRecipients($recipientsArray);


$graphServiceClient->teamwork()->sendActivityNotificationToRecipients()->post($requestBody)->wait();
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
	templateParameters = @(
		@{
			name = "deploymentId"
			value = "6788662"
		}
	)
	recipients = @(
		@{
			"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
			userId = "569363e2-4e49-4661-87f2-16f245c5d66a"
		}
		@{
			"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
			userId = "ab88234e-0874-477c-9638-d144296ed04f"
		}
		@{
			"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
			userId = "01c64f53-69aa-42c7-9b7f-9f75195d6bfc"
		}
	)
}

Send-MgTeamworkActivityNotificationToRecipient -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teamwork.send_activity_notification_to_recipients.send_activity_notification_to_recipients_post_request_body import SendActivityNotificationToRecipientsPostRequestBody
from msgraph.generated.models.teamwork_activity_topic import TeamworkActivityTopic
from msgraph.generated.models.teamwork_activity_topic_source import TeamworkActivityTopicSource
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.key_value_pair import KeyValuePair
from msgraph.generated.models.teamwork_notification_recipient import TeamworkNotificationRecipient
from msgraph.generated.models.aad_user_notification_recipient import AadUserNotificationRecipient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SendActivityNotificationToRecipientsPostRequestBody(
	topic = TeamworkActivityTopic(
		source = TeamworkActivityTopicSource.Text,
		value = "Deployment Approvals Channel",
		web_url = "https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000",
	),
	activity_type = "deploymentApprovalRequired",
	preview_text = ItemBody(
		content = "New deployment requires your approval",
	),
	template_parameters = [
		KeyValuePair(
			name = "deploymentId",
			value = "6788662",
		),
	],
	recipients = [
		AadUserNotificationRecipient(
			odata_type = "microsoft.graph.aadUserNotificationRecipient",
			user_id = "569363e2-4e49-4661-87f2-16f245c5d66a",
		),
		AadUserNotificationRecipient(
			odata_type = "microsoft.graph.aadUserNotificationRecipient",
			user_id = "ab88234e-0874-477c-9638-d144296ed04f",
		),
		AadUserNotificationRecipient(
			odata_type = "microsoft.graph.aadUserNotificationRecipient",
			user_id = "01c64f53-69aa-42c7-9b7f-9f75195d6bfc",
		),
	],
)

await graph_client.teamwork.send_activity_notification_to_recipients.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

```http
HTTP/1.1 202 Accepted
```

### Example 3: Notify multiple users about an event using a custom icon

If you want to notify multiple users with a customized icon instead of the default app icon, you can set the optional **iconId** property in the request body.

> **Note:** The `activityType` in the manifest must contain the list of allowed icon IDs in order to use this parameter. The request validation fails if the app manifest is missing the customized list of icons. For more information, see [Public developer preview app manifest](https://learn.microsoft.com/en-us/microsoftteams/platform/resources/schema/manifest-schema-dev-preview).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
POST https://graph.microsoft.com/v1.0/teamwork/sendActivityNotificationToRecipients
Content-Type: application/json

{
  "topic": {
    "source": "text",
    "value": "Deployment Approvals Channel",
    "webUrl": "https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000"
  },
  "activityType": "announcementPosted",
  "previewText": {
    "content": "new announcemnet posted"
  },
  "iconId": "announcementCreated",
  "templateParameters": [
    {
      "name": "deploymentId",
      "value": "6788662"
    }
  ],
  "recipients": [
    {
      "@odata.type": "microsoft.graph.aadUserNotificationRecipient",
      "userId": "569363e2-4e49-4661-87f2-16f245c5d66a"
    },
    {
      "@odata.type": "microsoft.graph.aadUserNotificationRecipient",
      "userId": "ab88234e-0874-477c-9638-d144296ed04f"
    },
    {
      "@odata.type": "microsoft.graph.aadUserNotificationRecipient",
      "userId": "01c64f53-69aa-42c7-9b7f-9f75195d6bfc"
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Teamwork.SendActivityNotificationToRecipients;
using Microsoft.Graph.Models;

var requestBody = new SendActivityNotificationToRecipientsPostRequestBody
{
	Topic = new TeamworkActivityTopic
	{
		Source = TeamworkActivityTopicSource.Text,
		Value = "Deployment Approvals Channel",
		WebUrl = "https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000",
	},
	ActivityType = "announcementPosted",
	PreviewText = new ItemBody
	{
		Content = "new announcemnet posted",
	},
	IconId = "announcementCreated",
	TemplateParameters = new List<KeyValuePair>
	{
		new KeyValuePair
		{
			Name = "deploymentId",
			Value = "6788662",
		},
	},
	Recipients = new List<TeamworkNotificationRecipient>
	{
		new AadUserNotificationRecipient
		{
			OdataType = "microsoft.graph.aadUserNotificationRecipient",
			UserId = "569363e2-4e49-4661-87f2-16f245c5d66a",
		},
		new AadUserNotificationRecipient
		{
			OdataType = "microsoft.graph.aadUserNotificationRecipient",
			UserId = "ab88234e-0874-477c-9638-d144296ed04f",
		},
		new AadUserNotificationRecipient
		{
			OdataType = "microsoft.graph.aadUserNotificationRecipient",
			UserId = "01c64f53-69aa-42c7-9b7f-9f75195d6bfc",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Teamwork.SendActivityNotificationToRecipients.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphteamwork "github.com/microsoftgraph/msgraph-sdk-go/teamwork"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphteamwork.NewSendActivityNotificationToRecipientsPostRequestBody()
topic := graphmodels.NewTeamworkActivityTopic()
source := graphmodels.TEXT_TEAMWORKACTIVITYTOPICSOURCE 
topic.SetSource(&source) 
value := "Deployment Approvals Channel"
topic.SetValue(&value) 
webUrl := "https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000"
topic.SetWebUrl(&webUrl) 
requestBody.SetTopic(topic)
activityType := "announcementPosted"
requestBody.SetActivityType(&activityType) 
previewText := graphmodels.NewItemBody()
content := "new announcemnet posted"
previewText.SetContent(&content) 
requestBody.SetPreviewText(previewText)
iconId := "announcementCreated"
requestBody.SetIconId(&iconId) 


keyValuePair := graphmodels.NewKeyValuePair()
name := "deploymentId"
keyValuePair.SetName(&name) 
value := "6788662"
keyValuePair.SetValue(&value) 

templateParameters := []graphmodels.KeyValuePairable {
	keyValuePair,
}
requestBody.SetTemplateParameters(templateParameters)


teamworkNotificationRecipient := graphmodels.NewAadUserNotificationRecipient()
userId := "569363e2-4e49-4661-87f2-16f245c5d66a"
teamworkNotificationRecipient.SetUserId(&userId) 
teamworkNotificationRecipient1 := graphmodels.NewAadUserNotificationRecipient()
userId := "ab88234e-0874-477c-9638-d144296ed04f"
teamworkNotificationRecipient1.SetUserId(&userId) 
teamworkNotificationRecipient2 := graphmodels.NewAadUserNotificationRecipient()
userId := "01c64f53-69aa-42c7-9b7f-9f75195d6bfc"
teamworkNotificationRecipient2.SetUserId(&userId) 

recipients := []graphmodels.TeamworkNotificationRecipientable {
	teamworkNotificationRecipient,
	teamworkNotificationRecipient1,
	teamworkNotificationRecipient2,
}
requestBody.SetRecipients(recipients)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Teamwork().SendActivityNotificationToRecipients().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.teamwork.sendactivitynotificationtorecipients.SendActivityNotificationToRecipientsPostRequestBody sendActivityNotificationToRecipientsPostRequestBody = new com.microsoft.graph.teamwork.sendactivitynotificationtorecipients.SendActivityNotificationToRecipientsPostRequestBody();
TeamworkActivityTopic topic = new TeamworkActivityTopic();
topic.setSource(TeamworkActivityTopicSource.Text);
topic.setValue("Deployment Approvals Channel");
topic.setWebUrl("https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000");
sendActivityNotificationToRecipientsPostRequestBody.setTopic(topic);
sendActivityNotificationToRecipientsPostRequestBody.setActivityType("announcementPosted");
ItemBody previewText = new ItemBody();
previewText.setContent("new announcemnet posted");
sendActivityNotificationToRecipientsPostRequestBody.setPreviewText(previewText);
sendActivityNotificationToRecipientsPostRequestBody.setIconId("announcementCreated");
LinkedList<KeyValuePair> templateParameters = new LinkedList<KeyValuePair>();
KeyValuePair keyValuePair = new KeyValuePair();
keyValuePair.setName("deploymentId");
keyValuePair.setValue("6788662");
templateParameters.add(keyValuePair);
sendActivityNotificationToRecipientsPostRequestBody.setTemplateParameters(templateParameters);
LinkedList<TeamworkNotificationRecipient> recipients = new LinkedList<TeamworkNotificationRecipient>();
AadUserNotificationRecipient teamworkNotificationRecipient = new AadUserNotificationRecipient();
teamworkNotificationRecipient.setOdataType("microsoft.graph.aadUserNotificationRecipient");
teamworkNotificationRecipient.setUserId("569363e2-4e49-4661-87f2-16f245c5d66a");
recipients.add(teamworkNotificationRecipient);
AadUserNotificationRecipient teamworkNotificationRecipient1 = new AadUserNotificationRecipient();
teamworkNotificationRecipient1.setOdataType("microsoft.graph.aadUserNotificationRecipient");
teamworkNotificationRecipient1.setUserId("ab88234e-0874-477c-9638-d144296ed04f");
recipients.add(teamworkNotificationRecipient1);
AadUserNotificationRecipient teamworkNotificationRecipient2 = new AadUserNotificationRecipient();
teamworkNotificationRecipient2.setOdataType("microsoft.graph.aadUserNotificationRecipient");
teamworkNotificationRecipient2.setUserId("01c64f53-69aa-42c7-9b7f-9f75195d6bfc");
recipients.add(teamworkNotificationRecipient2);
sendActivityNotificationToRecipientsPostRequestBody.setRecipients(recipients);
graphClient.teamwork().sendActivityNotificationToRecipients().post(sendActivityNotificationToRecipientsPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const sendActivityNotificationToRecipients = {
  topic: {
    source: 'text',
    value: 'Deployment Approvals Channel',
    webUrl: 'https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000'
  },
  activityType: 'announcementPosted',
  previewText: {
    content: 'new announcemnet posted'
  },
  iconId: 'announcementCreated',
  templateParameters: [
    {
      name: 'deploymentId',
      value: '6788662'
    }
  ],
  recipients: [
    {
      '@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
      userId: '569363e2-4e49-4661-87f2-16f245c5d66a'
    },
    {
      '@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
      userId: 'ab88234e-0874-477c-9638-d144296ed04f'
    },
    {
      '@odata.type': 'microsoft.graph.aadUserNotificationRecipient',
      userId: '01c64f53-69aa-42c7-9b7f-9f75195d6bfc'
    }
  ]
};

await client.api('/teamwork/sendActivityNotificationToRecipients')
	.post(sendActivityNotificationToRecipients);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teamwork\SendActivityNotificationToRecipients\SendActivityNotificationToRecipientsPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopic;
use Microsoft\Graph\Generated\Models\TeamworkActivityTopicSource;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\KeyValuePair;
use Microsoft\Graph\Generated\Models\TeamworkNotificationRecipient;
use Microsoft\Graph\Generated\Models\AadUserNotificationRecipient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SendActivityNotificationToRecipientsPostRequestBody();
$topic = new TeamworkActivityTopic();
$topic->setSource(new TeamworkActivityTopicSource('text'));
$topic->setValue('Deployment Approvals Channel');
$topic->setWebUrl('https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000');
$requestBody->setTopic($topic);
$requestBody->setActivityType('announcementPosted');
$previewText = new ItemBody();
$previewText->setContent('new announcemnet posted');
$requestBody->setPreviewText($previewText);
$requestBody->setIconId('announcementCreated');
$templateParametersKeyValuePair1 = new KeyValuePair();
$templateParametersKeyValuePair1->setName('deploymentId');
$templateParametersKeyValuePair1->setValue('6788662');
$templateParametersArray []= $templateParametersKeyValuePair1;
$requestBody->setTemplateParameters($templateParametersArray);

$recipientsTeamworkNotificationRecipient1 = new AadUserNotificationRecipient();
$recipientsTeamworkNotificationRecipient1->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipientsTeamworkNotificationRecipient1->setUserId('569363e2-4e49-4661-87f2-16f245c5d66a');
$recipientsArray []= $recipientsTeamworkNotificationRecipient1;
$recipientsTeamworkNotificationRecipient2 = new AadUserNotificationRecipient();
$recipientsTeamworkNotificationRecipient2->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipientsTeamworkNotificationRecipient2->setUserId('ab88234e-0874-477c-9638-d144296ed04f');
$recipientsArray []= $recipientsTeamworkNotificationRecipient2;
$recipientsTeamworkNotificationRecipient3 = new AadUserNotificationRecipient();
$recipientsTeamworkNotificationRecipient3->setOdataType('microsoft.graph.aadUserNotificationRecipient');
$recipientsTeamworkNotificationRecipient3->setUserId('01c64f53-69aa-42c7-9b7f-9f75195d6bfc');
$recipientsArray []= $recipientsTeamworkNotificationRecipient3;
$requestBody->setRecipients($recipientsArray);


$graphServiceClient->teamwork()->sendActivityNotificationToRecipients()->post($requestBody)->wait();
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
	activityType = "announcementPosted"
	previewText = @{
		content = "new announcemnet posted"
	}
	iconId = "announcementCreated"
	templateParameters = @(
		@{
			name = "deploymentId"
			value = "6788662"
		}
	)
	recipients = @(
		@{
			"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
			userId = "569363e2-4e49-4661-87f2-16f245c5d66a"
		}
		@{
			"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
			userId = "ab88234e-0874-477c-9638-d144296ed04f"
		}
		@{
			"@odata.type" = "microsoft.graph.aadUserNotificationRecipient"
			userId = "01c64f53-69aa-42c7-9b7f-9f75195d6bfc"
		}
	)
}

Send-MgTeamworkActivityNotificationToRecipient -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teamwork.send_activity_notification_to_recipients.send_activity_notification_to_recipients_post_request_body import SendActivityNotificationToRecipientsPostRequestBody
from msgraph.generated.models.teamwork_activity_topic import TeamworkActivityTopic
from msgraph.generated.models.teamwork_activity_topic_source import TeamworkActivityTopicSource
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.key_value_pair import KeyValuePair
from msgraph.generated.models.teamwork_notification_recipient import TeamworkNotificationRecipient
from msgraph.generated.models.aad_user_notification_recipient import AadUserNotificationRecipient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SendActivityNotificationToRecipientsPostRequestBody(
	topic = TeamworkActivityTopic(
		source = TeamworkActivityTopicSource.Text,
		value = "Deployment Approvals Channel",
		web_url = "https://teams.microsoft.com/l/message/19:448cfd2ac2a7490a9084a9ed14cttr78c@thread.skype/1605223780000?tenantId=c8b1bf45-3834-4ecf-971a-b4c755ee677d&groupId=d4c2a937-f097-435a-bc91-5c1683ca7245&parentMessageId=1605223771864&teamName=Approvals&channelName=Azure%20DevOps&createdTime=1605223780000",
	),
	activity_type = "announcementPosted",
	preview_text = ItemBody(
		content = "new announcemnet posted",
	),
	icon_id = "announcementCreated",
	template_parameters = [
		KeyValuePair(
			name = "deploymentId",
			value = "6788662",
		),
	],
	recipients = [
		AadUserNotificationRecipient(
			odata_type = "microsoft.graph.aadUserNotificationRecipient",
			user_id = "569363e2-4e49-4661-87f2-16f245c5d66a",
		),
		AadUserNotificationRecipient(
			odata_type = "microsoft.graph.aadUserNotificationRecipient",
			user_id = "ab88234e-0874-477c-9638-d144296ed04f",
		),
		AadUserNotificationRecipient(
			odata_type = "microsoft.graph.aadUserNotificationRecipient",
			user_id = "01c64f53-69aa-42c7-9b7f-9f75195d6bfc",
		),
	],
)

await graph_client.teamwork.send_activity_notification_to_recipients.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
```
