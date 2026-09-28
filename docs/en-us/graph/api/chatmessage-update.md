<!-- Source: https://learn.microsoft.com/en-us/graph/api/chatmessage-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update chatMessage

Update a [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) object. Except for the **policyViolation** property, all properties of a **chatMessage** can be updated in delegated permissions scenarios. Only the **policyViolation** property of a **chatMessage** can be updated in application permissions scenarios.

The update only works for chats where members are Microsoft Teams users. If one of the participants is using Skype, the operation fails.

This method doesn't support federation. Only the user in the tenant who sent the message can perform data loss prevention \(DLP\) updates on the specified chat message.

Note

When used with application permissions, a [license](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-loss-prevention-graph-apis-for-teams-data-loss-prevention-dlp-and-for-teams-export) that includes the Microsoft Communications DLP [service plan](https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/licensing-service-plan-reference) is required.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

### Permissions for channel

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | ChannelMessage.ReadWrite, Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | ChannelMessage.UpdatePolicyViolation.All, Group.ReadWrite.All\*\* |

Note

The Group.ReadWrite.All permission is supported only for backward compatibility. We recommend that you update your solutions to use an alternative permission listed in the previous table and avoid using these permissions going forward.

### Permissions for chat

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | Chat.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | Chat.UpdatePolicyViolation.All, Chat.ReadWrite.All |

## HTTP request

To update a **chatMessage** in a **channel**:

```http
PATCH /teams/(team-id)/channels/{channel-id}/messages/{message-id}
PATCH /teams/(team-id)/channels/{channel-id}/messages/{message-id}/replies/{reply-id}
```

To update a **chatMessage** in a **chat**:

```http
PATCH /chats/{chatThread-id}/messages/{message-id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

For applications that use delegated permissions: In the request body, supply a JSON representation of a [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) object, specifying the properties that need to be changed.

For applications that use application permissions: In the request body, supply a JSON representation of a [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) object, specifying only the **policyViolation** property.

## Response body

For applications that use delegated permissions: If successful, this method returns a `204 No Content` response.

For applications that use application permissions: If successful, this method returns a `200 OK` response.

### Errors

The following table lists other response codes that this API can return.

| Sample error type | Status code | Sample error messages |
| :--- | :--- | :--- |
| E5 license or Microsoft Communications service plan requirement not met. | 402 Payment Required | `"...needs a valid license to access this API..."`  <br>`"...tenant needs a valid license to access this API..."` |

## Examples

### Example 1: Update policyViolation property using application permissions

#### Request

The following example shows a request to update the **policyViolation** property on a Microsoft Teams channel message by using application permissions.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/teams/e1234567-e123-4276-55555-6232b0e3a89a/channels/a7654321-e321-0000-0000-123b0e3a00a/messages/19%3Aa21b0b0c05194ebc9e30000000000f61%40thread.skype
Content-Type: application/json

{
  "policyViolation": {
    "policyTip": {
      "generalText" : "This item has been blocked by the administrator.",
      "complianceUrl" : "https://contoso.com/dlp-policy-page",
      "matchedConditionDescriptions" : ["Credit Card Number"]
    },
    "verdictDetails" : "AllowOverrideWithoutJustification,AllowFalsePositiveOverride",
    "dlpAction" : "BlockAccess"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ChatMessage
{
	PolicyViolation = new ChatMessagePolicyViolation
	{
		PolicyTip = new ChatMessagePolicyViolationPolicyTip
		{
			GeneralText = "This item has been blocked by the administrator.",
			ComplianceUrl = "https://contoso.com/dlp-policy-page",
			MatchedConditionDescriptions = new List<string>
			{
				"Credit Card Number",
			},
		},
		VerdictDetails = ChatMessagePolicyViolationVerdictDetailsTypes.AllowOverrideWithoutJustification | ChatMessagePolicyViolationVerdictDetailsTypes.AllowFalsePositiveOverride,
		DlpAction = ChatMessagePolicyViolationDlpActionTypes.BlockAccess,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages["{chatMessage-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewChatMessage()
policyViolation := graphmodels.NewChatMessagePolicyViolation()
policyTip := graphmodels.NewChatMessagePolicyViolationPolicyTip()
generalText := "This item has been blocked by the administrator."
policyTip.SetGeneralText(&generalText) 
complianceUrl := "https://contoso.com/dlp-policy-page"
policyTip.SetComplianceUrl(&complianceUrl) 
matchedConditionDescriptions := []string {
	"Credit Card Number",
}
policyTip.SetMatchedConditionDescriptions(matchedConditionDescriptions)
policyViolation.SetPolicyTip(policyTip)
verdictDetails := graphmodels.ALLOWOVERRIDEWITHOUTJUSTIFICATION,ALLOWFALSEPOSITIVEOVERRIDE_CHATMESSAGEPOLICYVIOLATIONVERDICTDETAILSTYPES 
policyViolation.SetVerdictDetails(&verdictDetails) 
dlpAction := graphmodels.BLOCKACCESS_CHATMESSAGEPOLICYVIOLATIONDLPACTIONTYPES 
policyViolation.SetDlpAction(&dlpAction) 
requestBody.SetPolicyViolation(policyViolation)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().ByChatMessageId("chatMessage-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
ChatMessagePolicyViolation policyViolation = new ChatMessagePolicyViolation();
ChatMessagePolicyViolationPolicyTip policyTip = new ChatMessagePolicyViolationPolicyTip();
policyTip.setGeneralText("This item has been blocked by the administrator.");
policyTip.setComplianceUrl("https://contoso.com/dlp-policy-page");
LinkedList<String> matchedConditionDescriptions = new LinkedList<String>();
matchedConditionDescriptions.add("Credit Card Number");
policyTip.setMatchedConditionDescriptions(matchedConditionDescriptions);
policyViolation.setPolicyTip(policyTip);
policyViolation.setVerdictDetails(EnumSet.of(ChatMessagePolicyViolationVerdictDetailsTypes.AllowOverrideWithoutJustification, ChatMessagePolicyViolationVerdictDetailsTypes.AllowFalsePositiveOverride));
policyViolation.setDlpAction(EnumSet.of(ChatMessagePolicyViolationDlpActionTypes.BlockAccess));
chatMessage.setPolicyViolation(policyViolation);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().byChatMessageId("{chatMessage-id}").patch(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
  policyViolation: {
    policyTip: {
      generalText: 'This item has been blocked by the administrator.',
      complianceUrl: 'https://contoso.com/dlp-policy-page',
      matchedConditionDescriptions: ['Credit Card Number']
    },
    verdictDetails: 'AllowOverrideWithoutJustification,AllowFalsePositiveOverride',
    dlpAction: 'BlockAccess'
  }
};

await client.api('/teams/e1234567-e123-4276-55555-6232b0e3a89a/channels/a7654321-e321-0000-0000-123b0e3a00a/messages/19:a21b0b0c05194ebc9e30000000000f61@thread.skype')
	.update(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ChatMessagePolicyViolation;
use Microsoft\Graph\Generated\Models\ChatMessagePolicyViolationPolicyTip;
use Microsoft\Graph\Generated\Models\ChatMessagePolicyViolationVerdictDetailsTypes;
use Microsoft\Graph\Generated\Models\ChatMessagePolicyViolationDlpActionTypes;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$policyViolation = new ChatMessagePolicyViolation();
$policyViolationPolicyTip = new ChatMessagePolicyViolationPolicyTip();
$policyViolationPolicyTip->setGeneralText('This item has been blocked by the administrator.');
$policyViolationPolicyTip->setComplianceUrl('https://contoso.com/dlp-policy-page');
$policyViolationPolicyTip->setMatchedConditionDescriptions(['Credit Card Number', 	]);
$policyViolation->setPolicyTip($policyViolationPolicyTip);
$policyViolation->setVerdictDetails(new ChatMessagePolicyViolationVerdictDetailsTypes('allowOverrideWithoutJustification,AllowFalsePositiveOverride'));
$policyViolation->setDlpAction(new ChatMessagePolicyViolationDlpActionTypes('blockAccess'));
$requestBody->setPolicyViolation($policyViolation);

$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->byChatMessageId('chatMessage-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	policyViolation = @{
		policyTip = @{
			generalText = "This item has been blocked by the administrator."
			complianceUrl = "https://contoso.com/dlp-policy-page"
			matchedConditionDescriptions = @(
			"Credit Card Number"
		)
	}
	verdictDetails = "AllowOverrideWithoutJustification,AllowFalsePositiveOverride"
	dlpAction = "BlockAccess"
}
}

Update-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -ChatMessageId $chatMessageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.chat_message_policy_violation import ChatMessagePolicyViolation
from msgraph.generated.models.chat_message_policy_violation_policy_tip import ChatMessagePolicyViolationPolicyTip
from msgraph.generated.models.chat_message_policy_violation_verdict_details_types import ChatMessagePolicyViolationVerdictDetailsTypes
from msgraph.generated.models.chat_message_policy_violation_dlp_action_types import ChatMessagePolicyViolationDlpActionTypes
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	policy_violation = ChatMessagePolicyViolation(
		policy_tip = ChatMessagePolicyViolationPolicyTip(
			general_text = "This item has been blocked by the administrator.",
			compliance_url = "https://contoso.com/dlp-policy-page",
			matched_condition_descriptions = [
				"Credit Card Number",
			],
		),
		verdict_details = ChatMessagePolicyViolationVerdictDetailsTypes.AllowOverrideWithoutJustification | ChatMessagePolicyViolationVerdictDetailsTypes.AllowFalsePositiveOverride,
		dlp_action = ChatMessagePolicyViolationDlpActionTypes.BlockAccess,
	),
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.by_chat_message_id('chatMessage-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```

### Example 2: Update any property of a message using delegated permissions

#### Request

The following example shows a request to update the properties on a Microsoft Teams channel message by using delegated permissions.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/teams/e1234567-e123-4276-55555-6232b0e3a89a/channels/a7654321-e321-0000-0000-123b0e3a00a/messages/19%3Aa21b0b0c05194ebc9e30000000000f61%40thread.skype
Content-Type: application/json

{
  "messageType": "message",
  "subject": null,
  "summary": null,
  "importance": "normal",
  "locale": "en-us",
  "from": {
    "application": null,
    "device": null,
    "user": {
      "id": "3b102402-813e-4e17-a6b2-f841aef1fdfc",
      "displayName": "Lam Cong",
      "userIdentityType": "aadUser"
    },
    "conversation": null
  },
  "body": {
    "contentType": "text",
    "content": "Edit text only"
  },
  "attachments": [],
  "mentions": [],
  "reactions": [],
  "messageHistory": []
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ChatMessage
{
	MessageType = ChatMessageType.Message,
	Subject = null,
	Summary = null,
	Importance = ChatMessageImportance.Normal,
	Locale = "en-us",
	From = new ChatMessageFromIdentitySet
	{
		Application = null,
		Device = null,
		User = new Identity
		{
			Id = "3b102402-813e-4e17-a6b2-f841aef1fdfc",
			DisplayName = "Lam Cong",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"userIdentityType" , "aadUser"
				},
			},
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"conversation" , null
			},
		},
	},
	Body = new ItemBody
	{
		ContentType = BodyType.Text,
		Content = "Edit text only",
	},
	Attachments = new List<ChatMessageAttachment>
	{
	},
	Mentions = new List<ChatMessageMention>
	{
	},
	Reactions = new List<ChatMessageReaction>
	{
	},
	MessageHistory = new List<ChatMessageHistoryItem>
	{
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages["{chatMessage-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewChatMessage()
messageType := graphmodels.MESSAGE_CHATMESSAGETYPE 
requestBody.SetMessageType(&messageType) 
subject := null
requestBody.SetSubject(&subject) 
summary := null
requestBody.SetSummary(&summary) 
importance := graphmodels.NORMAL_CHATMESSAGEIMPORTANCE 
requestBody.SetImportance(&importance) 
locale := "en-us"
requestBody.SetLocale(&locale) 
from := graphmodels.NewChatMessageFromIdentitySet()
application := null
from.SetApplication(&application) 
device := null
from.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "3b102402-813e-4e17-a6b2-f841aef1fdfc"
user.SetId(&id) 
displayName := "Lam Cong"
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
from.SetUser(user)
additionalData := map[string]interface{}{
	conversation := null
from.SetConversation(&conversation) 
}
from.SetAdditionalData(additionalData)
requestBody.SetFrom(from)
body := graphmodels.NewItemBody()
contentType := graphmodels.TEXT_BODYTYPE 
body.SetContentType(&contentType) 
content := "Edit text only"
body.SetContent(&content) 
requestBody.SetBody(body)
attachments := []graphmodels.ChatMessageAttachmentable {

}
requestBody.SetAttachments(attachments)
mentions := []graphmodels.ChatMessageMentionable {

}
requestBody.SetMentions(mentions)
reactions := []graphmodels.ChatMessageReactionable {

}
requestBody.SetReactions(reactions)
messageHistory := []graphmodels.ChatMessageHistoryItemable {

}
requestBody.SetMessageHistory(messageHistory)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().ByChatMessageId("chatMessage-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
chatMessage.setMessageType(ChatMessageType.Message);
chatMessage.setSubject(null);
chatMessage.setSummary(null);
chatMessage.setImportance(ChatMessageImportance.Normal);
chatMessage.setLocale("en-us");
ChatMessageFromIdentitySet from = new ChatMessageFromIdentitySet();
from.setApplication(null);
from.setDevice(null);
Identity user = new Identity();
user.setId("3b102402-813e-4e17-a6b2-f841aef1fdfc");
user.setDisplayName("Lam Cong");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("userIdentityType", "aadUser");
user.setAdditionalData(additionalData);
from.setUser(user);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("conversation", null);
from.setAdditionalData(additionalData1);
chatMessage.setFrom(from);
ItemBody body = new ItemBody();
body.setContentType(BodyType.Text);
body.setContent("Edit text only");
chatMessage.setBody(body);
LinkedList<ChatMessageAttachment> attachments = new LinkedList<ChatMessageAttachment>();
chatMessage.setAttachments(attachments);
LinkedList<ChatMessageMention> mentions = new LinkedList<ChatMessageMention>();
chatMessage.setMentions(mentions);
LinkedList<ChatMessageReaction> reactions = new LinkedList<ChatMessageReaction>();
chatMessage.setReactions(reactions);
LinkedList<ChatMessageHistoryItem> messageHistory = new LinkedList<ChatMessageHistoryItem>();
chatMessage.setMessageHistory(messageHistory);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().byChatMessageId("{chatMessage-id}").patch(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
  messageType: 'message',
  subject: null,
  summary: null,
  importance: 'normal',
  locale: 'en-us',
  from: {
    application: null,
    device: null,
    user: {
      id: '3b102402-813e-4e17-a6b2-f841aef1fdfc',
      displayName: 'Lam Cong',
      userIdentityType: 'aadUser'
    },
    conversation: null
  },
  body: {
    contentType: 'text',
    content: 'Edit text only'
  },
  attachments: [],
  mentions: [],
  reactions: [],
  messageHistory: []
};

await client.api('/teams/e1234567-e123-4276-55555-6232b0e3a89a/channels/a7654321-e321-0000-0000-123b0e3a00a/messages/19:a21b0b0c05194ebc9e30000000000f61@thread.skype')
	.update(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ChatMessageType;
use Microsoft\Graph\Generated\Models\ChatMessageImportance;
use Microsoft\Graph\Generated\Models\ChatMessageFromIdentitySet;
use Microsoft\Graph\Generated\Models\Identity;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageAttachment;
use Microsoft\Graph\Generated\Models\ChatMessageMention;
use Microsoft\Graph\Generated\Models\ChatMessageReaction;
use Microsoft\Graph\Generated\Models\ChatMessageHistoryItem;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$requestBody->setMessageType(new ChatMessageType('message'));
$requestBody->setSubject(null);
$requestBody->setSummary(null);
$requestBody->setImportance(new ChatMessageImportance('normal'));
$requestBody->setLocale('en-us');
$from = new ChatMessageFromIdentitySet();
$from->setApplication(null);
$from->setDevice(null);
$fromUser = new Identity();
$fromUser->setId('3b102402-813e-4e17-a6b2-f841aef1fdfc');
$fromUser->setDisplayName('Lam Cong');
$additionalData = [
	'userIdentityType' => 'aadUser',
];
$fromUser->setAdditionalData($additionalData);
$from->setUser($fromUser);
$additionalData = [
	'conversation' => null,
];
$from->setAdditionalData($additionalData);
$requestBody->setFrom($from);
$body = new ItemBody();
$body->setContentType(new BodyType('text'));
$body->setContent('Edit text only');
$requestBody->setBody($body);
$requestBody->setAttachments([	]);
$requestBody->setMentions([	]);
$requestBody->setReactions([	]);
$requestBody->setMessageHistory([	]);

$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->byChatMessageId('chatMessage-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	messageType = "message"
	subject = $null
	summary = $null
	importance = "normal"
	locale = "en-us"
	from = @{
		application = $null
		device = $null
		user = @{
			id = "3b102402-813e-4e17-a6b2-f841aef1fdfc"
			displayName = "Lam Cong"
			userIdentityType = "aadUser"
		}
		conversation = $null
	}
	body = @{
		contentType = "text"
		content = "Edit text only"
	}
	attachments = @(
	)
	mentions = @(
	)
	reactions = @(
	)
	messageHistory = @(
	)
}

Update-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -ChatMessageId $chatMessageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.chat_message_type import ChatMessageType
from msgraph.generated.models.chat_message_importance import ChatMessageImportance
from msgraph.generated.models.chat_message_from_identity_set import ChatMessageFromIdentitySet
from msgraph.generated.models.identity import Identity
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_attachment import ChatMessageAttachment
from msgraph.generated.models.chat_message_mention import ChatMessageMention
from msgraph.generated.models.chat_message_reaction import ChatMessageReaction
from msgraph.generated.models.chat_message_history_item import ChatMessageHistoryItem
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	message_type = ChatMessageType.Message,
	subject = None,
	summary = None,
	importance = ChatMessageImportance.Normal,
	locale = "en-us",
	from = ChatMessageFromIdentitySet(
		application = None,
		device = None,
		user = Identity(
			id = "3b102402-813e-4e17-a6b2-f841aef1fdfc",
			display_name = "Lam Cong",
			additional_data = {
					"user_identity_type" : "aadUser",
			}
		),
		additional_data = {
				"conversation" : None,
		}
	),
	body = ItemBody(
		content_type = BodyType.Text,
		content = "Edit text only",
	),
	attachments = [
	],
	mentions = [
	],
	reactions = [
	],
	message_history = [
	],
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.by_chat_message_id('chatMessage-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 3: Update the mentions of a message using delegated permissions

#### Request

The following example shows a request to update the mentions on a Microsoft Teams channel message by using delegated permissions.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
PATCH https://graph.microsoft.com/v1.0/teams/e1234567-e123-4276-55555-6232b0e3a89a/channels/a7654321-e321-0000-0000-123b0e3a00a/messages/19%3Aa21b0b0c05194ebc9e30000000000f61%40thread.skype
Content-Type: application/json

{
  "messageType": "message",
  "deletedDateTime": null,
  "subject": null,
  "summary": null,
  "importance": "normal",
  "locale": "en-us",
  "from": {
    "application": null,
    "device": null,
    "conversation": null,
    "user": {
      "id": "6b3f3c54-d09c-4fdd-b146-9b514a8a4f40",
      "displayName": "Lam Cong",
      "userIdentityType": "aadUser"
    }
  },
  "body": {
    "contentType": "html",
    "content": "<div><div>\n<div>\n<div>\n<div>\n<div><at id=\"0\">Raghav</at><at id=\"1\">TestGlobalBot</at> YEAH"
  },
  "attachments": [],
  "mentions": [
    {
      "id": 0,
      "mentionText": "Raghav",
      "mentioned": {
        "application": null,
        "device": null,
        "conversation": null,
        "user": {
          "id": "f1b66449-b46d-49b0-9c3c-53c10234c818e",
          "displayName": "Lam Cong",
          "userIdentityType": "aadUser"
        }
      }
    },
    {
      "id": 1,
      "mentionText": "TestGlobalBot",
      "mentioned": {
        "application": {
          "id": "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
          "displayName": "TestGlobalBot",
          "applicationIdentityType": "bot"
        },
        "device": null,
        "conversation": null,
        "user": null
      }
    }
  ],
  "reactions": [],
  "messageHistory": []
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ChatMessage
{
	MessageType = ChatMessageType.Message,
	DeletedDateTime = null,
	Subject = null,
	Summary = null,
	Importance = ChatMessageImportance.Normal,
	Locale = "en-us",
	From = new ChatMessageFromIdentitySet
	{
		Application = null,
		Device = null,
		User = new Identity
		{
			Id = "6b3f3c54-d09c-4fdd-b146-9b514a8a4f40",
			DisplayName = "Lam Cong",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"userIdentityType" , "aadUser"
				},
			},
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"conversation" , null
			},
		},
	},
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "<div><div>\n<div>\n<div>\n<div>\n<div><at id=\"0\">Raghav</at><at id=\"1\">TestGlobalBot</at> YEAH",
	},
	Attachments = new List<ChatMessageAttachment>
	{
	},
	Mentions = new List<ChatMessageMention>
	{
		new ChatMessageMention
		{
			Id = 0,
			MentionText = "Raghav",
			Mentioned = new ChatMessageMentionedIdentitySet
			{
				Application = null,
				Device = null,
				Conversation = null,
				User = new Identity
				{
					Id = "f1b66449-b46d-49b0-9c3c-53c10234c818e",
					DisplayName = "Lam Cong",
					AdditionalData = new Dictionary<string, object>
					{
						{
							"userIdentityType" , "aadUser"
						},
					},
				},
			},
		},
		new ChatMessageMention
		{
			Id = 1,
			MentionText = "TestGlobalBot",
			Mentioned = new ChatMessageMentionedIdentitySet
			{
				Application = new Identity
				{
					Id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
					DisplayName = "TestGlobalBot",
					AdditionalData = new Dictionary<string, object>
					{
						{
							"applicationIdentityType" , "bot"
						},
					},
				},
				Device = null,
				Conversation = null,
				User = null,
			},
		},
	},
	Reactions = new List<ChatMessageReaction>
	{
	},
	MessageHistory = new List<ChatMessageHistoryItem>
	{
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages["{chatMessage-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewChatMessage()
messageType := graphmodels.MESSAGE_CHATMESSAGETYPE 
requestBody.SetMessageType(&messageType) 
deletedDateTime := null
requestBody.SetDeletedDateTime(&deletedDateTime) 
subject := null
requestBody.SetSubject(&subject) 
summary := null
requestBody.SetSummary(&summary) 
importance := graphmodels.NORMAL_CHATMESSAGEIMPORTANCE 
requestBody.SetImportance(&importance) 
locale := "en-us"
requestBody.SetLocale(&locale) 
from := graphmodels.NewChatMessageFromIdentitySet()
application := null
from.SetApplication(&application) 
device := null
from.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "6b3f3c54-d09c-4fdd-b146-9b514a8a4f40"
user.SetId(&id) 
displayName := "Lam Cong"
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
from.SetUser(user)
additionalData := map[string]interface{}{
	conversation := null
from.SetConversation(&conversation) 
}
from.SetAdditionalData(additionalData)
requestBody.SetFrom(from)
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "<div><div>\n<div>\n<div>\n<div>\n<div><at id=\"0\">Raghav</at><at id=\"1\">TestGlobalBot</at> YEAH"
body.SetContent(&content) 
requestBody.SetBody(body)
attachments := []graphmodels.ChatMessageAttachmentable {

}
requestBody.SetAttachments(attachments)


chatMessageMention := graphmodels.NewChatMessageMention()
id := int32(0)
chatMessageMention.SetId(&id) 
mentionText := "Raghav"
chatMessageMention.SetMentionText(&mentionText) 
mentioned := graphmodels.NewChatMessageMentionedIdentitySet()
application := null
mentioned.SetApplication(&application) 
device := null
mentioned.SetDevice(&device) 
conversation := null
mentioned.SetConversation(&conversation) 
user := graphmodels.NewIdentity()
id := "f1b66449-b46d-49b0-9c3c-53c10234c818e"
user.SetId(&id) 
displayName := "Lam Cong"
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
mentioned.SetUser(user)
chatMessageMention.SetMentioned(mentioned)
chatMessageMention1 := graphmodels.NewChatMessageMention()
id := int32(1)
chatMessageMention1.SetId(&id) 
mentionText := "TestGlobalBot"
chatMessageMention1.SetMentionText(&mentionText) 
mentioned := graphmodels.NewChatMessageMentionedIdentitySet()
application := graphmodels.NewIdentity()
id := "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
application.SetId(&id) 
displayName := "TestGlobalBot"
application.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"applicationIdentityType" : "bot", 
}
application.SetAdditionalData(additionalData)
mentioned.SetApplication(application)
device := null
mentioned.SetDevice(&device) 
conversation := null
mentioned.SetConversation(&conversation) 
user := null
mentioned.SetUser(&user) 
chatMessageMention1.SetMentioned(mentioned)

mentions := []graphmodels.ChatMessageMentionable {
	chatMessageMention,
	chatMessageMention1,
}
requestBody.SetMentions(mentions)
reactions := []graphmodels.ChatMessageReactionable {

}
requestBody.SetReactions(reactions)
messageHistory := []graphmodels.ChatMessageHistoryItemable {

}
requestBody.SetMessageHistory(messageHistory)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().ByChatMessageId("chatMessage-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
chatMessage.setMessageType(ChatMessageType.Message);
chatMessage.setDeletedDateTime(null);
chatMessage.setSubject(null);
chatMessage.setSummary(null);
chatMessage.setImportance(ChatMessageImportance.Normal);
chatMessage.setLocale("en-us");
ChatMessageFromIdentitySet from = new ChatMessageFromIdentitySet();
from.setApplication(null);
from.setDevice(null);
Identity user = new Identity();
user.setId("6b3f3c54-d09c-4fdd-b146-9b514a8a4f40");
user.setDisplayName("Lam Cong");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("userIdentityType", "aadUser");
user.setAdditionalData(additionalData);
from.setUser(user);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("conversation", null);
from.setAdditionalData(additionalData1);
chatMessage.setFrom(from);
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("<div><div>\n<div>\n<div>\n<div>\n<div><at id=\"0\">Raghav</at><at id=\"1\">TestGlobalBot</at> YEAH");
chatMessage.setBody(body);
LinkedList<ChatMessageAttachment> attachments = new LinkedList<ChatMessageAttachment>();
chatMessage.setAttachments(attachments);
LinkedList<ChatMessageMention> mentions = new LinkedList<ChatMessageMention>();
ChatMessageMention chatMessageMention = new ChatMessageMention();
chatMessageMention.setId(0);
chatMessageMention.setMentionText("Raghav");
ChatMessageMentionedIdentitySet mentioned = new ChatMessageMentionedIdentitySet();
mentioned.setApplication(null);
mentioned.setDevice(null);
mentioned.setConversation(null);
Identity user1 = new Identity();
user1.setId("f1b66449-b46d-49b0-9c3c-53c10234c818e");
user1.setDisplayName("Lam Cong");
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
additionalData2.put("userIdentityType", "aadUser");
user1.setAdditionalData(additionalData2);
mentioned.setUser(user1);
chatMessageMention.setMentioned(mentioned);
mentions.add(chatMessageMention);
ChatMessageMention chatMessageMention1 = new ChatMessageMention();
chatMessageMention1.setId(1);
chatMessageMention1.setMentionText("TestGlobalBot");
ChatMessageMentionedIdentitySet mentioned1 = new ChatMessageMentionedIdentitySet();
Identity application2 = new Identity();
application2.setId("03a02232-d8f5-4970-a77e-6e8c76ce7a4e");
application2.setDisplayName("TestGlobalBot");
HashMap<String, Object> additionalData3 = new HashMap<String, Object>();
additionalData3.put("applicationIdentityType", "bot");
application2.setAdditionalData(additionalData3);
mentioned1.setApplication(application2);
mentioned1.setDevice(null);
mentioned1.setConversation(null);
mentioned1.setUser(null);
chatMessageMention1.setMentioned(mentioned1);
mentions.add(chatMessageMention1);
chatMessage.setMentions(mentions);
LinkedList<ChatMessageReaction> reactions = new LinkedList<ChatMessageReaction>();
chatMessage.setReactions(reactions);
LinkedList<ChatMessageHistoryItem> messageHistory = new LinkedList<ChatMessageHistoryItem>();
chatMessage.setMessageHistory(messageHistory);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().byChatMessageId("{chatMessage-id}").patch(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
  messageType: 'message',
  deletedDateTime: null,
  subject: null,
  summary: null,
  importance: 'normal',
  locale: 'en-us',
  from: {
    application: null,
    device: null,
    conversation: null,
    user: {
      id: '6b3f3c54-d09c-4fdd-b146-9b514a8a4f40',
      displayName: 'Lam Cong',
      userIdentityType: 'aadUser'
    }
  },
  body: {
    contentType: 'html',
    content: '<div><div>\n<div>\n<div>\n<div>\n<div><at id=\"0\">Raghav</at><at id=\"1\">TestGlobalBot</at> YEAH'
  },
  attachments: [],
  mentions: [
    {
      id: 0,
      mentionText: 'Raghav',
      mentioned: {
        application: null,
        device: null,
        conversation: null,
        user: {
          id: 'f1b66449-b46d-49b0-9c3c-53c10234c818e',
          displayName: 'Lam Cong',
          userIdentityType: 'aadUser'
        }
      }
    },
    {
      id: 1,
      mentionText: 'TestGlobalBot',
      mentioned: {
        application: {
          id: '03a02232-d8f5-4970-a77e-6e8c76ce7a4e',
          displayName: 'TestGlobalBot',
          applicationIdentityType: 'bot'
        },
        device: null,
        conversation: null,
        user: null
      }
    }
  ],
  reactions: [],
  messageHistory: []
};

await client.api('/teams/e1234567-e123-4276-55555-6232b0e3a89a/channels/a7654321-e321-0000-0000-123b0e3a00a/messages/19:a21b0b0c05194ebc9e30000000000f61@thread.skype')
	.update(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ChatMessageType;
use Microsoft\Graph\Generated\Models\ChatMessageImportance;
use Microsoft\Graph\Generated\Models\ChatMessageFromIdentitySet;
use Microsoft\Graph\Generated\Models\Identity;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageAttachment;
use Microsoft\Graph\Generated\Models\ChatMessageMention;
use Microsoft\Graph\Generated\Models\ChatMessageMentionedIdentitySet;
use Microsoft\Graph\Generated\Models\ChatMessageReaction;
use Microsoft\Graph\Generated\Models\ChatMessageHistoryItem;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$requestBody->setMessageType(new ChatMessageType('message'));
$requestBody->setDeletedDateTime(null);
$requestBody->setSubject(null);
$requestBody->setSummary(null);
$requestBody->setImportance(new ChatMessageImportance('normal'));
$requestBody->setLocale('en-us');
$from = new ChatMessageFromIdentitySet();
$from->setApplication(null);
$from->setDevice(null);
$fromUser = new Identity();
$fromUser->setId('6b3f3c54-d09c-4fdd-b146-9b514a8a4f40');
$fromUser->setDisplayName('Lam Cong');
$additionalData = [
	'userIdentityType' => 'aadUser',
];
$fromUser->setAdditionalData($additionalData);
$from->setUser($fromUser);
$additionalData = [
	'conversation' => null,
];
$from->setAdditionalData($additionalData);
$requestBody->setFrom($from);
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('<div><div>\n<div>\n<div>\n<div>\n<div><at id=\"0\">Raghav</at><at id=\"1\">TestGlobalBot</at> YEAH');
$requestBody->setBody($body);
$requestBody->setAttachments([	]);
$mentionsChatMessageMention1 = new ChatMessageMention();
$mentionsChatMessageMention1->setId(0);
$mentionsChatMessageMention1->setMentionText('Raghav');
$mentionsChatMessageMention1Mentioned = new ChatMessageMentionedIdentitySet();
$mentionsChatMessageMention1Mentioned->setApplication(null);
$mentionsChatMessageMention1Mentioned->setDevice(null);
$mentionsChatMessageMention1Mentioned->setConversation(null);
$mentionsChatMessageMention1MentionedUser = new Identity();
$mentionsChatMessageMention1MentionedUser->setId('f1b66449-b46d-49b0-9c3c-53c10234c818e');
$mentionsChatMessageMention1MentionedUser->setDisplayName('Lam Cong');
$additionalData = [
	'userIdentityType' => 'aadUser',
];
$mentionsChatMessageMention1MentionedUser->setAdditionalData($additionalData);
$mentionsChatMessageMention1Mentioned->setUser($mentionsChatMessageMention1MentionedUser);
$mentionsChatMessageMention1->setMentioned($mentionsChatMessageMention1Mentioned);
$mentionsArray []= $mentionsChatMessageMention1;
$mentionsChatMessageMention2 = new ChatMessageMention();
$mentionsChatMessageMention2->setId(1);
$mentionsChatMessageMention2->setMentionText('TestGlobalBot');
$mentionsChatMessageMention2Mentioned = new ChatMessageMentionedIdentitySet();
$mentionsChatMessageMention2MentionedApplication = new Identity();
$mentionsChatMessageMention2MentionedApplication->setId('03a02232-d8f5-4970-a77e-6e8c76ce7a4e');
$mentionsChatMessageMention2MentionedApplication->setDisplayName('TestGlobalBot');
$additionalData = [
	'applicationIdentityType' => 'bot',
];
$mentionsChatMessageMention2MentionedApplication->setAdditionalData($additionalData);
$mentionsChatMessageMention2Mentioned->setApplication($mentionsChatMessageMention2MentionedApplication);
$mentionsChatMessageMention2Mentioned->setDevice(null);
$mentionsChatMessageMention2Mentioned->setConversation(null);
$mentionsChatMessageMention2Mentioned->setUser(null);
$mentionsChatMessageMention2->setMentioned($mentionsChatMessageMention2Mentioned);
$mentionsArray []= $mentionsChatMessageMention2;
$requestBody->setMentions($mentionsArray);

$requestBody->setReactions([]);
$requestBody->setMessageHistory([]);

$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->byChatMessageId('chatMessage-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	messageType = "message"
	deletedDateTime = $null
	subject = $null
	summary = $null
	importance = "normal"
	locale = "en-us"
	from = @{
		application = $null
		device = $null
		conversation = $null
		user = @{
			id = "6b3f3c54-d09c-4fdd-b146-9b514a8a4f40"
			displayName = "Lam Cong"
			userIdentityType = "aadUser"
		}
	}
	body = @{
		contentType = "html"
		content = "<div><div>
<div>
<div>
<div>
<div><at id="0">Raghav</at><at id="1">TestGlobalBot</at> YEAH"
	}
	attachments = @(
	)
	mentions = @(
		@{
			id = 0
			mentionText = "Raghav"
			mentioned = @{
				application = $null
				device = $null
				conversation = $null
				user = @{
					id = "f1b66449-b46d-49b0-9c3c-53c10234c818e"
					displayName = "Lam Cong"
					userIdentityType = "aadUser"
				}
			}
		}
		@{
			id = 1
			mentionText = "TestGlobalBot"
			mentioned = @{
				application = @{
					id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
					displayName = "TestGlobalBot"
					applicationIdentityType = "bot"
				}
				device = $null
				conversation = $null
				user = $null
			}
		}
	)
	reactions = @(
	)
	messageHistory = @(
	)
}

Update-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -ChatMessageId $chatMessageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.chat_message_type import ChatMessageType
from msgraph.generated.models.chat_message_importance import ChatMessageImportance
from msgraph.generated.models.chat_message_from_identity_set import ChatMessageFromIdentitySet
from msgraph.generated.models.identity import Identity
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_attachment import ChatMessageAttachment
from msgraph.generated.models.chat_message_mention import ChatMessageMention
from msgraph.generated.models.chat_message_mentioned_identity_set import ChatMessageMentionedIdentitySet
from msgraph.generated.models.chat_message_reaction import ChatMessageReaction
from msgraph.generated.models.chat_message_history_item import ChatMessageHistoryItem
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	message_type = ChatMessageType.Message,
	deleted_date_time = None,
	subject = None,
	summary = None,
	importance = ChatMessageImportance.Normal,
	locale = "en-us",
	from = ChatMessageFromIdentitySet(
		application = None,
		device = None,
		user = Identity(
			id = "6b3f3c54-d09c-4fdd-b146-9b514a8a4f40",
			display_name = "Lam Cong",
			additional_data = {
					"user_identity_type" : "aadUser",
			}
		),
		additional_data = {
				"conversation" : None,
		}
	),
	body = ItemBody(
		content_type = BodyType.Html,
		content = "<div><div>\n<div>\n<div>\n<div>\n<div><at id=\"0\">Raghav</at><at id=\"1\">TestGlobalBot</at> YEAH",
	),
	attachments = [
	],
	mentions = [
		ChatMessageMention(
			id = 0,
			mention_text = "Raghav",
			mentioned = ChatMessageMentionedIdentitySet(
				application = None,
				device = None,
				conversation = None,
				user = Identity(
					id = "f1b66449-b46d-49b0-9c3c-53c10234c818e",
					display_name = "Lam Cong",
					additional_data = {
							"user_identity_type" : "aadUser",
					}
				),
			),
		),
		ChatMessageMention(
			id = 1,
			mention_text = "TestGlobalBot",
			mentioned = ChatMessageMentionedIdentitySet(
				application = Identity(
					id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
					display_name = "TestGlobalBot",
					additional_data = {
							"application_identity_type" : "bot",
					}
				),
				device = None,
				conversation = None,
				user = None,
			),
		),
	],
	reactions = [
	],
	message_history = [
	],
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.by_chat_message_id('chatMessage-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 4: Update the content with attachments of a message using delegated permissions

#### Request

The following example shows a request to update the attachments on a Microsoft Teams channel message by using delegated permissions.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
PATCH https://graph.microsoft.com/v1.0/teams/e1234567-e123-4276-55555-6232b0e3a89a/channels/a7654321-e321-0000-0000-123b0e3a00a/messages/19%3Aa21b0b0c05194ebc9e30000000000f61%40thread.skype
Content-Type: application/json

{
  "messageType": "message",
  "subject": null,
  "summary": null,
  "importance": "normal",
  "locale": "en-us",
  "from": {
    "application": null,
    "device": null,
    "user": {
      "id": "3b102402-813e-4e17-a6b2-f841aef1fdfc",
      "displayName": "Lam Cong",
      "userIdentityType": "aadUser"
    },
    "conversation": null
  },
  "body": {
    "contentType": "html",
    "content": "<p><em>text</em></p><attachment id=\"e8f78756199240b88448ae0fc6db112d\"></attachment><attachment id=\"638464e32834471ea202007da60a5ae6\"></attachment>"
  },
  "attachments": [
    {
      "id": "e8f78756199240b88448ae0fc6db112d",
      "contentType": "application/vnd.microsoft.card.hero",
      "contentUrl": null,
      "content": "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"image\": \"https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png\",\r\n      \"title\": \"😃😃 click me 😃😃\",\r\n      \"value\": \"http://microsoft.com\"\r\n    },\r\n    {\r\n      \"type\": \"imback\",\r\n      \"title\": \"&i am back& <>= \\\"\",\r\n      \"value\": \"&i am back& <>= \\\"\"\r\n    },\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"title\": \"Open URL\",\r\n      \"value\": \"http://google.com\"\r\n    }\r\n  ]\r\n}",
      "name": null,
      "thumbnailUrl": null
    },
    {
      "id": "638464e32834471ea202007da60a5ae6",
      "contentType": "application/vnd.microsoft.card.hero",
      "contentUrl": null,
      "content": "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"&message back& <>= \\\"\",\r\n      \"text\": \"text = &message back& <>= \\\"\",\r\n      \"displayText\": \"displayText = &message back& <>= \\\"\",\r\n      \"value\": {\r\n        \"text\": \"some text 2\"\r\n      }\r\n    }\r\n  ]\r\n}",
      "name": null,
      "thumbnailUrl": null
    }
  ],
  "mentions": [],
  "reactions": [],
  "messageHistory": []
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ChatMessage
{
	MessageType = ChatMessageType.Message,
	Subject = null,
	Summary = null,
	Importance = ChatMessageImportance.Normal,
	Locale = "en-us",
	From = new ChatMessageFromIdentitySet
	{
		Application = null,
		Device = null,
		User = new Identity
		{
			Id = "3b102402-813e-4e17-a6b2-f841aef1fdfc",
			DisplayName = "Lam Cong",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"userIdentityType" , "aadUser"
				},
			},
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"conversation" , null
			},
		},
	},
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "<p><em>text</em></p><attachment id=\"e8f78756199240b88448ae0fc6db112d\"></attachment><attachment id=\"638464e32834471ea202007da60a5ae6\"></attachment>",
	},
	Attachments = new List<ChatMessageAttachment>
	{
		new ChatMessageAttachment
		{
			Id = "e8f78756199240b88448ae0fc6db112d",
			ContentType = "application/vnd.microsoft.card.hero",
			ContentUrl = null,
			Content = "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"image\": \"https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png\",\r\n      \"title\": \"😃😃 click me 😃😃\",\r\n      \"value\": \"http://microsoft.com\"\r\n    },\r\n    {\r\n      \"type\": \"imback\",\r\n      \"title\": \"&i am back& <>= \"\",\r\n      \"value\": \"&i am back& <>= \"\"\r\n    },\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"title\": \"Open URL\",\r\n      \"value\": \"http://google.com\"\r\n    }\r\n  ]\r\n}",
			Name = null,
			ThumbnailUrl = null,
		},
		new ChatMessageAttachment
		{
			Id = "638464e32834471ea202007da60a5ae6",
			ContentType = "application/vnd.microsoft.card.hero",
			ContentUrl = null,
			Content = "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"&message back& <>= \"\",\r\n      \"text\": \"text = &message back& <>= \"\",\r\n      \"displayText\": \"displayText = &message back& <>= \"\",\r\n      \"value\": {\r\n        \"text\": \"some text 2\"\r\n      }\r\n    }\r\n  ]\r\n}",
			Name = null,
			ThumbnailUrl = null,
		},
	},
	Mentions = new List<ChatMessageMention>
	{
	},
	Reactions = new List<ChatMessageReaction>
	{
	},
	MessageHistory = new List<ChatMessageHistoryItem>
	{
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages["{chatMessage-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewChatMessage()
messageType := graphmodels.MESSAGE_CHATMESSAGETYPE 
requestBody.SetMessageType(&messageType) 
subject := null
requestBody.SetSubject(&subject) 
summary := null
requestBody.SetSummary(&summary) 
importance := graphmodels.NORMAL_CHATMESSAGEIMPORTANCE 
requestBody.SetImportance(&importance) 
locale := "en-us"
requestBody.SetLocale(&locale) 
from := graphmodels.NewChatMessageFromIdentitySet()
application := null
from.SetApplication(&application) 
device := null
from.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "3b102402-813e-4e17-a6b2-f841aef1fdfc"
user.SetId(&id) 
displayName := "Lam Cong"
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
from.SetUser(user)
additionalData := map[string]interface{}{
	conversation := null
from.SetConversation(&conversation) 
}
from.SetAdditionalData(additionalData)
requestBody.SetFrom(from)
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "<p><em>text</em></p><attachment id=\"e8f78756199240b88448ae0fc6db112d\"></attachment><attachment id=\"638464e32834471ea202007da60a5ae6\"></attachment>"
body.SetContent(&content) 
requestBody.SetBody(body)


chatMessageAttachment := graphmodels.NewChatMessageAttachment()
id := "e8f78756199240b88448ae0fc6db112d"
chatMessageAttachment.SetId(&id) 
contentType := "application/vnd.microsoft.card.hero"
chatMessageAttachment.SetContentType(&contentType) 
contentUrl := null
chatMessageAttachment.SetContentUrl(&contentUrl) 
content := "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"image\": \"https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png\",\r\n      \"title\": \"😃😃 click me 😃😃\",\r\n      \"value\": \"http://microsoft.com\"\r\n    },\r\n    {\r\n      \"type\": \"imback\",\r\n      \"title\": \"&i am back& <>= \"\",\r\n      \"value\": \"&i am back& <>= \"\"\r\n    },\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"title\": \"Open URL\",\r\n      \"value\": \"http://google.com\"\r\n    }\r\n  ]\r\n}"
chatMessageAttachment.SetContent(&content) 
name := null
chatMessageAttachment.SetName(&name) 
thumbnailUrl := null
chatMessageAttachment.SetThumbnailUrl(&thumbnailUrl) 
chatMessageAttachment1 := graphmodels.NewChatMessageAttachment()
id := "638464e32834471ea202007da60a5ae6"
chatMessageAttachment1.SetId(&id) 
contentType := "application/vnd.microsoft.card.hero"
chatMessageAttachment1.SetContentType(&contentType) 
contentUrl := null
chatMessageAttachment1.SetContentUrl(&contentUrl) 
content := "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"&message back& <>= \"\",\r\n      \"text\": \"text = &message back& <>= \"\",\r\n      \"displayText\": \"displayText = &message back& <>= \"\",\r\n      \"value\": {\r\n        \"text\": \"some text 2\"\r\n      }\r\n    }\r\n  ]\r\n}"
chatMessageAttachment1.SetContent(&content) 
name := null
chatMessageAttachment1.SetName(&name) 
thumbnailUrl := null
chatMessageAttachment1.SetThumbnailUrl(&thumbnailUrl) 

attachments := []graphmodels.ChatMessageAttachmentable {
	chatMessageAttachment,
	chatMessageAttachment1,
}
requestBody.SetAttachments(attachments)
mentions := []graphmodels.ChatMessageMentionable {

}
requestBody.SetMentions(mentions)
reactions := []graphmodels.ChatMessageReactionable {

}
requestBody.SetReactions(reactions)
messageHistory := []graphmodels.ChatMessageHistoryItemable {

}
requestBody.SetMessageHistory(messageHistory)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().ByChatMessageId("chatMessage-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
chatMessage.setMessageType(ChatMessageType.Message);
chatMessage.setSubject(null);
chatMessage.setSummary(null);
chatMessage.setImportance(ChatMessageImportance.Normal);
chatMessage.setLocale("en-us");
ChatMessageFromIdentitySet from = new ChatMessageFromIdentitySet();
from.setApplication(null);
from.setDevice(null);
Identity user = new Identity();
user.setId("3b102402-813e-4e17-a6b2-f841aef1fdfc");
user.setDisplayName("Lam Cong");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("userIdentityType", "aadUser");
user.setAdditionalData(additionalData);
from.setUser(user);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("conversation", null);
from.setAdditionalData(additionalData1);
chatMessage.setFrom(from);
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("<p><em>text</em></p><attachment id=\"e8f78756199240b88448ae0fc6db112d\"></attachment><attachment id=\"638464e32834471ea202007da60a5ae6\"></attachment>");
chatMessage.setBody(body);
LinkedList<ChatMessageAttachment> attachments = new LinkedList<ChatMessageAttachment>();
ChatMessageAttachment chatMessageAttachment = new ChatMessageAttachment();
chatMessageAttachment.setId("e8f78756199240b88448ae0fc6db112d");
chatMessageAttachment.setContentType("application/vnd.microsoft.card.hero");
chatMessageAttachment.setContentUrl(null);
chatMessageAttachment.setContent("{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"image\": \"https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png\",\r\n      \"title\": \"😃😃 click me 😃😃\",\r\n      \"value\": \"http://microsoft.com\"\r\n    },\r\n    {\r\n      \"type\": \"imback\",\r\n      \"title\": \"&i am back& <>= \"\",\r\n      \"value\": \"&i am back& <>= \"\"\r\n    },\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"title\": \"Open URL\",\r\n      \"value\": \"http://google.com\"\r\n    }\r\n  ]\r\n}");
chatMessageAttachment.setName(null);
chatMessageAttachment.setThumbnailUrl(null);
attachments.add(chatMessageAttachment);
ChatMessageAttachment chatMessageAttachment1 = new ChatMessageAttachment();
chatMessageAttachment1.setId("638464e32834471ea202007da60a5ae6");
chatMessageAttachment1.setContentType("application/vnd.microsoft.card.hero");
chatMessageAttachment1.setContentUrl(null);
chatMessageAttachment1.setContent("{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"&message back& <>= \"\",\r\n      \"text\": \"text = &message back& <>= \"\",\r\n      \"displayText\": \"displayText = &message back& <>= \"\",\r\n      \"value\": {\r\n        \"text\": \"some text 2\"\r\n      }\r\n    }\r\n  ]\r\n}");
chatMessageAttachment1.setName(null);
chatMessageAttachment1.setThumbnailUrl(null);
attachments.add(chatMessageAttachment1);
chatMessage.setAttachments(attachments);
LinkedList<ChatMessageMention> mentions = new LinkedList<ChatMessageMention>();
chatMessage.setMentions(mentions);
LinkedList<ChatMessageReaction> reactions = new LinkedList<ChatMessageReaction>();
chatMessage.setReactions(reactions);
LinkedList<ChatMessageHistoryItem> messageHistory = new LinkedList<ChatMessageHistoryItem>();
chatMessage.setMessageHistory(messageHistory);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().byChatMessageId("{chatMessage-id}").patch(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
  messageType: 'message',
  subject: null,
  summary: null,
  importance: 'normal',
  locale: 'en-us',
  from: {
    application: null,
    device: null,
    user: {
      id: '3b102402-813e-4e17-a6b2-f841aef1fdfc',
      displayName: 'Lam Cong',
      userIdentityType: 'aadUser'
    },
    conversation: null
  },
  body: {
    contentType: 'html',
    content: '<p><em>text</em></p><attachment id=\"e8f78756199240b88448ae0fc6db112d\"></attachment><attachment id=\"638464e32834471ea202007da60a5ae6\"></attachment>'
  },
  attachments: [
    {
      id: 'e8f78756199240b88448ae0fc6db112d',
      contentType: 'application/vnd.microsoft.card.hero',
      contentUrl: null,
      content: '{\r\n  \"title\': \'*title*\",\r\n  \"subtitle\': \'*subtitle*\",\r\n  \"text\': \'Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you\'re cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\': [\r\n    {\r\n      \'url\': \'https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\': [\r\n    {\r\n      \'type\': \'openUrl\",\r\n      \"image\': \'https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png\",\r\n      \"title\': \'😃😃 click me 😃😃\",\r\n      \"value\': \'http://microsoft.com\"\r\n    },\r\n    {\r\n      \"type\': \'imback\",\r\n      \"title\': \'&i am back& <>= \\\"\",\r\n      \"value\': \'&i am back& <>= \\\"\"\r\n    },\r\n    {\r\n      \"type\': \'openUrl\",\r\n      \"title\': \'Open URL\",\r\n      \"value\': \"http://google.com\"\r\n    }\r\n  ]\r\n}",
      name: null,
      thumbnailUrl: null
    },
    {
      id: '638464e32834471ea202007da60a5ae6',
      contentType: 'application/vnd.microsoft.card.hero',
      contentUrl: null,
      content: '{\r\n  \"title\': \'*title*\",\r\n  \"subtitle\': \'*subtitle*\",\r\n  \"text\': \'Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you\'re cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\': [\r\n    {\r\n      \'url\': \'https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\': [\r\n    {\r\n      \'type\': \'messageBack\",\r\n      \"title\': \'&message back& <>= \\\"\",\r\n      \"text\': \'text = &message back& <>= \\\"\",\r\n      \"displayText\': \'displayText = &message back& <>= \\\"\",\r\n      \"value\': {\r\n        \'text\': \"some text 2\"\r\n      }\r\n    }\r\n  ]\r\n}",
      name: null,
      thumbnailUrl: null
    }
  ],
  mentions: [],
  reactions: [],
  messageHistory: []
};

await client.api('/teams/e1234567-e123-4276-55555-6232b0e3a89a/channels/a7654321-e321-0000-0000-123b0e3a00a/messages/19:a21b0b0c05194ebc9e30000000000f61@thread.skype')
	.update(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ChatMessageType;
use Microsoft\Graph\Generated\Models\ChatMessageImportance;
use Microsoft\Graph\Generated\Models\ChatMessageFromIdentitySet;
use Microsoft\Graph\Generated\Models\Identity;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageAttachment;
use Microsoft\Graph\Generated\Models\ChatMessageMention;
use Microsoft\Graph\Generated\Models\ChatMessageReaction;
use Microsoft\Graph\Generated\Models\ChatMessageHistoryItem;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$requestBody->setMessageType(new ChatMessageType('message'));
$requestBody->setSubject(null);
$requestBody->setSummary(null);
$requestBody->setImportance(new ChatMessageImportance('normal'));
$requestBody->setLocale('en-us');
$from = new ChatMessageFromIdentitySet();
$from->setApplication(null);
$from->setDevice(null);
$fromUser = new Identity();
$fromUser->setId('3b102402-813e-4e17-a6b2-f841aef1fdfc');
$fromUser->setDisplayName('Lam Cong');
$additionalData = [
	'userIdentityType' => 'aadUser',
];
$fromUser->setAdditionalData($additionalData);
$from->setUser($fromUser);
$additionalData = [
	'conversation' => null,
];
$from->setAdditionalData($additionalData);
$requestBody->setFrom($from);
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('<p><em>text</em></p><attachment id=\"e8f78756199240b88448ae0fc6db112d\"></attachment><attachment id=\"638464e32834471ea202007da60a5ae6\"></attachment>');
$requestBody->setBody($body);
$attachmentsChatMessageAttachment1 = new ChatMessageAttachment();
$attachmentsChatMessageAttachment1->setId('e8f78756199240b88448ae0fc6db112d');
$attachmentsChatMessageAttachment1->setContentType('application/vnd.microsoft.card.hero');
$attachmentsChatMessageAttachment1->setContentUrl(null);
$attachmentsChatMessageAttachment1->setContent('{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you\'re cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"image\": \"https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png\",\r\n      \"title\": \"😃😃 click me 😃😃\",\r\n      \"value\": \"http://microsoft.com\"\r\n    },\r\n    {\r\n      \"type\": \"imback\",\r\n      \"title\": \"&i am back& <>= \"\",\r\n      \"value\": \"&i am back& <>= \"\"\r\n    },\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"title\": \"Open URL\",\r\n      \"value\": \"http://google.com\"\r\n    }\r\n  ]\r\n}');
$attachmentsChatMessageAttachment1->setName(null);
$attachmentsChatMessageAttachment1->setThumbnailUrl(null);
$attachmentsArray []= $attachmentsChatMessageAttachment1;
$attachmentsChatMessageAttachment2 = new ChatMessageAttachment();
$attachmentsChatMessageAttachment2->setId('638464e32834471ea202007da60a5ae6');
$attachmentsChatMessageAttachment2->setContentType('application/vnd.microsoft.card.hero');
$attachmentsChatMessageAttachment2->setContentUrl(null);
$attachmentsChatMessageAttachment2->setContent('{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you\'re cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"&message back& <>= \"\",\r\n      \"text\": \"text = &message back& <>= \"\",\r\n      \"displayText\": \"displayText = &message back& <>= \"\",\r\n      \"value\": {\r\n        \"text\": \"some text 2\"\r\n      }\r\n    }\r\n  ]\r\n}');
$attachmentsChatMessageAttachment2->setName(null);
$attachmentsChatMessageAttachment2->setThumbnailUrl(null);
$attachmentsArray []= $attachmentsChatMessageAttachment2;
$requestBody->setAttachments($attachmentsArray);

$requestBody->setMentions([]);
$requestBody->setReactions([]);
$requestBody->setMessageHistory([]);

$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->byChatMessageId('chatMessage-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	messageType = "message"
	subject = $null
	summary = $null
	importance = "normal"
	locale = "en-us"
	from = @{
		application = $null
		device = $null
		user = @{
			id = "3b102402-813e-4e17-a6b2-f841aef1fdfc"
			displayName = "Lam Cong"
			userIdentityType = "aadUser"
		}
		conversation = $null
	}
	body = @{
		contentType = "html"
		content = "<p><em>text</em></p><attachment id="e8f78756199240b88448ae0fc6db112d"></attachment><attachment id="638464e32834471ea202007da60a5ae6"></attachment>"
	}
	attachments = @(
		@{
			id = "e8f78756199240b88448ae0fc6db112d"
			contentType = "application/vnd.microsoft.card.hero"
			contentUrl = $null
			content = '{
  "title": "*title*",
  "subtitle": "*subtitle*",
  "text": "Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.",
  "images": [
    {
      "url": "https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview"
    }
  ],
  "buttons": [
    {
      "type": "openUrl",
      "image": "https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png",
      "title": "😃😃 click me 😃😃",
      "value": "http://microsoft.com"
    },
    {
      "type": "imback",
      "title": "&i am back& <>= \"",
      "value": "&i am back& <>= \""
    },
    {
      "type": "openUrl",
      "title": "Open URL",
      "value": "http://google.com"
    }
  ]
}'
			name = $null
			thumbnailUrl = $null
		}
		@{
			id = "638464e32834471ea202007da60a5ae6"
			contentType = "application/vnd.microsoft.card.hero"
			contentUrl = $null
			content = '{
  "title": "*title*",
  "subtitle": "*subtitle*",
  "text": "Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.",
  "images": [
    {
      "url": "https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview"
    }
  ],
  "buttons": [
    {
      "type": "messageBack",
      "title": "&message back& <>= \"",
      "text": "text = &message back& <>= \"",
      "displayText": "displayText = &message back& <>= \"",
      "value": {
        "text": "some text 2"
      }
    }
  ]
}'
			name = $null
			thumbnailUrl = $null
		}
	)
	mentions = @(
	)
	reactions = @(
	)
	messageHistory = @(
	)
}

Update-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -ChatMessageId $chatMessageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.chat_message_type import ChatMessageType
from msgraph.generated.models.chat_message_importance import ChatMessageImportance
from msgraph.generated.models.chat_message_from_identity_set import ChatMessageFromIdentitySet
from msgraph.generated.models.identity import Identity
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_attachment import ChatMessageAttachment
from msgraph.generated.models.chat_message_mention import ChatMessageMention
from msgraph.generated.models.chat_message_reaction import ChatMessageReaction
from msgraph.generated.models.chat_message_history_item import ChatMessageHistoryItem
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	message_type = ChatMessageType.Message,
	subject = None,
	summary = None,
	importance = ChatMessageImportance.Normal,
	locale = "en-us",
	from = ChatMessageFromIdentitySet(
		application = None,
		device = None,
		user = Identity(
			id = "3b102402-813e-4e17-a6b2-f841aef1fdfc",
			display_name = "Lam Cong",
			additional_data = {
					"user_identity_type" : "aadUser",
			}
		),
		additional_data = {
				"conversation" : None,
		}
	),
	body = ItemBody(
		content_type = BodyType.Html,
		content = "<p><em>text</em></p><attachment id=\"e8f78756199240b88448ae0fc6db112d\"></attachment><attachment id=\"638464e32834471ea202007da60a5ae6\"></attachment>",
	),
	attachments = [
		ChatMessageAttachment(
			id = "e8f78756199240b88448ae0fc6db112d",
			content_type = "application/vnd.microsoft.card.hero",
			content_url = None,
			content = "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"image\": \"https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png\",\r\n      \"title\": \"😃😃 click me 😃😃\",\r\n      \"value\": \"http://microsoft.com\"\r\n    },\r\n    {\r\n      \"type\": \"imback\",\r\n      \"title\": \"&i am back& <>= \"\",\r\n      \"value\": \"&i am back& <>= \"\"\r\n    },\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"title\": \"Open URL\",\r\n      \"value\": \"http://google.com\"\r\n    }\r\n  ]\r\n}",
			name = None,
			thumbnail_url = None,
		),
		ChatMessageAttachment(
			id = "638464e32834471ea202007da60a5ae6",
			content_type = "application/vnd.microsoft.card.hero",
			content_url = None,
			content = "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"&message back& <>= \"\",\r\n      \"text\": \"text = &message back& <>= \"\",\r\n      \"displayText\": \"displayText = &message back& <>= \"\",\r\n      \"value\": {\r\n        \"text\": \"some text 2\"\r\n      }\r\n    }\r\n  ]\r\n}",
			name = None,
			thumbnail_url = None,
		),
	],
	mentions = [
	],
	reactions = [
	],
	message_history = [
	],
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.by_chat_message_id('chatMessage-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 5: Update the reactions in a message using delegated permissions

#### Request

The following example shows a request to update the reactions property on a Microsoft Teams channel message by using delegated permissions.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
PATCH https://graph.microsoft.com/v1.0/teams/e1234567-e123-4276-55555-6232b0e3a89a/channels/a7654321-e321-0000-0000-123b0e3a00a/messages/19%3Aa21b0b0c05194ebc9e30000000000f61%40thread.skype
Content-Type: application/json

{
  "messageType": "message",
  "subject": null,
  "summary": null,
  "importance": "normal",
  "locale": "en-us",
  "from": {
    "application": null,
    "device": null,
    "user": {
      "id": "3b102402-813e-4e17-a6b2-f841aef1fdfc",
      "displayName": "Lam Cong",
      "userIdentityType": "aadUser"
    },
    "conversation": null
  },
  "body": {
    "contentType": "html",
    "content": "<p><em>text</em></p><attachment id=\"e8f78756199240b88448ae0fc6db112d\"></attachment><attachment id=\"638464e32834471ea202007da60a5ae6\"></attachment>"
  },
  "attachments": [
    {
      "id": "e8f78756199240b88448ae0fc6db112d",
      "contentType": "application/vnd.microsoft.card.hero",
      "contentUrl": null,
      "content": "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"image\": \"https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png\",\r\n      \"title\": \"😃😃 click me 😃😃\",\r\n      \"value\": \"http://microsoft.com\"\r\n    },\r\n    {\r\n      \"type\": \"imback\",\r\n      \"title\": \"&i am back& <>= \\\"\",\r\n      \"value\": \"&i am back& <>= \\\"\"\r\n    },\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"title\": \"Open URL\",\r\n      \"value\": \"http://google.com\"\r\n    }\r\n  ]\r\n}",
      "name": null,
      "thumbnailUrl": null
    },
    {
      "id": "638464e32834471ea202007da60a5ae6",
      "contentType": "application/vnd.microsoft.card.hero",
      "contentUrl": null,
      "content": "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"&message back& <>= \\\"\",\r\n      \"text\": \"text = &message back& <>= \\\"\",\r\n      \"displayText\": \"displayText = &message back& <>= \\\"\",\r\n      \"value\": {\r\n        \"text\": \"some text 2\"\r\n      }\r\n    }\r\n  ]\r\n}",
      "name": null,
      "thumbnailUrl": null
    }
  ],
  "mentions": [],
  "reactions": [
    {
      "reactionType": "angry",
      "createdDateTime": "2018-10-21T08:10:30.489Z",
      "user": {
        "application": null,
        "device": null,
        "user": {
          "id": "f1b66449-b46d-49b0-9c3c-53c10a5c818e",
          "displayName": null,
          "userIdentityType": "aadUser"
        }
      }
    },
    {
      "reactionType": "laugh",
      "createdDateTime": "2018-10-21T08:10:32.489Z",
      "user": {
        "application": null,
        "device": null,
        "user": {
          "id": "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
          "displayName": null,
          "userIdentityType": "aadUser"
        }
      }
    },
    {
      "reactionType": "like",
      "createdDateTime": "2018-10-21T02:17:14.67Z",
      "user": {
        "application": null,
        "device": null,
        "user": {
          "id": "f1b66449-b46d-49b0-9c3c-53c10a5c818e",
          "displayName": null,
          "userIdentityType": "aadUser"
        }
      }
    },
    {
      "reactionType": "like",
      "createdDateTime": "2018-10-21T02:34:40.3Z",
      "user": {
        "application": null,
        "device": null,
        "user": {
          "id": "4c9041b7-449a-40f7-8855-56da239b9fd1",
          "displayName": null,
          "userIdentityType": "aadUser"
        }
      }
    },
    {
      "reactionType": "like",
      "createdDateTime": "2018-10-21T08:10:25.489Z",
      "user": {
        "application": null,
        "device": null,
        "user": {
          "id": "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
          "displayName": null,
          "userIdentityType": "aadUser"
        }
      }
    },
    {
      "reactionType": "heart",
      "createdDateTime": "2018-10-21T08:10:31.489Z",
      "user": {
        "application": null,
        "device": null,
        "user": {
          "id": "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
          "displayName": null,
          "userIdentityType": "aadUser"
        }
      }
    },
    {
      "reactionType": "sad",
      "createdDateTime": "2018-10-21T08:10:33.489Z",
      "user": {
        "application": null,
        "device": null,
        "user": {
          "id": "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
          "displayName": null,
          "userIdentityType": "aadUser"
        }
      }
    },
    {
      "reactionType": "surprised",
      "createdDateTime": "2018-10-21T08:10:34.489Z",
      "user": {
        "application": null,
        "device": null,
        "user": {
          "id": "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
          "displayName": null,
          "userIdentityType": "aadUser"
        }
      }
    }
  ],
  "messageHistory": [
    {
      "modifiedDateTime": "2018-10-21T08:10:30.489Z",
      "actions": "reactionAdded",
      "reaction": {
        "reactionType": "angry",
        "user": {
          "application": null,
          "device": null,
          "user": {
            "id": "f1b66449-b46d-49b0-9c3c-53c10a5c818e",
            "displayName": null,
            "userIdentityType": "aadUser"
          }
        }
      }
    },
    {
      "modifiedDateTime": "2018-10-21T08:10:32.489Z",
      "actions": "reactionAdded",
      "reaction": {
        "reactionType": "laugh",
        "user": {
          "application": null,
          "device": null,
          "user": {
            "id": "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
            "displayName": null,
            "userIdentityType": "aadUser"
          }
        }
      }
    },
    {
      "modifiedDateTime": "2018-10-21T02:17:14.67Z",
      "actions": "reactionAdded",
      "reaction": {
        "reactionType": "like",
        "user": {
          "application": null,
          "device": null,
          "user": {
            "id": "f1b66449-b46d-49b0-9c3c-53c10a5c818e",
            "displayName": null,
            "userIdentityType": "aadUser"
          }
        }
      }
    },
    {
      "modifiedDateTime": "2018-10-21T02:34:40.3Z",
      "actions": "reactionAdded",
      "reaction": {
        "reactionType": "like",
        "user": {
          "application": null,
          "device": null,
          "user": {
            "id": "4c9041b7-449a-40f7-8855-56da239b9fd1",
            "displayName": null,
            "userIdentityType": "aadUser"
          }
        }
      }
    },
    {
      "modifiedDateTime": "2018-10-21T08:10:25.489Z",
      "actions": "reactionAdded",
      "reaction": {
        "reactionType": "like",
        "user": {
          "application": null,
          "device": null,
          "user": {
            "id": "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
            "displayName": null,
            "userIdentityType": "aadUser"
          }
        }
      }
    },
    {
      "modifiedDateTime": "2018-10-21T08:10:31.489Z",
      "actions": "reactionAdded",
      "reaction": {
        "reactionType": "heart",
        "user": {
          "application": null,
          "device": null,
          "user": {
            "id": "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
            "displayName": null,
            "userIdentityType": "aadUser"
          }
        }
      }
    },
    {
      "modifiedDateTime": "2018-10-21T08:10:33.489Z",
      "actions": "reactionAdded",
      "reaction": {
        "reactionType": "sad",
        "user": {
          "application": null,
          "device": null,
          "user": {
            "id": "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
            "displayName": null,
            "userIdentityType": "aadUser"
          }
        }
      }
    },
    {
      "modifiedDateTime": "2018-10-21T08:10:34.489Z",
      "actions": "surprised",
      "reaction": {
        "reactionType": "sad",
        "user": {
          "application": null,
          "device": null,
          "user": {
            "id": "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
            "displayName": null,
            "userIdentityType": "aadUser"
          }
        }
      }
    }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ChatMessage
{
	MessageType = ChatMessageType.Message,
	Subject = null,
	Summary = null,
	Importance = ChatMessageImportance.Normal,
	Locale = "en-us",
	From = new ChatMessageFromIdentitySet
	{
		Application = null,
		Device = null,
		User = new Identity
		{
			Id = "3b102402-813e-4e17-a6b2-f841aef1fdfc",
			DisplayName = "Lam Cong",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"userIdentityType" , "aadUser"
				},
			},
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"conversation" , null
			},
		},
	},
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "<p><em>text</em></p><attachment id=\"e8f78756199240b88448ae0fc6db112d\"></attachment><attachment id=\"638464e32834471ea202007da60a5ae6\"></attachment>",
	},
	Attachments = new List<ChatMessageAttachment>
	{
		new ChatMessageAttachment
		{
			Id = "e8f78756199240b88448ae0fc6db112d",
			ContentType = "application/vnd.microsoft.card.hero",
			ContentUrl = null,
			Content = "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"image\": \"https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png\",\r\n      \"title\": \"😃😃 click me 😃😃\",\r\n      \"value\": \"http://microsoft.com\"\r\n    },\r\n    {\r\n      \"type\": \"imback\",\r\n      \"title\": \"&i am back& <>= \"\",\r\n      \"value\": \"&i am back& <>= \"\"\r\n    },\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"title\": \"Open URL\",\r\n      \"value\": \"http://google.com\"\r\n    }\r\n  ]\r\n}",
			Name = null,
			ThumbnailUrl = null,
		},
		new ChatMessageAttachment
		{
			Id = "638464e32834471ea202007da60a5ae6",
			ContentType = "application/vnd.microsoft.card.hero",
			ContentUrl = null,
			Content = "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"&message back& <>= \"\",\r\n      \"text\": \"text = &message back& <>= \"\",\r\n      \"displayText\": \"displayText = &message back& <>= \"\",\r\n      \"value\": {\r\n        \"text\": \"some text 2\"\r\n      }\r\n    }\r\n  ]\r\n}",
			Name = null,
			ThumbnailUrl = null,
		},
	},
	Mentions = new List<ChatMessageMention>
	{
	},
	Reactions = new List<ChatMessageReaction>
	{
		new ChatMessageReaction
		{
			ReactionType = "angry",
			CreatedDateTime = DateTimeOffset.Parse("2018-10-21T08:10:30.489Z"),
			User = new ChatMessageReactionIdentitySet
			{
				Application = null,
				Device = null,
				User = new Identity
				{
					Id = "f1b66449-b46d-49b0-9c3c-53c10a5c818e",
					DisplayName = null,
					AdditionalData = new Dictionary<string, object>
					{
						{
							"userIdentityType" , "aadUser"
						},
					},
				},
			},
		},
		new ChatMessageReaction
		{
			ReactionType = "laugh",
			CreatedDateTime = DateTimeOffset.Parse("2018-10-21T08:10:32.489Z"),
			User = new ChatMessageReactionIdentitySet
			{
				Application = null,
				Device = null,
				User = new Identity
				{
					Id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
					DisplayName = null,
					AdditionalData = new Dictionary<string, object>
					{
						{
							"userIdentityType" , "aadUser"
						},
					},
				},
			},
		},
		new ChatMessageReaction
		{
			ReactionType = "like",
			CreatedDateTime = DateTimeOffset.Parse("2018-10-21T02:17:14.67Z"),
			User = new ChatMessageReactionIdentitySet
			{
				Application = null,
				Device = null,
				User = new Identity
				{
					Id = "f1b66449-b46d-49b0-9c3c-53c10a5c818e",
					DisplayName = null,
					AdditionalData = new Dictionary<string, object>
					{
						{
							"userIdentityType" , "aadUser"
						},
					},
				},
			},
		},
		new ChatMessageReaction
		{
			ReactionType = "like",
			CreatedDateTime = DateTimeOffset.Parse("2018-10-21T02:34:40.3Z"),
			User = new ChatMessageReactionIdentitySet
			{
				Application = null,
				Device = null,
				User = new Identity
				{
					Id = "4c9041b7-449a-40f7-8855-56da239b9fd1",
					DisplayName = null,
					AdditionalData = new Dictionary<string, object>
					{
						{
							"userIdentityType" , "aadUser"
						},
					},
				},
			},
		},
		new ChatMessageReaction
		{
			ReactionType = "like",
			CreatedDateTime = DateTimeOffset.Parse("2018-10-21T08:10:25.489Z"),
			User = new ChatMessageReactionIdentitySet
			{
				Application = null,
				Device = null,
				User = new Identity
				{
					Id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
					DisplayName = null,
					AdditionalData = new Dictionary<string, object>
					{
						{
							"userIdentityType" , "aadUser"
						},
					},
				},
			},
		},
		new ChatMessageReaction
		{
			ReactionType = "heart",
			CreatedDateTime = DateTimeOffset.Parse("2018-10-21T08:10:31.489Z"),
			User = new ChatMessageReactionIdentitySet
			{
				Application = null,
				Device = null,
				User = new Identity
				{
					Id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
					DisplayName = null,
					AdditionalData = new Dictionary<string, object>
					{
						{
							"userIdentityType" , "aadUser"
						},
					},
				},
			},
		},
		new ChatMessageReaction
		{
			ReactionType = "sad",
			CreatedDateTime = DateTimeOffset.Parse("2018-10-21T08:10:33.489Z"),
			User = new ChatMessageReactionIdentitySet
			{
				Application = null,
				Device = null,
				User = new Identity
				{
					Id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
					DisplayName = null,
					AdditionalData = new Dictionary<string, object>
					{
						{
							"userIdentityType" , "aadUser"
						},
					},
				},
			},
		},
		new ChatMessageReaction
		{
			ReactionType = "surprised",
			CreatedDateTime = DateTimeOffset.Parse("2018-10-21T08:10:34.489Z"),
			User = new ChatMessageReactionIdentitySet
			{
				Application = null,
				Device = null,
				User = new Identity
				{
					Id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
					DisplayName = null,
					AdditionalData = new Dictionary<string, object>
					{
						{
							"userIdentityType" , "aadUser"
						},
					},
				},
			},
		},
	},
	MessageHistory = new List<ChatMessageHistoryItem>
	{
		new ChatMessageHistoryItem
		{
			ModifiedDateTime = DateTimeOffset.Parse("2018-10-21T08:10:30.489Z"),
			Actions = ChatMessageActions.ReactionAdded,
			Reaction = new ChatMessageReaction
			{
				ReactionType = "angry",
				User = new ChatMessageReactionIdentitySet
				{
					Application = null,
					Device = null,
					User = new Identity
					{
						Id = "f1b66449-b46d-49b0-9c3c-53c10a5c818e",
						DisplayName = null,
						AdditionalData = new Dictionary<string, object>
						{
							{
								"userIdentityType" , "aadUser"
							},
						},
					},
				},
			},
		},
		new ChatMessageHistoryItem
		{
			ModifiedDateTime = DateTimeOffset.Parse("2018-10-21T08:10:32.489Z"),
			Actions = ChatMessageActions.ReactionAdded,
			Reaction = new ChatMessageReaction
			{
				ReactionType = "laugh",
				User = new ChatMessageReactionIdentitySet
				{
					Application = null,
					Device = null,
					User = new Identity
					{
						Id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
						DisplayName = null,
						AdditionalData = new Dictionary<string, object>
						{
							{
								"userIdentityType" , "aadUser"
							},
						},
					},
				},
			},
		},
		new ChatMessageHistoryItem
		{
			ModifiedDateTime = DateTimeOffset.Parse("2018-10-21T02:17:14.67Z"),
			Actions = ChatMessageActions.ReactionAdded,
			Reaction = new ChatMessageReaction
			{
				ReactionType = "like",
				User = new ChatMessageReactionIdentitySet
				{
					Application = null,
					Device = null,
					User = new Identity
					{
						Id = "f1b66449-b46d-49b0-9c3c-53c10a5c818e",
						DisplayName = null,
						AdditionalData = new Dictionary<string, object>
						{
							{
								"userIdentityType" , "aadUser"
							},
						},
					},
				},
			},
		},
		new ChatMessageHistoryItem
		{
			ModifiedDateTime = DateTimeOffset.Parse("2018-10-21T02:34:40.3Z"),
			Actions = ChatMessageActions.ReactionAdded,
			Reaction = new ChatMessageReaction
			{
				ReactionType = "like",
				User = new ChatMessageReactionIdentitySet
				{
					Application = null,
					Device = null,
					User = new Identity
					{
						Id = "4c9041b7-449a-40f7-8855-56da239b9fd1",
						DisplayName = null,
						AdditionalData = new Dictionary<string, object>
						{
							{
								"userIdentityType" , "aadUser"
							},
						},
					},
				},
			},
		},
		new ChatMessageHistoryItem
		{
			ModifiedDateTime = DateTimeOffset.Parse("2018-10-21T08:10:25.489Z"),
			Actions = ChatMessageActions.ReactionAdded,
			Reaction = new ChatMessageReaction
			{
				ReactionType = "like",
				User = new ChatMessageReactionIdentitySet
				{
					Application = null,
					Device = null,
					User = new Identity
					{
						Id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
						DisplayName = null,
						AdditionalData = new Dictionary<string, object>
						{
							{
								"userIdentityType" , "aadUser"
							},
						},
					},
				},
			},
		},
		new ChatMessageHistoryItem
		{
			ModifiedDateTime = DateTimeOffset.Parse("2018-10-21T08:10:31.489Z"),
			Actions = ChatMessageActions.ReactionAdded,
			Reaction = new ChatMessageReaction
			{
				ReactionType = "heart",
				User = new ChatMessageReactionIdentitySet
				{
					Application = null,
					Device = null,
					User = new Identity
					{
						Id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
						DisplayName = null,
						AdditionalData = new Dictionary<string, object>
						{
							{
								"userIdentityType" , "aadUser"
							},
						},
					},
				},
			},
		},
		new ChatMessageHistoryItem
		{
			ModifiedDateTime = DateTimeOffset.Parse("2018-10-21T08:10:33.489Z"),
			Actions = ChatMessageActions.ReactionAdded,
			Reaction = new ChatMessageReaction
			{
				ReactionType = "sad",
				User = new ChatMessageReactionIdentitySet
				{
					Application = null,
					Device = null,
					User = new Identity
					{
						Id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
						DisplayName = null,
						AdditionalData = new Dictionary<string, object>
						{
							{
								"userIdentityType" , "aadUser"
							},
						},
					},
				},
			},
		},
		new ChatMessageHistoryItem
		{
			ModifiedDateTime = DateTimeOffset.Parse("2018-10-21T08:10:34.489Z"),
			Actions = ChatMessageActions.ReactionAdded,
			Reaction = new ChatMessageReaction
			{
				ReactionType = "sad",
				User = new ChatMessageReactionIdentitySet
				{
					Application = null,
					Device = null,
					User = new Identity
					{
						Id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
						DisplayName = null,
						AdditionalData = new Dictionary<string, object>
						{
							{
								"userIdentityType" , "aadUser"
							},
						},
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages["{chatMessage-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewChatMessage()
messageType := graphmodels.MESSAGE_CHATMESSAGETYPE 
requestBody.SetMessageType(&messageType) 
subject := null
requestBody.SetSubject(&subject) 
summary := null
requestBody.SetSummary(&summary) 
importance := graphmodels.NORMAL_CHATMESSAGEIMPORTANCE 
requestBody.SetImportance(&importance) 
locale := "en-us"
requestBody.SetLocale(&locale) 
from := graphmodels.NewChatMessageFromIdentitySet()
application := null
from.SetApplication(&application) 
device := null
from.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "3b102402-813e-4e17-a6b2-f841aef1fdfc"
user.SetId(&id) 
displayName := "Lam Cong"
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
from.SetUser(user)
additionalData := map[string]interface{}{
	conversation := null
from.SetConversation(&conversation) 
}
from.SetAdditionalData(additionalData)
requestBody.SetFrom(from)
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "<p><em>text</em></p><attachment id=\"e8f78756199240b88448ae0fc6db112d\"></attachment><attachment id=\"638464e32834471ea202007da60a5ae6\"></attachment>"
body.SetContent(&content) 
requestBody.SetBody(body)


chatMessageAttachment := graphmodels.NewChatMessageAttachment()
id := "e8f78756199240b88448ae0fc6db112d"
chatMessageAttachment.SetId(&id) 
contentType := "application/vnd.microsoft.card.hero"
chatMessageAttachment.SetContentType(&contentType) 
contentUrl := null
chatMessageAttachment.SetContentUrl(&contentUrl) 
content := "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"image\": \"https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png\",\r\n      \"title\": \"😃😃 click me 😃😃\",\r\n      \"value\": \"http://microsoft.com\"\r\n    },\r\n    {\r\n      \"type\": \"imback\",\r\n      \"title\": \"&i am back& <>= \"\",\r\n      \"value\": \"&i am back& <>= \"\"\r\n    },\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"title\": \"Open URL\",\r\n      \"value\": \"http://google.com\"\r\n    }\r\n  ]\r\n}"
chatMessageAttachment.SetContent(&content) 
name := null
chatMessageAttachment.SetName(&name) 
thumbnailUrl := null
chatMessageAttachment.SetThumbnailUrl(&thumbnailUrl) 
chatMessageAttachment1 := graphmodels.NewChatMessageAttachment()
id := "638464e32834471ea202007da60a5ae6"
chatMessageAttachment1.SetId(&id) 
contentType := "application/vnd.microsoft.card.hero"
chatMessageAttachment1.SetContentType(&contentType) 
contentUrl := null
chatMessageAttachment1.SetContentUrl(&contentUrl) 
content := "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"&message back& <>= \"\",\r\n      \"text\": \"text = &message back& <>= \"\",\r\n      \"displayText\": \"displayText = &message back& <>= \"\",\r\n      \"value\": {\r\n        \"text\": \"some text 2\"\r\n      }\r\n    }\r\n  ]\r\n}"
chatMessageAttachment1.SetContent(&content) 
name := null
chatMessageAttachment1.SetName(&name) 
thumbnailUrl := null
chatMessageAttachment1.SetThumbnailUrl(&thumbnailUrl) 

attachments := []graphmodels.ChatMessageAttachmentable {
	chatMessageAttachment,
	chatMessageAttachment1,
}
requestBody.SetAttachments(attachments)
mentions := []graphmodels.ChatMessageMentionable {

}
requestBody.SetMentions(mentions)


chatMessageReaction := graphmodels.NewChatMessageReaction()
reactionType := "angry"
chatMessageReaction.SetReactionType(&reactionType) 
createdDateTime , err := time.Parse(time.RFC3339, "2018-10-21T08:10:30.489Z")
chatMessageReaction.SetCreatedDateTime(&createdDateTime) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "f1b66449-b46d-49b0-9c3c-53c10a5c818e"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
chatMessageReaction.SetUser(user)
chatMessageReaction1 := graphmodels.NewChatMessageReaction()
reactionType := "laugh"
chatMessageReaction1.SetReactionType(&reactionType) 
createdDateTime , err := time.Parse(time.RFC3339, "2018-10-21T08:10:32.489Z")
chatMessageReaction1.SetCreatedDateTime(&createdDateTime) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
chatMessageReaction1.SetUser(user)
chatMessageReaction2 := graphmodels.NewChatMessageReaction()
reactionType := "like"
chatMessageReaction2.SetReactionType(&reactionType) 
createdDateTime , err := time.Parse(time.RFC3339, "2018-10-21T02:17:14.67Z")
chatMessageReaction2.SetCreatedDateTime(&createdDateTime) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "f1b66449-b46d-49b0-9c3c-53c10a5c818e"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
chatMessageReaction2.SetUser(user)
chatMessageReaction3 := graphmodels.NewChatMessageReaction()
reactionType := "like"
chatMessageReaction3.SetReactionType(&reactionType) 
createdDateTime , err := time.Parse(time.RFC3339, "2018-10-21T02:34:40.3Z")
chatMessageReaction3.SetCreatedDateTime(&createdDateTime) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "4c9041b7-449a-40f7-8855-56da239b9fd1"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
chatMessageReaction3.SetUser(user)
chatMessageReaction4 := graphmodels.NewChatMessageReaction()
reactionType := "like"
chatMessageReaction4.SetReactionType(&reactionType) 
createdDateTime , err := time.Parse(time.RFC3339, "2018-10-21T08:10:25.489Z")
chatMessageReaction4.SetCreatedDateTime(&createdDateTime) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
chatMessageReaction4.SetUser(user)
chatMessageReaction5 := graphmodels.NewChatMessageReaction()
reactionType := "heart"
chatMessageReaction5.SetReactionType(&reactionType) 
createdDateTime , err := time.Parse(time.RFC3339, "2018-10-21T08:10:31.489Z")
chatMessageReaction5.SetCreatedDateTime(&createdDateTime) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
chatMessageReaction5.SetUser(user)
chatMessageReaction6 := graphmodels.NewChatMessageReaction()
reactionType := "sad"
chatMessageReaction6.SetReactionType(&reactionType) 
createdDateTime , err := time.Parse(time.RFC3339, "2018-10-21T08:10:33.489Z")
chatMessageReaction6.SetCreatedDateTime(&createdDateTime) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
chatMessageReaction6.SetUser(user)
chatMessageReaction7 := graphmodels.NewChatMessageReaction()
reactionType := "surprised"
chatMessageReaction7.SetReactionType(&reactionType) 
createdDateTime , err := time.Parse(time.RFC3339, "2018-10-21T08:10:34.489Z")
chatMessageReaction7.SetCreatedDateTime(&createdDateTime) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
chatMessageReaction7.SetUser(user)

reactions := []graphmodels.ChatMessageReactionable {
	chatMessageReaction,
	chatMessageReaction1,
	chatMessageReaction2,
	chatMessageReaction3,
	chatMessageReaction4,
	chatMessageReaction5,
	chatMessageReaction6,
	chatMessageReaction7,
}
requestBody.SetReactions(reactions)


chatMessageHistoryItem := graphmodels.NewChatMessageHistoryItem()
modifiedDateTime , err := time.Parse(time.RFC3339, "2018-10-21T08:10:30.489Z")
chatMessageHistoryItem.SetModifiedDateTime(&modifiedDateTime) 
actions := graphmodels.REACTIONADDED_CHATMESSAGEACTIONS 
chatMessageHistoryItem.SetActions(&actions) 
reaction := graphmodels.NewChatMessageReaction()
reactionType := "angry"
reaction.SetReactionType(&reactionType) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "f1b66449-b46d-49b0-9c3c-53c10a5c818e"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
reaction.SetUser(user)
chatMessageHistoryItem.SetReaction(reaction)
chatMessageHistoryItem1 := graphmodels.NewChatMessageHistoryItem()
modifiedDateTime , err := time.Parse(time.RFC3339, "2018-10-21T08:10:32.489Z")
chatMessageHistoryItem1.SetModifiedDateTime(&modifiedDateTime) 
actions := graphmodels.REACTIONADDED_CHATMESSAGEACTIONS 
chatMessageHistoryItem1.SetActions(&actions) 
reaction := graphmodels.NewChatMessageReaction()
reactionType := "laugh"
reaction.SetReactionType(&reactionType) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
reaction.SetUser(user)
chatMessageHistoryItem1.SetReaction(reaction)
chatMessageHistoryItem2 := graphmodels.NewChatMessageHistoryItem()
modifiedDateTime , err := time.Parse(time.RFC3339, "2018-10-21T02:17:14.67Z")
chatMessageHistoryItem2.SetModifiedDateTime(&modifiedDateTime) 
actions := graphmodels.REACTIONADDED_CHATMESSAGEACTIONS 
chatMessageHistoryItem2.SetActions(&actions) 
reaction := graphmodels.NewChatMessageReaction()
reactionType := "like"
reaction.SetReactionType(&reactionType) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "f1b66449-b46d-49b0-9c3c-53c10a5c818e"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
reaction.SetUser(user)
chatMessageHistoryItem2.SetReaction(reaction)
chatMessageHistoryItem3 := graphmodels.NewChatMessageHistoryItem()
modifiedDateTime , err := time.Parse(time.RFC3339, "2018-10-21T02:34:40.3Z")
chatMessageHistoryItem3.SetModifiedDateTime(&modifiedDateTime) 
actions := graphmodels.REACTIONADDED_CHATMESSAGEACTIONS 
chatMessageHistoryItem3.SetActions(&actions) 
reaction := graphmodels.NewChatMessageReaction()
reactionType := "like"
reaction.SetReactionType(&reactionType) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "4c9041b7-449a-40f7-8855-56da239b9fd1"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
reaction.SetUser(user)
chatMessageHistoryItem3.SetReaction(reaction)
chatMessageHistoryItem4 := graphmodels.NewChatMessageHistoryItem()
modifiedDateTime , err := time.Parse(time.RFC3339, "2018-10-21T08:10:25.489Z")
chatMessageHistoryItem4.SetModifiedDateTime(&modifiedDateTime) 
actions := graphmodels.REACTIONADDED_CHATMESSAGEACTIONS 
chatMessageHistoryItem4.SetActions(&actions) 
reaction := graphmodels.NewChatMessageReaction()
reactionType := "like"
reaction.SetReactionType(&reactionType) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
reaction.SetUser(user)
chatMessageHistoryItem4.SetReaction(reaction)
chatMessageHistoryItem5 := graphmodels.NewChatMessageHistoryItem()
modifiedDateTime , err := time.Parse(time.RFC3339, "2018-10-21T08:10:31.489Z")
chatMessageHistoryItem5.SetModifiedDateTime(&modifiedDateTime) 
actions := graphmodels.REACTIONADDED_CHATMESSAGEACTIONS 
chatMessageHistoryItem5.SetActions(&actions) 
reaction := graphmodels.NewChatMessageReaction()
reactionType := "heart"
reaction.SetReactionType(&reactionType) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
reaction.SetUser(user)
chatMessageHistoryItem5.SetReaction(reaction)
chatMessageHistoryItem6 := graphmodels.NewChatMessageHistoryItem()
modifiedDateTime , err := time.Parse(time.RFC3339, "2018-10-21T08:10:33.489Z")
chatMessageHistoryItem6.SetModifiedDateTime(&modifiedDateTime) 
actions := graphmodels.REACTIONADDED_CHATMESSAGEACTIONS 
chatMessageHistoryItem6.SetActions(&actions) 
reaction := graphmodels.NewChatMessageReaction()
reactionType := "sad"
reaction.SetReactionType(&reactionType) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
reaction.SetUser(user)
chatMessageHistoryItem6.SetReaction(reaction)
chatMessageHistoryItem7 := graphmodels.NewChatMessageHistoryItem()
modifiedDateTime , err := time.Parse(time.RFC3339, "2018-10-21T08:10:34.489Z")
chatMessageHistoryItem7.SetModifiedDateTime(&modifiedDateTime) 
actions := graphmodels.SURPRISED_CHATMESSAGEACTIONS 
chatMessageHistoryItem7.SetActions(&actions) 
reaction := graphmodels.NewChatMessageReaction()
reactionType := "sad"
reaction.SetReactionType(&reactionType) 
user := graphmodels.NewChatMessageReactionIdentitySet()
application := null
user.SetApplication(&application) 
device := null
user.SetDevice(&device) 
user := graphmodels.NewIdentity()
id := "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
user.SetId(&id) 
displayName := null
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
user.SetUser(user)
reaction.SetUser(user)
chatMessageHistoryItem7.SetReaction(reaction)

messageHistory := []graphmodels.ChatMessageHistoryItemable {
	chatMessageHistoryItem,
	chatMessageHistoryItem1,
	chatMessageHistoryItem2,
	chatMessageHistoryItem3,
	chatMessageHistoryItem4,
	chatMessageHistoryItem5,
	chatMessageHistoryItem6,
	chatMessageHistoryItem7,
}
requestBody.SetMessageHistory(messageHistory)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().ByChatMessageId("chatMessage-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
chatMessage.setMessageType(ChatMessageType.Message);
chatMessage.setSubject(null);
chatMessage.setSummary(null);
chatMessage.setImportance(ChatMessageImportance.Normal);
chatMessage.setLocale("en-us");
ChatMessageFromIdentitySet from = new ChatMessageFromIdentitySet();
from.setApplication(null);
from.setDevice(null);
Identity user = new Identity();
user.setId("3b102402-813e-4e17-a6b2-f841aef1fdfc");
user.setDisplayName("Lam Cong");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("userIdentityType", "aadUser");
user.setAdditionalData(additionalData);
from.setUser(user);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("conversation", null);
from.setAdditionalData(additionalData1);
chatMessage.setFrom(from);
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("<p><em>text</em></p><attachment id=\"e8f78756199240b88448ae0fc6db112d\"></attachment><attachment id=\"638464e32834471ea202007da60a5ae6\"></attachment>");
chatMessage.setBody(body);
LinkedList<ChatMessageAttachment> attachments = new LinkedList<ChatMessageAttachment>();
ChatMessageAttachment chatMessageAttachment = new ChatMessageAttachment();
chatMessageAttachment.setId("e8f78756199240b88448ae0fc6db112d");
chatMessageAttachment.setContentType("application/vnd.microsoft.card.hero");
chatMessageAttachment.setContentUrl(null);
chatMessageAttachment.setContent("{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"image\": \"https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png\",\r\n      \"title\": \"😃😃 click me 😃😃\",\r\n      \"value\": \"http://microsoft.com\"\r\n    },\r\n    {\r\n      \"type\": \"imback\",\r\n      \"title\": \"&i am back& <>= \"\",\r\n      \"value\": \"&i am back& <>= \"\"\r\n    },\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"title\": \"Open URL\",\r\n      \"value\": \"http://google.com\"\r\n    }\r\n  ]\r\n}");
chatMessageAttachment.setName(null);
chatMessageAttachment.setThumbnailUrl(null);
attachments.add(chatMessageAttachment);
ChatMessageAttachment chatMessageAttachment1 = new ChatMessageAttachment();
chatMessageAttachment1.setId("638464e32834471ea202007da60a5ae6");
chatMessageAttachment1.setContentType("application/vnd.microsoft.card.hero");
chatMessageAttachment1.setContentUrl(null);
chatMessageAttachment1.setContent("{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"&message back& <>= \"\",\r\n      \"text\": \"text = &message back& <>= \"\",\r\n      \"displayText\": \"displayText = &message back& <>= \"\",\r\n      \"value\": {\r\n        \"text\": \"some text 2\"\r\n      }\r\n    }\r\n  ]\r\n}");
chatMessageAttachment1.setName(null);
chatMessageAttachment1.setThumbnailUrl(null);
attachments.add(chatMessageAttachment1);
chatMessage.setAttachments(attachments);
LinkedList<ChatMessageMention> mentions = new LinkedList<ChatMessageMention>();
chatMessage.setMentions(mentions);
LinkedList<ChatMessageReaction> reactions = new LinkedList<ChatMessageReaction>();
ChatMessageReaction chatMessageReaction = new ChatMessageReaction();
chatMessageReaction.setReactionType("angry");
OffsetDateTime createdDateTime = OffsetDateTime.parse("2018-10-21T08:10:30.489Z");
chatMessageReaction.setCreatedDateTime(createdDateTime);
ChatMessageReactionIdentitySet user1 = new ChatMessageReactionIdentitySet();
user1.setApplication(null);
user1.setDevice(null);
Identity user2 = new Identity();
user2.setId("f1b66449-b46d-49b0-9c3c-53c10a5c818e");
user2.setDisplayName(null);
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
additionalData2.put("userIdentityType", "aadUser");
user2.setAdditionalData(additionalData2);
user1.setUser(user2);
chatMessageReaction.setUser(user1);
reactions.add(chatMessageReaction);
ChatMessageReaction chatMessageReaction1 = new ChatMessageReaction();
chatMessageReaction1.setReactionType("laugh");
OffsetDateTime createdDateTime1 = OffsetDateTime.parse("2018-10-21T08:10:32.489Z");
chatMessageReaction1.setCreatedDateTime(createdDateTime1);
ChatMessageReactionIdentitySet user3 = new ChatMessageReactionIdentitySet();
user3.setApplication(null);
user3.setDevice(null);
Identity user4 = new Identity();
user4.setId("03a02232-d8f5-4970-a77e-6e8c76ce7a4e");
user4.setDisplayName(null);
HashMap<String, Object> additionalData3 = new HashMap<String, Object>();
additionalData3.put("userIdentityType", "aadUser");
user4.setAdditionalData(additionalData3);
user3.setUser(user4);
chatMessageReaction1.setUser(user3);
reactions.add(chatMessageReaction1);
ChatMessageReaction chatMessageReaction2 = new ChatMessageReaction();
chatMessageReaction2.setReactionType("like");
OffsetDateTime createdDateTime2 = OffsetDateTime.parse("2018-10-21T02:17:14.67Z");
chatMessageReaction2.setCreatedDateTime(createdDateTime2);
ChatMessageReactionIdentitySet user5 = new ChatMessageReactionIdentitySet();
user5.setApplication(null);
user5.setDevice(null);
Identity user6 = new Identity();
user6.setId("f1b66449-b46d-49b0-9c3c-53c10a5c818e");
user6.setDisplayName(null);
HashMap<String, Object> additionalData4 = new HashMap<String, Object>();
additionalData4.put("userIdentityType", "aadUser");
user6.setAdditionalData(additionalData4);
user5.setUser(user6);
chatMessageReaction2.setUser(user5);
reactions.add(chatMessageReaction2);
ChatMessageReaction chatMessageReaction3 = new ChatMessageReaction();
chatMessageReaction3.setReactionType("like");
OffsetDateTime createdDateTime3 = OffsetDateTime.parse("2018-10-21T02:34:40.3Z");
chatMessageReaction3.setCreatedDateTime(createdDateTime3);
ChatMessageReactionIdentitySet user7 = new ChatMessageReactionIdentitySet();
user7.setApplication(null);
user7.setDevice(null);
Identity user8 = new Identity();
user8.setId("4c9041b7-449a-40f7-8855-56da239b9fd1");
user8.setDisplayName(null);
HashMap<String, Object> additionalData5 = new HashMap<String, Object>();
additionalData5.put("userIdentityType", "aadUser");
user8.setAdditionalData(additionalData5);
user7.setUser(user8);
chatMessageReaction3.setUser(user7);
reactions.add(chatMessageReaction3);
ChatMessageReaction chatMessageReaction4 = new ChatMessageReaction();
chatMessageReaction4.setReactionType("like");
OffsetDateTime createdDateTime4 = OffsetDateTime.parse("2018-10-21T08:10:25.489Z");
chatMessageReaction4.setCreatedDateTime(createdDateTime4);
ChatMessageReactionIdentitySet user9 = new ChatMessageReactionIdentitySet();
user9.setApplication(null);
user9.setDevice(null);
Identity user10 = new Identity();
user10.setId("03a02232-d8f5-4970-a77e-6e8c76ce7a4e");
user10.setDisplayName(null);
HashMap<String, Object> additionalData6 = new HashMap<String, Object>();
additionalData6.put("userIdentityType", "aadUser");
user10.setAdditionalData(additionalData6);
user9.setUser(user10);
chatMessageReaction4.setUser(user9);
reactions.add(chatMessageReaction4);
ChatMessageReaction chatMessageReaction5 = new ChatMessageReaction();
chatMessageReaction5.setReactionType("heart");
OffsetDateTime createdDateTime5 = OffsetDateTime.parse("2018-10-21T08:10:31.489Z");
chatMessageReaction5.setCreatedDateTime(createdDateTime5);
ChatMessageReactionIdentitySet user11 = new ChatMessageReactionIdentitySet();
user11.setApplication(null);
user11.setDevice(null);
Identity user12 = new Identity();
user12.setId("03a02232-d8f5-4970-a77e-6e8c76ce7a4e");
user12.setDisplayName(null);
HashMap<String, Object> additionalData7 = new HashMap<String, Object>();
additionalData7.put("userIdentityType", "aadUser");
user12.setAdditionalData(additionalData7);
user11.setUser(user12);
chatMessageReaction5.setUser(user11);
reactions.add(chatMessageReaction5);
ChatMessageReaction chatMessageReaction6 = new ChatMessageReaction();
chatMessageReaction6.setReactionType("sad");
OffsetDateTime createdDateTime6 = OffsetDateTime.parse("2018-10-21T08:10:33.489Z");
chatMessageReaction6.setCreatedDateTime(createdDateTime6);
ChatMessageReactionIdentitySet user13 = new ChatMessageReactionIdentitySet();
user13.setApplication(null);
user13.setDevice(null);
Identity user14 = new Identity();
user14.setId("03a02232-d8f5-4970-a77e-6e8c76ce7a4e");
user14.setDisplayName(null);
HashMap<String, Object> additionalData8 = new HashMap<String, Object>();
additionalData8.put("userIdentityType", "aadUser");
user14.setAdditionalData(additionalData8);
user13.setUser(user14);
chatMessageReaction6.setUser(user13);
reactions.add(chatMessageReaction6);
ChatMessageReaction chatMessageReaction7 = new ChatMessageReaction();
chatMessageReaction7.setReactionType("surprised");
OffsetDateTime createdDateTime7 = OffsetDateTime.parse("2018-10-21T08:10:34.489Z");
chatMessageReaction7.setCreatedDateTime(createdDateTime7);
ChatMessageReactionIdentitySet user15 = new ChatMessageReactionIdentitySet();
user15.setApplication(null);
user15.setDevice(null);
Identity user16 = new Identity();
user16.setId("03a02232-d8f5-4970-a77e-6e8c76ce7a4e");
user16.setDisplayName(null);
HashMap<String, Object> additionalData9 = new HashMap<String, Object>();
additionalData9.put("userIdentityType", "aadUser");
user16.setAdditionalData(additionalData9);
user15.setUser(user16);
chatMessageReaction7.setUser(user15);
reactions.add(chatMessageReaction7);
chatMessage.setReactions(reactions);
LinkedList<ChatMessageHistoryItem> messageHistory = new LinkedList<ChatMessageHistoryItem>();
ChatMessageHistoryItem chatMessageHistoryItem = new ChatMessageHistoryItem();
OffsetDateTime modifiedDateTime = OffsetDateTime.parse("2018-10-21T08:10:30.489Z");
chatMessageHistoryItem.setModifiedDateTime(modifiedDateTime);
chatMessageHistoryItem.setActions(EnumSet.of(ChatMessageActions.ReactionAdded));
ChatMessageReaction reaction = new ChatMessageReaction();
reaction.setReactionType("angry");
ChatMessageReactionIdentitySet user17 = new ChatMessageReactionIdentitySet();
user17.setApplication(null);
user17.setDevice(null);
Identity user18 = new Identity();
user18.setId("f1b66449-b46d-49b0-9c3c-53c10a5c818e");
user18.setDisplayName(null);
HashMap<String, Object> additionalData10 = new HashMap<String, Object>();
additionalData10.put("userIdentityType", "aadUser");
user18.setAdditionalData(additionalData10);
user17.setUser(user18);
reaction.setUser(user17);
chatMessageHistoryItem.setReaction(reaction);
messageHistory.add(chatMessageHistoryItem);
ChatMessageHistoryItem chatMessageHistoryItem1 = new ChatMessageHistoryItem();
OffsetDateTime modifiedDateTime1 = OffsetDateTime.parse("2018-10-21T08:10:32.489Z");
chatMessageHistoryItem1.setModifiedDateTime(modifiedDateTime1);
chatMessageHistoryItem1.setActions(EnumSet.of(ChatMessageActions.ReactionAdded));
ChatMessageReaction reaction1 = new ChatMessageReaction();
reaction1.setReactionType("laugh");
ChatMessageReactionIdentitySet user19 = new ChatMessageReactionIdentitySet();
user19.setApplication(null);
user19.setDevice(null);
Identity user20 = new Identity();
user20.setId("03a02232-d8f5-4970-a77e-6e8c76ce7a4e");
user20.setDisplayName(null);
HashMap<String, Object> additionalData11 = new HashMap<String, Object>();
additionalData11.put("userIdentityType", "aadUser");
user20.setAdditionalData(additionalData11);
user19.setUser(user20);
reaction1.setUser(user19);
chatMessageHistoryItem1.setReaction(reaction1);
messageHistory.add(chatMessageHistoryItem1);
ChatMessageHistoryItem chatMessageHistoryItem2 = new ChatMessageHistoryItem();
OffsetDateTime modifiedDateTime2 = OffsetDateTime.parse("2018-10-21T02:17:14.67Z");
chatMessageHistoryItem2.setModifiedDateTime(modifiedDateTime2);
chatMessageHistoryItem2.setActions(EnumSet.of(ChatMessageActions.ReactionAdded));
ChatMessageReaction reaction2 = new ChatMessageReaction();
reaction2.setReactionType("like");
ChatMessageReactionIdentitySet user21 = new ChatMessageReactionIdentitySet();
user21.setApplication(null);
user21.setDevice(null);
Identity user22 = new Identity();
user22.setId("f1b66449-b46d-49b0-9c3c-53c10a5c818e");
user22.setDisplayName(null);
HashMap<String, Object> additionalData12 = new HashMap<String, Object>();
additionalData12.put("userIdentityType", "aadUser");
user22.setAdditionalData(additionalData12);
user21.setUser(user22);
reaction2.setUser(user21);
chatMessageHistoryItem2.setReaction(reaction2);
messageHistory.add(chatMessageHistoryItem2);
ChatMessageHistoryItem chatMessageHistoryItem3 = new ChatMessageHistoryItem();
OffsetDateTime modifiedDateTime3 = OffsetDateTime.parse("2018-10-21T02:34:40.3Z");
chatMessageHistoryItem3.setModifiedDateTime(modifiedDateTime3);
chatMessageHistoryItem3.setActions(EnumSet.of(ChatMessageActions.ReactionAdded));
ChatMessageReaction reaction3 = new ChatMessageReaction();
reaction3.setReactionType("like");
ChatMessageReactionIdentitySet user23 = new ChatMessageReactionIdentitySet();
user23.setApplication(null);
user23.setDevice(null);
Identity user24 = new Identity();
user24.setId("4c9041b7-449a-40f7-8855-56da239b9fd1");
user24.setDisplayName(null);
HashMap<String, Object> additionalData13 = new HashMap<String, Object>();
additionalData13.put("userIdentityType", "aadUser");
user24.setAdditionalData(additionalData13);
user23.setUser(user24);
reaction3.setUser(user23);
chatMessageHistoryItem3.setReaction(reaction3);
messageHistory.add(chatMessageHistoryItem3);
ChatMessageHistoryItem chatMessageHistoryItem4 = new ChatMessageHistoryItem();
OffsetDateTime modifiedDateTime4 = OffsetDateTime.parse("2018-10-21T08:10:25.489Z");
chatMessageHistoryItem4.setModifiedDateTime(modifiedDateTime4);
chatMessageHistoryItem4.setActions(EnumSet.of(ChatMessageActions.ReactionAdded));
ChatMessageReaction reaction4 = new ChatMessageReaction();
reaction4.setReactionType("like");
ChatMessageReactionIdentitySet user25 = new ChatMessageReactionIdentitySet();
user25.setApplication(null);
user25.setDevice(null);
Identity user26 = new Identity();
user26.setId("03a02232-d8f5-4970-a77e-6e8c76ce7a4e");
user26.setDisplayName(null);
HashMap<String, Object> additionalData14 = new HashMap<String, Object>();
additionalData14.put("userIdentityType", "aadUser");
user26.setAdditionalData(additionalData14);
user25.setUser(user26);
reaction4.setUser(user25);
chatMessageHistoryItem4.setReaction(reaction4);
messageHistory.add(chatMessageHistoryItem4);
ChatMessageHistoryItem chatMessageHistoryItem5 = new ChatMessageHistoryItem();
OffsetDateTime modifiedDateTime5 = OffsetDateTime.parse("2018-10-21T08:10:31.489Z");
chatMessageHistoryItem5.setModifiedDateTime(modifiedDateTime5);
chatMessageHistoryItem5.setActions(EnumSet.of(ChatMessageActions.ReactionAdded));
ChatMessageReaction reaction5 = new ChatMessageReaction();
reaction5.setReactionType("heart");
ChatMessageReactionIdentitySet user27 = new ChatMessageReactionIdentitySet();
user27.setApplication(null);
user27.setDevice(null);
Identity user28 = new Identity();
user28.setId("03a02232-d8f5-4970-a77e-6e8c76ce7a4e");
user28.setDisplayName(null);
HashMap<String, Object> additionalData15 = new HashMap<String, Object>();
additionalData15.put("userIdentityType", "aadUser");
user28.setAdditionalData(additionalData15);
user27.setUser(user28);
reaction5.setUser(user27);
chatMessageHistoryItem5.setReaction(reaction5);
messageHistory.add(chatMessageHistoryItem5);
ChatMessageHistoryItem chatMessageHistoryItem6 = new ChatMessageHistoryItem();
OffsetDateTime modifiedDateTime6 = OffsetDateTime.parse("2018-10-21T08:10:33.489Z");
chatMessageHistoryItem6.setModifiedDateTime(modifiedDateTime6);
chatMessageHistoryItem6.setActions(EnumSet.of(ChatMessageActions.ReactionAdded));
ChatMessageReaction reaction6 = new ChatMessageReaction();
reaction6.setReactionType("sad");
ChatMessageReactionIdentitySet user29 = new ChatMessageReactionIdentitySet();
user29.setApplication(null);
user29.setDevice(null);
Identity user30 = new Identity();
user30.setId("03a02232-d8f5-4970-a77e-6e8c76ce7a4e");
user30.setDisplayName(null);
HashMap<String, Object> additionalData16 = new HashMap<String, Object>();
additionalData16.put("userIdentityType", "aadUser");
user30.setAdditionalData(additionalData16);
user29.setUser(user30);
reaction6.setUser(user29);
chatMessageHistoryItem6.setReaction(reaction6);
messageHistory.add(chatMessageHistoryItem6);
ChatMessageHistoryItem chatMessageHistoryItem7 = new ChatMessageHistoryItem();
OffsetDateTime modifiedDateTime7 = OffsetDateTime.parse("2018-10-21T08:10:34.489Z");
chatMessageHistoryItem7.setModifiedDateTime(modifiedDateTime7);
chatMessageHistoryItem7.setActions(EnumSet.of(ChatMessageActions.ReactionAdded));
ChatMessageReaction reaction7 = new ChatMessageReaction();
reaction7.setReactionType("sad");
ChatMessageReactionIdentitySet user31 = new ChatMessageReactionIdentitySet();
user31.setApplication(null);
user31.setDevice(null);
Identity user32 = new Identity();
user32.setId("03a02232-d8f5-4970-a77e-6e8c76ce7a4e");
user32.setDisplayName(null);
HashMap<String, Object> additionalData17 = new HashMap<String, Object>();
additionalData17.put("userIdentityType", "aadUser");
user32.setAdditionalData(additionalData17);
user31.setUser(user32);
reaction7.setUser(user31);
chatMessageHistoryItem7.setReaction(reaction7);
messageHistory.add(chatMessageHistoryItem7);
chatMessage.setMessageHistory(messageHistory);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().byChatMessageId("{chatMessage-id}").patch(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
  messageType: 'message',
  subject: null,
  summary: null,
  importance: 'normal',
  locale: 'en-us',
  from: {
    application: null,
    device: null,
    user: {
      id: '3b102402-813e-4e17-a6b2-f841aef1fdfc',
      displayName: 'Lam Cong',
      userIdentityType: 'aadUser'
    },
    conversation: null
  },
  body: {
    contentType: 'html',
    content: '<p><em>text</em></p><attachment id=\"e8f78756199240b88448ae0fc6db112d\"></attachment><attachment id=\"638464e32834471ea202007da60a5ae6\"></attachment>'
  },
  attachments: [
    {
      id: 'e8f78756199240b88448ae0fc6db112d',
      contentType: 'application/vnd.microsoft.card.hero',
      contentUrl: null,
      content: '{\r\n  \"title\': \'*title*\",\r\n  \"subtitle\': \'*subtitle*\",\r\n  \"text\': \'Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you\'re cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\': [\r\n    {\r\n      \'url\': \'https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\': [\r\n    {\r\n      \'type\': \'openUrl\",\r\n      \"image\': \'https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png\",\r\n      \"title\': \'😃😃 click me 😃😃\",\r\n      \"value\': \'http://microsoft.com\"\r\n    },\r\n    {\r\n      \"type\': \'imback\",\r\n      \"title\': \'&i am back& <>= \\\"\",\r\n      \"value\': \'&i am back& <>= \\\"\"\r\n    },\r\n    {\r\n      \"type\': \'openUrl\",\r\n      \"title\': \'Open URL\",\r\n      \"value\': \"http://google.com\"\r\n    }\r\n  ]\r\n}",
      name: null,
      thumbnailUrl: null
    },
    {
      id: '638464e32834471ea202007da60a5ae6',
      contentType: 'application/vnd.microsoft.card.hero',
      contentUrl: null,
      content: '{\r\n  \"title\': \'*title*\",\r\n  \"subtitle\': \'*subtitle*\",\r\n  \"text\': \'Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you\'re cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\': [\r\n    {\r\n      \'url\': \'https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\': [\r\n    {\r\n      \'type\': \'messageBack\",\r\n      \"title\': \'&message back& <>= \\\"\",\r\n      \"text\': \'text = &message back& <>= \\\"\",\r\n      \"displayText\': \'displayText = &message back& <>= \\\"\",\r\n      \"value\': {\r\n        \'text\': \"some text 2\"\r\n      }\r\n    }\r\n  ]\r\n}",
      name: null,
      thumbnailUrl: null
    }
  ],
  mentions: [],
  reactions: [
    {
      reactionType: 'angry',
      createdDateTime: '2018-10-21T08:10:30.489Z',
      user: {
        application: null,
        device: null,
        user: {
          id: 'f1b66449-b46d-49b0-9c3c-53c10a5c818e',
          displayName: null,
          userIdentityType: 'aadUser'
        }
      }
    },
    {
      reactionType: 'laugh',
      createdDateTime: '2018-10-21T08:10:32.489Z',
      user: {
        application: null,
        device: null,
        user: {
          id: '03a02232-d8f5-4970-a77e-6e8c76ce7a4e',
          displayName: null,
          userIdentityType: 'aadUser'
        }
      }
    },
    {
      reactionType: 'like',
      createdDateTime: '2018-10-21T02:17:14.67Z',
      user: {
        application: null,
        device: null,
        user: {
          id: 'f1b66449-b46d-49b0-9c3c-53c10a5c818e',
          displayName: null,
          userIdentityType: 'aadUser'
        }
      }
    },
    {
      reactionType: 'like',
      createdDateTime: '2018-10-21T02:34:40.3Z',
      user: {
        application: null,
        device: null,
        user: {
          id: '4c9041b7-449a-40f7-8855-56da239b9fd1',
          displayName: null,
          userIdentityType: 'aadUser'
        }
      }
    },
    {
      reactionType: 'like',
      createdDateTime: '2018-10-21T08:10:25.489Z',
      user: {
        application: null,
        device: null,
        user: {
          id: '03a02232-d8f5-4970-a77e-6e8c76ce7a4e',
          displayName: null,
          userIdentityType: 'aadUser'
        }
      }
    },
    {
      reactionType: 'heart',
      createdDateTime: '2018-10-21T08:10:31.489Z',
      user: {
        application: null,
        device: null,
        user: {
          id: '03a02232-d8f5-4970-a77e-6e8c76ce7a4e',
          displayName: null,
          userIdentityType: 'aadUser'
        }
      }
    },
    {
      reactionType: 'sad',
      createdDateTime: '2018-10-21T08:10:33.489Z',
      user: {
        application: null,
        device: null,
        user: {
          id: '03a02232-d8f5-4970-a77e-6e8c76ce7a4e',
          displayName: null,
          userIdentityType: 'aadUser'
        }
      }
    },
    {
      reactionType: 'surprised',
      createdDateTime: '2018-10-21T08:10:34.489Z',
      user: {
        application: null,
        device: null,
        user: {
          id: '03a02232-d8f5-4970-a77e-6e8c76ce7a4e',
          displayName: null,
          userIdentityType: 'aadUser'
        }
      }
    }
  ],
  messageHistory: [
    {
      modifiedDateTime: '2018-10-21T08:10:30.489Z',
      actions: 'reactionAdded',
      reaction: {
        reactionType: 'angry',
        user: {
          application: null,
          device: null,
          user: {
            id: 'f1b66449-b46d-49b0-9c3c-53c10a5c818e',
            displayName: null,
            userIdentityType: 'aadUser'
          }
        }
      }
    },
    {
      modifiedDateTime: '2018-10-21T08:10:32.489Z',
      actions: 'reactionAdded',
      reaction: {
        reactionType: 'laugh',
        user: {
          application: null,
          device: null,
          user: {
            id: '03a02232-d8f5-4970-a77e-6e8c76ce7a4e',
            displayName: null,
            userIdentityType: 'aadUser'
          }
        }
      }
    },
    {
      modifiedDateTime: '2018-10-21T02:17:14.67Z',
      actions: 'reactionAdded',
      reaction: {
        reactionType: 'like',
        user: {
          application: null,
          device: null,
          user: {
            id: 'f1b66449-b46d-49b0-9c3c-53c10a5c818e',
            displayName: null,
            userIdentityType: 'aadUser'
          }
        }
      }
    },
    {
      modifiedDateTime: '2018-10-21T02:34:40.3Z',
      actions: 'reactionAdded',
      reaction: {
        reactionType: 'like',
        user: {
          application: null,
          device: null,
          user: {
            id: '4c9041b7-449a-40f7-8855-56da239b9fd1',
            displayName: null,
            userIdentityType: 'aadUser'
          }
        }
      }
    },
    {
      modifiedDateTime: '2018-10-21T08:10:25.489Z',
      actions: 'reactionAdded',
      reaction: {
        reactionType: 'like',
        user: {
          application: null,
          device: null,
          user: {
            id: '03a02232-d8f5-4970-a77e-6e8c76ce7a4e',
            displayName: null,
            userIdentityType: 'aadUser'
          }
        }
      }
    },
    {
      modifiedDateTime: '2018-10-21T08:10:31.489Z',
      actions: 'reactionAdded',
      reaction: {
        reactionType: 'heart',
        user: {
          application: null,
          device: null,
          user: {
            id: '03a02232-d8f5-4970-a77e-6e8c76ce7a4e',
            displayName: null,
            userIdentityType: 'aadUser'
          }
        }
      }
    },
    {
      modifiedDateTime: '2018-10-21T08:10:33.489Z',
      actions: 'reactionAdded',
      reaction: {
        reactionType: 'sad',
        user: {
          application: null,
          device: null,
          user: {
            id: '03a02232-d8f5-4970-a77e-6e8c76ce7a4e',
            displayName: null,
            userIdentityType: 'aadUser'
          }
        }
      }
    },
    {
      modifiedDateTime: '2018-10-21T08:10:34.489Z',
      actions: 'surprised',
      reaction: {
        reactionType: 'sad',
        user: {
          application: null,
          device: null,
          user: {
            id: '03a02232-d8f5-4970-a77e-6e8c76ce7a4e',
            displayName: null,
            userIdentityType: 'aadUser'
          }
        }
      }
    }
  ]
};

await client.api('/teams/e1234567-e123-4276-55555-6232b0e3a89a/channels/a7654321-e321-0000-0000-123b0e3a00a/messages/19:a21b0b0c05194ebc9e30000000000f61@thread.skype')
	.update(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ChatMessageType;
use Microsoft\Graph\Generated\Models\ChatMessageImportance;
use Microsoft\Graph\Generated\Models\ChatMessageFromIdentitySet;
use Microsoft\Graph\Generated\Models\Identity;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageAttachment;
use Microsoft\Graph\Generated\Models\ChatMessageMention;
use Microsoft\Graph\Generated\Models\ChatMessageReaction;
use Microsoft\Graph\Generated\Models\ChatMessageReactionIdentitySet;
use Microsoft\Graph\Generated\Models\ChatMessageHistoryItem;
use Microsoft\Graph\Generated\Models\ChatMessageActions;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$requestBody->setMessageType(new ChatMessageType('message'));
$requestBody->setSubject(null);
$requestBody->setSummary(null);
$requestBody->setImportance(new ChatMessageImportance('normal'));
$requestBody->setLocale('en-us');
$from = new ChatMessageFromIdentitySet();
$from->setApplication(null);
$from->setDevice(null);
$fromUser = new Identity();
$fromUser->setId('3b102402-813e-4e17-a6b2-f841aef1fdfc');
$fromUser->setDisplayName('Lam Cong');
$additionalData = [
	'userIdentityType' => 'aadUser',
];
$fromUser->setAdditionalData($additionalData);
$from->setUser($fromUser);
$additionalData = [
	'conversation' => null,
];
$from->setAdditionalData($additionalData);
$requestBody->setFrom($from);
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('<p><em>text</em></p><attachment id=\"e8f78756199240b88448ae0fc6db112d\"></attachment><attachment id=\"638464e32834471ea202007da60a5ae6\"></attachment>');
$requestBody->setBody($body);
$attachmentsChatMessageAttachment1 = new ChatMessageAttachment();
$attachmentsChatMessageAttachment1->setId('e8f78756199240b88448ae0fc6db112d');
$attachmentsChatMessageAttachment1->setContentType('application/vnd.microsoft.card.hero');
$attachmentsChatMessageAttachment1->setContentUrl(null);
$attachmentsChatMessageAttachment1->setContent('{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you\'re cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"image\": \"https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png\",\r\n      \"title\": \"😃😃 click me 😃😃\",\r\n      \"value\": \"http://microsoft.com\"\r\n    },\r\n    {\r\n      \"type\": \"imback\",\r\n      \"title\": \"&i am back& <>= \"\",\r\n      \"value\": \"&i am back& <>= \"\"\r\n    },\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"title\": \"Open URL\",\r\n      \"value\": \"http://google.com\"\r\n    }\r\n  ]\r\n}');
$attachmentsChatMessageAttachment1->setName(null);
$attachmentsChatMessageAttachment1->setThumbnailUrl(null);
$attachmentsArray []= $attachmentsChatMessageAttachment1;
$attachmentsChatMessageAttachment2 = new ChatMessageAttachment();
$attachmentsChatMessageAttachment2->setId('638464e32834471ea202007da60a5ae6');
$attachmentsChatMessageAttachment2->setContentType('application/vnd.microsoft.card.hero');
$attachmentsChatMessageAttachment2->setContentUrl(null);
$attachmentsChatMessageAttachment2->setContent('{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you\'re cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"&message back& <>= \"\",\r\n      \"text\": \"text = &message back& <>= \"\",\r\n      \"displayText\": \"displayText = &message back& <>= \"\",\r\n      \"value\": {\r\n        \"text\": \"some text 2\"\r\n      }\r\n    }\r\n  ]\r\n}');
$attachmentsChatMessageAttachment2->setName(null);
$attachmentsChatMessageAttachment2->setThumbnailUrl(null);
$attachmentsArray []= $attachmentsChatMessageAttachment2;
$requestBody->setAttachments($attachmentsArray);

$requestBody->setMentions([]);
$reactionsChatMessageReaction1 = new ChatMessageReaction();
$reactionsChatMessageReaction1->setReactionType('angry');
$reactionsChatMessageReaction1->setCreatedDateTime(new \DateTime('2018-10-21T08:10:30.489Z'));
$reactionsChatMessageReaction1User = new ChatMessageReactionIdentitySet();
$reactionsChatMessageReaction1User->setApplication(null);
$reactionsChatMessageReaction1User->setDevice(null);
$reactionsChatMessageReaction1UserUser = new Identity();
$reactionsChatMessageReaction1UserUser->setId('f1b66449-b46d-49b0-9c3c-53c10a5c818e');
$reactionsChatMessageReaction1UserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$reactionsChatMessageReaction1UserUser->setAdditionalData($additionalData);
$reactionsChatMessageReaction1User->setUser($reactionsChatMessageReaction1UserUser);
$reactionsChatMessageReaction1->setUser($reactionsChatMessageReaction1User);
$reactionsArray []= $reactionsChatMessageReaction1;
$reactionsChatMessageReaction2 = new ChatMessageReaction();
$reactionsChatMessageReaction2->setReactionType('laugh');
$reactionsChatMessageReaction2->setCreatedDateTime(new \DateTime('2018-10-21T08:10:32.489Z'));
$reactionsChatMessageReaction2User = new ChatMessageReactionIdentitySet();
$reactionsChatMessageReaction2User->setApplication(null);
$reactionsChatMessageReaction2User->setDevice(null);
$reactionsChatMessageReaction2UserUser = new Identity();
$reactionsChatMessageReaction2UserUser->setId('03a02232-d8f5-4970-a77e-6e8c76ce7a4e');
$reactionsChatMessageReaction2UserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$reactionsChatMessageReaction2UserUser->setAdditionalData($additionalData);
$reactionsChatMessageReaction2User->setUser($reactionsChatMessageReaction2UserUser);
$reactionsChatMessageReaction2->setUser($reactionsChatMessageReaction2User);
$reactionsArray []= $reactionsChatMessageReaction2;
$reactionsChatMessageReaction3 = new ChatMessageReaction();
$reactionsChatMessageReaction3->setReactionType('like');
$reactionsChatMessageReaction3->setCreatedDateTime(new \DateTime('2018-10-21T02:17:14.67Z'));
$reactionsChatMessageReaction3User = new ChatMessageReactionIdentitySet();
$reactionsChatMessageReaction3User->setApplication(null);
$reactionsChatMessageReaction3User->setDevice(null);
$reactionsChatMessageReaction3UserUser = new Identity();
$reactionsChatMessageReaction3UserUser->setId('f1b66449-b46d-49b0-9c3c-53c10a5c818e');
$reactionsChatMessageReaction3UserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$reactionsChatMessageReaction3UserUser->setAdditionalData($additionalData);
$reactionsChatMessageReaction3User->setUser($reactionsChatMessageReaction3UserUser);
$reactionsChatMessageReaction3->setUser($reactionsChatMessageReaction3User);
$reactionsArray []= $reactionsChatMessageReaction3;
$reactionsChatMessageReaction4 = new ChatMessageReaction();
$reactionsChatMessageReaction4->setReactionType('like');
$reactionsChatMessageReaction4->setCreatedDateTime(new \DateTime('2018-10-21T02:34:40.3Z'));
$reactionsChatMessageReaction4User = new ChatMessageReactionIdentitySet();
$reactionsChatMessageReaction4User->setApplication(null);
$reactionsChatMessageReaction4User->setDevice(null);
$reactionsChatMessageReaction4UserUser = new Identity();
$reactionsChatMessageReaction4UserUser->setId('4c9041b7-449a-40f7-8855-56da239b9fd1');
$reactionsChatMessageReaction4UserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$reactionsChatMessageReaction4UserUser->setAdditionalData($additionalData);
$reactionsChatMessageReaction4User->setUser($reactionsChatMessageReaction4UserUser);
$reactionsChatMessageReaction4->setUser($reactionsChatMessageReaction4User);
$reactionsArray []= $reactionsChatMessageReaction4;
$reactionsChatMessageReaction5 = new ChatMessageReaction();
$reactionsChatMessageReaction5->setReactionType('like');
$reactionsChatMessageReaction5->setCreatedDateTime(new \DateTime('2018-10-21T08:10:25.489Z'));
$reactionsChatMessageReaction5User = new ChatMessageReactionIdentitySet();
$reactionsChatMessageReaction5User->setApplication(null);
$reactionsChatMessageReaction5User->setDevice(null);
$reactionsChatMessageReaction5UserUser = new Identity();
$reactionsChatMessageReaction5UserUser->setId('03a02232-d8f5-4970-a77e-6e8c76ce7a4e');
$reactionsChatMessageReaction5UserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$reactionsChatMessageReaction5UserUser->setAdditionalData($additionalData);
$reactionsChatMessageReaction5User->setUser($reactionsChatMessageReaction5UserUser);
$reactionsChatMessageReaction5->setUser($reactionsChatMessageReaction5User);
$reactionsArray []= $reactionsChatMessageReaction5;
$reactionsChatMessageReaction6 = new ChatMessageReaction();
$reactionsChatMessageReaction6->setReactionType('heart');
$reactionsChatMessageReaction6->setCreatedDateTime(new \DateTime('2018-10-21T08:10:31.489Z'));
$reactionsChatMessageReaction6User = new ChatMessageReactionIdentitySet();
$reactionsChatMessageReaction6User->setApplication(null);
$reactionsChatMessageReaction6User->setDevice(null);
$reactionsChatMessageReaction6UserUser = new Identity();
$reactionsChatMessageReaction6UserUser->setId('03a02232-d8f5-4970-a77e-6e8c76ce7a4e');
$reactionsChatMessageReaction6UserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$reactionsChatMessageReaction6UserUser->setAdditionalData($additionalData);
$reactionsChatMessageReaction6User->setUser($reactionsChatMessageReaction6UserUser);
$reactionsChatMessageReaction6->setUser($reactionsChatMessageReaction6User);
$reactionsArray []= $reactionsChatMessageReaction6;
$reactionsChatMessageReaction7 = new ChatMessageReaction();
$reactionsChatMessageReaction7->setReactionType('sad');
$reactionsChatMessageReaction7->setCreatedDateTime(new \DateTime('2018-10-21T08:10:33.489Z'));
$reactionsChatMessageReaction7User = new ChatMessageReactionIdentitySet();
$reactionsChatMessageReaction7User->setApplication(null);
$reactionsChatMessageReaction7User->setDevice(null);
$reactionsChatMessageReaction7UserUser = new Identity();
$reactionsChatMessageReaction7UserUser->setId('03a02232-d8f5-4970-a77e-6e8c76ce7a4e');
$reactionsChatMessageReaction7UserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$reactionsChatMessageReaction7UserUser->setAdditionalData($additionalData);
$reactionsChatMessageReaction7User->setUser($reactionsChatMessageReaction7UserUser);
$reactionsChatMessageReaction7->setUser($reactionsChatMessageReaction7User);
$reactionsArray []= $reactionsChatMessageReaction7;
$reactionsChatMessageReaction8 = new ChatMessageReaction();
$reactionsChatMessageReaction8->setReactionType('surprised');
$reactionsChatMessageReaction8->setCreatedDateTime(new \DateTime('2018-10-21T08:10:34.489Z'));
$reactionsChatMessageReaction8User = new ChatMessageReactionIdentitySet();
$reactionsChatMessageReaction8User->setApplication(null);
$reactionsChatMessageReaction8User->setDevice(null);
$reactionsChatMessageReaction8UserUser = new Identity();
$reactionsChatMessageReaction8UserUser->setId('03a02232-d8f5-4970-a77e-6e8c76ce7a4e');
$reactionsChatMessageReaction8UserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$reactionsChatMessageReaction8UserUser->setAdditionalData($additionalData);
$reactionsChatMessageReaction8User->setUser($reactionsChatMessageReaction8UserUser);
$reactionsChatMessageReaction8->setUser($reactionsChatMessageReaction8User);
$reactionsArray []= $reactionsChatMessageReaction8;
$requestBody->setReactions($reactionsArray);

$messageHistoryChatMessageHistoryItem1 = new ChatMessageHistoryItem();
$messageHistoryChatMessageHistoryItem1->setModifiedDateTime(new \DateTime('2018-10-21T08:10:30.489Z'));
$messageHistoryChatMessageHistoryItem1->setActions(new ChatMessageActions('reactionAdded'));
$messageHistoryChatMessageHistoryItem1Reaction = new ChatMessageReaction();
$messageHistoryChatMessageHistoryItem1Reaction->setReactionType('angry');
$messageHistoryChatMessageHistoryItem1ReactionUser = new ChatMessageReactionIdentitySet();
$messageHistoryChatMessageHistoryItem1ReactionUser->setApplication(null);
$messageHistoryChatMessageHistoryItem1ReactionUser->setDevice(null);
$messageHistoryChatMessageHistoryItem1ReactionUserUser = new Identity();
$messageHistoryChatMessageHistoryItem1ReactionUserUser->setId('f1b66449-b46d-49b0-9c3c-53c10a5c818e');
$messageHistoryChatMessageHistoryItem1ReactionUserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$messageHistoryChatMessageHistoryItem1ReactionUserUser->setAdditionalData($additionalData);
$messageHistoryChatMessageHistoryItem1ReactionUser->setUser($messageHistoryChatMessageHistoryItem1ReactionUserUser);
$messageHistoryChatMessageHistoryItem1Reaction->setUser($messageHistoryChatMessageHistoryItem1ReactionUser);
$messageHistoryChatMessageHistoryItem1->setReaction($messageHistoryChatMessageHistoryItem1Reaction);
$messageHistoryArray []= $messageHistoryChatMessageHistoryItem1;
$messageHistoryChatMessageHistoryItem2 = new ChatMessageHistoryItem();
$messageHistoryChatMessageHistoryItem2->setModifiedDateTime(new \DateTime('2018-10-21T08:10:32.489Z'));
$messageHistoryChatMessageHistoryItem2->setActions(new ChatMessageActions('reactionAdded'));
$messageHistoryChatMessageHistoryItem2Reaction = new ChatMessageReaction();
$messageHistoryChatMessageHistoryItem2Reaction->setReactionType('laugh');
$messageHistoryChatMessageHistoryItem2ReactionUser = new ChatMessageReactionIdentitySet();
$messageHistoryChatMessageHistoryItem2ReactionUser->setApplication(null);
$messageHistoryChatMessageHistoryItem2ReactionUser->setDevice(null);
$messageHistoryChatMessageHistoryItem2ReactionUserUser = new Identity();
$messageHistoryChatMessageHistoryItem2ReactionUserUser->setId('03a02232-d8f5-4970-a77e-6e8c76ce7a4e');
$messageHistoryChatMessageHistoryItem2ReactionUserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$messageHistoryChatMessageHistoryItem2ReactionUserUser->setAdditionalData($additionalData);
$messageHistoryChatMessageHistoryItem2ReactionUser->setUser($messageHistoryChatMessageHistoryItem2ReactionUserUser);
$messageHistoryChatMessageHistoryItem2Reaction->setUser($messageHistoryChatMessageHistoryItem2ReactionUser);
$messageHistoryChatMessageHistoryItem2->setReaction($messageHistoryChatMessageHistoryItem2Reaction);
$messageHistoryArray []= $messageHistoryChatMessageHistoryItem2;
$messageHistoryChatMessageHistoryItem3 = new ChatMessageHistoryItem();
$messageHistoryChatMessageHistoryItem3->setModifiedDateTime(new \DateTime('2018-10-21T02:17:14.67Z'));
$messageHistoryChatMessageHistoryItem3->setActions(new ChatMessageActions('reactionAdded'));
$messageHistoryChatMessageHistoryItem3Reaction = new ChatMessageReaction();
$messageHistoryChatMessageHistoryItem3Reaction->setReactionType('like');
$messageHistoryChatMessageHistoryItem3ReactionUser = new ChatMessageReactionIdentitySet();
$messageHistoryChatMessageHistoryItem3ReactionUser->setApplication(null);
$messageHistoryChatMessageHistoryItem3ReactionUser->setDevice(null);
$messageHistoryChatMessageHistoryItem3ReactionUserUser = new Identity();
$messageHistoryChatMessageHistoryItem3ReactionUserUser->setId('f1b66449-b46d-49b0-9c3c-53c10a5c818e');
$messageHistoryChatMessageHistoryItem3ReactionUserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$messageHistoryChatMessageHistoryItem3ReactionUserUser->setAdditionalData($additionalData);
$messageHistoryChatMessageHistoryItem3ReactionUser->setUser($messageHistoryChatMessageHistoryItem3ReactionUserUser);
$messageHistoryChatMessageHistoryItem3Reaction->setUser($messageHistoryChatMessageHistoryItem3ReactionUser);
$messageHistoryChatMessageHistoryItem3->setReaction($messageHistoryChatMessageHistoryItem3Reaction);
$messageHistoryArray []= $messageHistoryChatMessageHistoryItem3;
$messageHistoryChatMessageHistoryItem4 = new ChatMessageHistoryItem();
$messageHistoryChatMessageHistoryItem4->setModifiedDateTime(new \DateTime('2018-10-21T02:34:40.3Z'));
$messageHistoryChatMessageHistoryItem4->setActions(new ChatMessageActions('reactionAdded'));
$messageHistoryChatMessageHistoryItem4Reaction = new ChatMessageReaction();
$messageHistoryChatMessageHistoryItem4Reaction->setReactionType('like');
$messageHistoryChatMessageHistoryItem4ReactionUser = new ChatMessageReactionIdentitySet();
$messageHistoryChatMessageHistoryItem4ReactionUser->setApplication(null);
$messageHistoryChatMessageHistoryItem4ReactionUser->setDevice(null);
$messageHistoryChatMessageHistoryItem4ReactionUserUser = new Identity();
$messageHistoryChatMessageHistoryItem4ReactionUserUser->setId('4c9041b7-449a-40f7-8855-56da239b9fd1');
$messageHistoryChatMessageHistoryItem4ReactionUserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$messageHistoryChatMessageHistoryItem4ReactionUserUser->setAdditionalData($additionalData);
$messageHistoryChatMessageHistoryItem4ReactionUser->setUser($messageHistoryChatMessageHistoryItem4ReactionUserUser);
$messageHistoryChatMessageHistoryItem4Reaction->setUser($messageHistoryChatMessageHistoryItem4ReactionUser);
$messageHistoryChatMessageHistoryItem4->setReaction($messageHistoryChatMessageHistoryItem4Reaction);
$messageHistoryArray []= $messageHistoryChatMessageHistoryItem4;
$messageHistoryChatMessageHistoryItem5 = new ChatMessageHistoryItem();
$messageHistoryChatMessageHistoryItem5->setModifiedDateTime(new \DateTime('2018-10-21T08:10:25.489Z'));
$messageHistoryChatMessageHistoryItem5->setActions(new ChatMessageActions('reactionAdded'));
$messageHistoryChatMessageHistoryItem5Reaction = new ChatMessageReaction();
$messageHistoryChatMessageHistoryItem5Reaction->setReactionType('like');
$messageHistoryChatMessageHistoryItem5ReactionUser = new ChatMessageReactionIdentitySet();
$messageHistoryChatMessageHistoryItem5ReactionUser->setApplication(null);
$messageHistoryChatMessageHistoryItem5ReactionUser->setDevice(null);
$messageHistoryChatMessageHistoryItem5ReactionUserUser = new Identity();
$messageHistoryChatMessageHistoryItem5ReactionUserUser->setId('03a02232-d8f5-4970-a77e-6e8c76ce7a4e');
$messageHistoryChatMessageHistoryItem5ReactionUserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$messageHistoryChatMessageHistoryItem5ReactionUserUser->setAdditionalData($additionalData);
$messageHistoryChatMessageHistoryItem5ReactionUser->setUser($messageHistoryChatMessageHistoryItem5ReactionUserUser);
$messageHistoryChatMessageHistoryItem5Reaction->setUser($messageHistoryChatMessageHistoryItem5ReactionUser);
$messageHistoryChatMessageHistoryItem5->setReaction($messageHistoryChatMessageHistoryItem5Reaction);
$messageHistoryArray []= $messageHistoryChatMessageHistoryItem5;
$messageHistoryChatMessageHistoryItem6 = new ChatMessageHistoryItem();
$messageHistoryChatMessageHistoryItem6->setModifiedDateTime(new \DateTime('2018-10-21T08:10:31.489Z'));
$messageHistoryChatMessageHistoryItem6->setActions(new ChatMessageActions('reactionAdded'));
$messageHistoryChatMessageHistoryItem6Reaction = new ChatMessageReaction();
$messageHistoryChatMessageHistoryItem6Reaction->setReactionType('heart');
$messageHistoryChatMessageHistoryItem6ReactionUser = new ChatMessageReactionIdentitySet();
$messageHistoryChatMessageHistoryItem6ReactionUser->setApplication(null);
$messageHistoryChatMessageHistoryItem6ReactionUser->setDevice(null);
$messageHistoryChatMessageHistoryItem6ReactionUserUser = new Identity();
$messageHistoryChatMessageHistoryItem6ReactionUserUser->setId('03a02232-d8f5-4970-a77e-6e8c76ce7a4e');
$messageHistoryChatMessageHistoryItem6ReactionUserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$messageHistoryChatMessageHistoryItem6ReactionUserUser->setAdditionalData($additionalData);
$messageHistoryChatMessageHistoryItem6ReactionUser->setUser($messageHistoryChatMessageHistoryItem6ReactionUserUser);
$messageHistoryChatMessageHistoryItem6Reaction->setUser($messageHistoryChatMessageHistoryItem6ReactionUser);
$messageHistoryChatMessageHistoryItem6->setReaction($messageHistoryChatMessageHistoryItem6Reaction);
$messageHistoryArray []= $messageHistoryChatMessageHistoryItem6;
$messageHistoryChatMessageHistoryItem7 = new ChatMessageHistoryItem();
$messageHistoryChatMessageHistoryItem7->setModifiedDateTime(new \DateTime('2018-10-21T08:10:33.489Z'));
$messageHistoryChatMessageHistoryItem7->setActions(new ChatMessageActions('reactionAdded'));
$messageHistoryChatMessageHistoryItem7Reaction = new ChatMessageReaction();
$messageHistoryChatMessageHistoryItem7Reaction->setReactionType('sad');
$messageHistoryChatMessageHistoryItem7ReactionUser = new ChatMessageReactionIdentitySet();
$messageHistoryChatMessageHistoryItem7ReactionUser->setApplication(null);
$messageHistoryChatMessageHistoryItem7ReactionUser->setDevice(null);
$messageHistoryChatMessageHistoryItem7ReactionUserUser = new Identity();
$messageHistoryChatMessageHistoryItem7ReactionUserUser->setId('03a02232-d8f5-4970-a77e-6e8c76ce7a4e');
$messageHistoryChatMessageHistoryItem7ReactionUserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$messageHistoryChatMessageHistoryItem7ReactionUserUser->setAdditionalData($additionalData);
$messageHistoryChatMessageHistoryItem7ReactionUser->setUser($messageHistoryChatMessageHistoryItem7ReactionUserUser);
$messageHistoryChatMessageHistoryItem7Reaction->setUser($messageHistoryChatMessageHistoryItem7ReactionUser);
$messageHistoryChatMessageHistoryItem7->setReaction($messageHistoryChatMessageHistoryItem7Reaction);
$messageHistoryArray []= $messageHistoryChatMessageHistoryItem7;
$messageHistoryChatMessageHistoryItem8 = new ChatMessageHistoryItem();
$messageHistoryChatMessageHistoryItem8->setModifiedDateTime(new \DateTime('2018-10-21T08:10:34.489Z'));
$messageHistoryChatMessageHistoryItem8->setActions(new ChatMessageActions('surprised'));
$messageHistoryChatMessageHistoryItem8Reaction = new ChatMessageReaction();
$messageHistoryChatMessageHistoryItem8Reaction->setReactionType('sad');
$messageHistoryChatMessageHistoryItem8ReactionUser = new ChatMessageReactionIdentitySet();
$messageHistoryChatMessageHistoryItem8ReactionUser->setApplication(null);
$messageHistoryChatMessageHistoryItem8ReactionUser->setDevice(null);
$messageHistoryChatMessageHistoryItem8ReactionUserUser = new Identity();
$messageHistoryChatMessageHistoryItem8ReactionUserUser->setId('03a02232-d8f5-4970-a77e-6e8c76ce7a4e');
$messageHistoryChatMessageHistoryItem8ReactionUserUser->setDisplayName(null);
$additionalData = [
'userIdentityType' => 'aadUser',
];
$messageHistoryChatMessageHistoryItem8ReactionUserUser->setAdditionalData($additionalData);
$messageHistoryChatMessageHistoryItem8ReactionUser->setUser($messageHistoryChatMessageHistoryItem8ReactionUserUser);
$messageHistoryChatMessageHistoryItem8Reaction->setUser($messageHistoryChatMessageHistoryItem8ReactionUser);
$messageHistoryChatMessageHistoryItem8->setReaction($messageHistoryChatMessageHistoryItem8Reaction);
$messageHistoryArray []= $messageHistoryChatMessageHistoryItem8;
$requestBody->setMessageHistory($messageHistoryArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->byChatMessageId('chatMessage-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	messageType = "message"
	subject = $null
	summary = $null
	importance = "normal"
	locale = "en-us"
	from = @{
		application = $null
		device = $null
		user = @{
			id = "3b102402-813e-4e17-a6b2-f841aef1fdfc"
			displayName = "Lam Cong"
			userIdentityType = "aadUser"
		}
		conversation = $null
	}
	body = @{
		contentType = "html"
		content = "<p><em>text</em></p><attachment id="e8f78756199240b88448ae0fc6db112d"></attachment><attachment id="638464e32834471ea202007da60a5ae6"></attachment>"
	}
	attachments = @(
		@{
			id = "e8f78756199240b88448ae0fc6db112d"
			contentType = "application/vnd.microsoft.card.hero"
			contentUrl = $null
			content = '{
  "title": "*title*",
  "subtitle": "*subtitle*",
  "text": "Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.",
  "images": [
    {
      "url": "https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview"
    }
  ],
  "buttons": [
    {
      "type": "openUrl",
      "image": "https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png",
      "title": "😃😃 click me 😃😃",
      "value": "http://microsoft.com"
    },
    {
      "type": "imback",
      "title": "&i am back& <>= \"",
      "value": "&i am back& <>= \""
    },
    {
      "type": "openUrl",
      "title": "Open URL",
      "value": "http://google.com"
    }
  ]
}'
			name = $null
			thumbnailUrl = $null
		}
		@{
			id = "638464e32834471ea202007da60a5ae6"
			contentType = "application/vnd.microsoft.card.hero"
			contentUrl = $null
			content = '{
  "title": "*title*",
  "subtitle": "*subtitle*",
  "text": "Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.",
  "images": [
    {
      "url": "https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview"
    }
  ],
  "buttons": [
    {
      "type": "messageBack",
      "title": "&message back& <>= \"",
      "text": "text = &message back& <>= \"",
      "displayText": "displayText = &message back& <>= \"",
      "value": {
        "text": "some text 2"
      }
    }
  ]
}'
			name = $null
			thumbnailUrl = $null
		}
	)
	mentions = @(
	)
	reactions = @(
		@{
			reactionType = "angry"
			createdDateTime = [System.DateTime]::Parse("2018-10-21T08:10:30.489Z")
			user = @{
				application = $null
				device = $null
				user = @{
					id = "f1b66449-b46d-49b0-9c3c-53c10a5c818e"
					displayName = $null
					userIdentityType = "aadUser"
				}
			}
		}
		@{
			reactionType = "laugh"
			createdDateTime = [System.DateTime]::Parse("2018-10-21T08:10:32.489Z")
			user = @{
				application = $null
				device = $null
				user = @{
					id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
					displayName = $null
					userIdentityType = "aadUser"
				}
			}
		}
		@{
			reactionType = "like"
			createdDateTime = [System.DateTime]::Parse("2018-10-21T02:17:14.67Z")
			user = @{
				application = $null
				device = $null
				user = @{
					id = "f1b66449-b46d-49b0-9c3c-53c10a5c818e"
					displayName = $null
					userIdentityType = "aadUser"
				}
			}
		}
		@{
			reactionType = "like"
			createdDateTime = [System.DateTime]::Parse("2018-10-21T02:34:40.3Z")
			user = @{
				application = $null
				device = $null
				user = @{
					id = "4c9041b7-449a-40f7-8855-56da239b9fd1"
					displayName = $null
					userIdentityType = "aadUser"
				}
			}
		}
		@{
			reactionType = "like"
			createdDateTime = [System.DateTime]::Parse("2018-10-21T08:10:25.489Z")
			user = @{
				application = $null
				device = $null
				user = @{
					id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
					displayName = $null
					userIdentityType = "aadUser"
				}
			}
		}
		@{
			reactionType = "heart"
			createdDateTime = [System.DateTime]::Parse("2018-10-21T08:10:31.489Z")
			user = @{
				application = $null
				device = $null
				user = @{
					id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
					displayName = $null
					userIdentityType = "aadUser"
				}
			}
		}
		@{
			reactionType = "sad"
			createdDateTime = [System.DateTime]::Parse("2018-10-21T08:10:33.489Z")
			user = @{
				application = $null
				device = $null
				user = @{
					id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
					displayName = $null
					userIdentityType = "aadUser"
				}
			}
		}
		@{
			reactionType = "surprised"
			createdDateTime = [System.DateTime]::Parse("2018-10-21T08:10:34.489Z")
			user = @{
				application = $null
				device = $null
				user = @{
					id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
					displayName = $null
					userIdentityType = "aadUser"
				}
			}
		}
	)
	messageHistory = @(
		@{
			modifiedDateTime = [System.DateTime]::Parse("2018-10-21T08:10:30.489Z")
			actions = "reactionAdded"
			reaction = @{
				reactionType = "angry"
				user = @{
					application = $null
					device = $null
					user = @{
						id = "f1b66449-b46d-49b0-9c3c-53c10a5c818e"
						displayName = $null
						userIdentityType = "aadUser"
					}
				}
			}
		}
		@{
			modifiedDateTime = [System.DateTime]::Parse("2018-10-21T08:10:32.489Z")
			actions = "reactionAdded"
			reaction = @{
				reactionType = "laugh"
				user = @{
					application = $null
					device = $null
					user = @{
						id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
						displayName = $null
						userIdentityType = "aadUser"
					}
				}
			}
		}
		@{
			modifiedDateTime = [System.DateTime]::Parse("2018-10-21T02:17:14.67Z")
			actions = "reactionAdded"
			reaction = @{
				reactionType = "like"
				user = @{
					application = $null
					device = $null
					user = @{
						id = "f1b66449-b46d-49b0-9c3c-53c10a5c818e"
						displayName = $null
						userIdentityType = "aadUser"
					}
				}
			}
		}
		@{
			modifiedDateTime = [System.DateTime]::Parse("2018-10-21T02:34:40.3Z")
			actions = "reactionAdded"
			reaction = @{
				reactionType = "like"
				user = @{
					application = $null
					device = $null
					user = @{
						id = "4c9041b7-449a-40f7-8855-56da239b9fd1"
						displayName = $null
						userIdentityType = "aadUser"
					}
				}
			}
		}
		@{
			modifiedDateTime = [System.DateTime]::Parse("2018-10-21T08:10:25.489Z")
			actions = "reactionAdded"
			reaction = @{
				reactionType = "like"
				user = @{
					application = $null
					device = $null
					user = @{
						id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
						displayName = $null
						userIdentityType = "aadUser"
					}
				}
			}
		}
		@{
			modifiedDateTime = [System.DateTime]::Parse("2018-10-21T08:10:31.489Z")
			actions = "reactionAdded"
			reaction = @{
				reactionType = "heart"
				user = @{
					application = $null
					device = $null
					user = @{
						id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
						displayName = $null
						userIdentityType = "aadUser"
					}
				}
			}
		}
		@{
			modifiedDateTime = [System.DateTime]::Parse("2018-10-21T08:10:33.489Z")
			actions = "reactionAdded"
			reaction = @{
				reactionType = "sad"
				user = @{
					application = $null
					device = $null
					user = @{
						id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
						displayName = $null
						userIdentityType = "aadUser"
					}
				}
			}
		}
		@{
			modifiedDateTime = [System.DateTime]::Parse("2018-10-21T08:10:34.489Z")
			actions = "surprised"
			reaction = @{
				reactionType = "sad"
				user = @{
					application = $null
					device = $null
					user = @{
						id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e"
						displayName = $null
						userIdentityType = "aadUser"
					}
				}
			}
		}
	)
}

Update-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -ChatMessageId $chatMessageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.chat_message_type import ChatMessageType
from msgraph.generated.models.chat_message_importance import ChatMessageImportance
from msgraph.generated.models.chat_message_from_identity_set import ChatMessageFromIdentitySet
from msgraph.generated.models.identity import Identity
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_attachment import ChatMessageAttachment
from msgraph.generated.models.chat_message_mention import ChatMessageMention
from msgraph.generated.models.chat_message_reaction import ChatMessageReaction
from msgraph.generated.models.chat_message_reaction_identity_set import ChatMessageReactionIdentitySet
from msgraph.generated.models.chat_message_history_item import ChatMessageHistoryItem
from msgraph.generated.models.chat_message_actions import ChatMessageActions
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	message_type = ChatMessageType.Message,
	subject = None,
	summary = None,
	importance = ChatMessageImportance.Normal,
	locale = "en-us",
	from = ChatMessageFromIdentitySet(
		application = None,
		device = None,
		user = Identity(
			id = "3b102402-813e-4e17-a6b2-f841aef1fdfc",
			display_name = "Lam Cong",
			additional_data = {
					"user_identity_type" : "aadUser",
			}
		),
		additional_data = {
				"conversation" : None,
		}
	),
	body = ItemBody(
		content_type = BodyType.Html,
		content = "<p><em>text</em></p><attachment id=\"e8f78756199240b88448ae0fc6db112d\"></attachment><attachment id=\"638464e32834471ea202007da60a5ae6\"></attachment>",
	),
	attachments = [
		ChatMessageAttachment(
			id = "e8f78756199240b88448ae0fc6db112d",
			content_type = "application/vnd.microsoft.card.hero",
			content_url = None,
			content = "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"image\": \"https://urlp.asm.skype.com/v1/url/content?url=https%3a%2f%2fcdn2.iconfinder.com%2fdata%2ficons%2fsocial-icons-33%2f128%2fTrello-128.png\",\r\n      \"title\": \"😃😃 click me 😃😃\",\r\n      \"value\": \"http://microsoft.com\"\r\n    },\r\n    {\r\n      \"type\": \"imback\",\r\n      \"title\": \"&i am back& <>= \"\",\r\n      \"value\": \"&i am back& <>= \"\"\r\n    },\r\n    {\r\n      \"type\": \"openUrl\",\r\n      \"title\": \"Open URL\",\r\n      \"value\": \"http://google.com\"\r\n    }\r\n  ]\r\n}",
			name = None,
			thumbnail_url = None,
		),
		ChatMessageAttachment(
			id = "638464e32834471ea202007da60a5ae6",
			content_type = "application/vnd.microsoft.card.hero",
			content_url = None,
			content = "{\r\n  \"title\": \"*title*\",\r\n  \"subtitle\": \"*subtitle*\",\r\n  \"text\": \"Have you found yourself scratching your head trying to figure these questions out? Frustrated trying to access some of the goodies unique to the Microsoft Teams platform?  Well, fear not, Bot Builder SDK Extension for Teams in .NET and Node flavors is here!  Just head on over to Nuget or NPM to download our tasty helpers, sure to speed up your prep time so you can spend more time maximizing the flavor of the bots you're cooking up.Here’s a small sample of some recipes to whet your appetite.\",\r\n  \"images\": [\r\n    {\r\n      \"url\": \"https://us-api.asm.skype.com/v1/objects/0-eus-d8-ced0c9567ee7b0b233b987bd32f9eacd/views/img_preview\"\r\n    }\r\n  ],\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"&message back& <>= \"\",\r\n      \"text\": \"text = &message back& <>= \"\",\r\n      \"displayText\": \"displayText = &message back& <>= \"\",\r\n      \"value\": {\r\n        \"text\": \"some text 2\"\r\n      }\r\n    }\r\n  ]\r\n}",
			name = None,
			thumbnail_url = None,
		),
	],
	mentions = [
	],
	reactions = [
		ChatMessageReaction(
			reaction_type = "angry",
			created_date_time = "2018-10-21T08:10:30.489Z",
			user = ChatMessageReactionIdentitySet(
				application = None,
				device = None,
				user = Identity(
					id = "f1b66449-b46d-49b0-9c3c-53c10a5c818e",
					display_name = None,
					additional_data = {
							"user_identity_type" : "aadUser",
					}
				),
			),
		),
		ChatMessageReaction(
			reaction_type = "laugh",
			created_date_time = "2018-10-21T08:10:32.489Z",
			user = ChatMessageReactionIdentitySet(
				application = None,
				device = None,
				user = Identity(
					id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
					display_name = None,
					additional_data = {
							"user_identity_type" : "aadUser",
					}
				),
			),
		),
		ChatMessageReaction(
			reaction_type = "like",
			created_date_time = "2018-10-21T02:17:14.67Z",
			user = ChatMessageReactionIdentitySet(
				application = None,
				device = None,
				user = Identity(
					id = "f1b66449-b46d-49b0-9c3c-53c10a5c818e",
					display_name = None,
					additional_data = {
							"user_identity_type" : "aadUser",
					}
				),
			),
		),
		ChatMessageReaction(
			reaction_type = "like",
			created_date_time = "2018-10-21T02:34:40.3Z",
			user = ChatMessageReactionIdentitySet(
				application = None,
				device = None,
				user = Identity(
					id = "4c9041b7-449a-40f7-8855-56da239b9fd1",
					display_name = None,
					additional_data = {
							"user_identity_type" : "aadUser",
					}
				),
			),
		),
		ChatMessageReaction(
			reaction_type = "like",
			created_date_time = "2018-10-21T08:10:25.489Z",
			user = ChatMessageReactionIdentitySet(
				application = None,
				device = None,
				user = Identity(
					id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
					display_name = None,
					additional_data = {
							"user_identity_type" : "aadUser",
					}
				),
			),
		),
		ChatMessageReaction(
			reaction_type = "heart",
			created_date_time = "2018-10-21T08:10:31.489Z",
			user = ChatMessageReactionIdentitySet(
				application = None,
				device = None,
				user = Identity(
					id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
					display_name = None,
					additional_data = {
							"user_identity_type" : "aadUser",
					}
				),
			),
		),
		ChatMessageReaction(
			reaction_type = "sad",
			created_date_time = "2018-10-21T08:10:33.489Z",
			user = ChatMessageReactionIdentitySet(
				application = None,
				device = None,
				user = Identity(
					id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
					display_name = None,
					additional_data = {
							"user_identity_type" : "aadUser",
					}
				),
			),
		),
		ChatMessageReaction(
			reaction_type = "surprised",
			created_date_time = "2018-10-21T08:10:34.489Z",
			user = ChatMessageReactionIdentitySet(
				application = None,
				device = None,
				user = Identity(
					id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
					display_name = None,
					additional_data = {
							"user_identity_type" : "aadUser",
					}
				),
			),
		),
	],
	message_history = [
		ChatMessageHistoryItem(
			modified_date_time = "2018-10-21T08:10:30.489Z",
			actions = ChatMessageActions.ReactionAdded,
			reaction = ChatMessageReaction(
				reaction_type = "angry",
				user = ChatMessageReactionIdentitySet(
					application = None,
					device = None,
					user = Identity(
						id = "f1b66449-b46d-49b0-9c3c-53c10a5c818e",
						display_name = None,
						additional_data = {
								"user_identity_type" : "aadUser",
						}
					),
				),
			),
		),
		ChatMessageHistoryItem(
			modified_date_time = "2018-10-21T08:10:32.489Z",
			actions = ChatMessageActions.ReactionAdded,
			reaction = ChatMessageReaction(
				reaction_type = "laugh",
				user = ChatMessageReactionIdentitySet(
					application = None,
					device = None,
					user = Identity(
						id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
						display_name = None,
						additional_data = {
								"user_identity_type" : "aadUser",
						}
					),
				),
			),
		),
		ChatMessageHistoryItem(
			modified_date_time = "2018-10-21T02:17:14.67Z",
			actions = ChatMessageActions.ReactionAdded,
			reaction = ChatMessageReaction(
				reaction_type = "like",
				user = ChatMessageReactionIdentitySet(
					application = None,
					device = None,
					user = Identity(
						id = "f1b66449-b46d-49b0-9c3c-53c10a5c818e",
						display_name = None,
						additional_data = {
								"user_identity_type" : "aadUser",
						}
					),
				),
			),
		),
		ChatMessageHistoryItem(
			modified_date_time = "2018-10-21T02:34:40.3Z",
			actions = ChatMessageActions.ReactionAdded,
			reaction = ChatMessageReaction(
				reaction_type = "like",
				user = ChatMessageReactionIdentitySet(
					application = None,
					device = None,
					user = Identity(
						id = "4c9041b7-449a-40f7-8855-56da239b9fd1",
						display_name = None,
						additional_data = {
								"user_identity_type" : "aadUser",
						}
					),
				),
			),
		),
		ChatMessageHistoryItem(
			modified_date_time = "2018-10-21T08:10:25.489Z",
			actions = ChatMessageActions.ReactionAdded,
			reaction = ChatMessageReaction(
				reaction_type = "like",
				user = ChatMessageReactionIdentitySet(
					application = None,
					device = None,
					user = Identity(
						id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
						display_name = None,
						additional_data = {
								"user_identity_type" : "aadUser",
						}
					),
				),
			),
		),
		ChatMessageHistoryItem(
			modified_date_time = "2018-10-21T08:10:31.489Z",
			actions = ChatMessageActions.ReactionAdded,
			reaction = ChatMessageReaction(
				reaction_type = "heart",
				user = ChatMessageReactionIdentitySet(
					application = None,
					device = None,
					user = Identity(
						id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
						display_name = None,
						additional_data = {
								"user_identity_type" : "aadUser",
						}
					),
				),
			),
		),
		ChatMessageHistoryItem(
			modified_date_time = "2018-10-21T08:10:33.489Z",
			actions = ChatMessageActions.ReactionAdded,
			reaction = ChatMessageReaction(
				reaction_type = "sad",
				user = ChatMessageReactionIdentitySet(
					application = None,
					device = None,
					user = Identity(
						id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
						display_name = None,
						additional_data = {
								"user_identity_type" : "aadUser",
						}
					),
				),
			),
		),
		ChatMessageHistoryItem(
			modified_date_time = "2018-10-21T08:10:34.489Z",
			actions = ChatMessageActions.ReactionAdded,
			reaction = ChatMessageReaction(
				reaction_type = "sad",
				user = ChatMessageReactionIdentitySet(
					application = None,
					device = None,
					user = Identity(
						id = "03a02232-d8f5-4970-a77e-6e8c76ce7a4e",
						display_name = None,
						additional_data = {
								"user_identity_type" : "aadUser",
						}
					),
				),
			),
		),
	],
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.by_chat_message_id('chatMessage-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
