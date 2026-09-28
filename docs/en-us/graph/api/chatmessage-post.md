<!-- Source: https://learn.microsoft.com/en-us/graph/api/chatmessage-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# Send chatMessage in a channel or a chat

Namespace: microsoft.graph

Send a new [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) in the specified [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) or a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0).

> **Notes:**
> 
> - We don't recommend that you use this API for data migration via the standard create message flow. For data migration scenarios, use the [import messages](https://learn.microsoft.com/en-us/graph/teams-import-messages) flow instead.
> - It is a violation of the [terms of use](https://learn.microsoft.com/en-us/legal/microsoft-apis/terms-of-use) to use Microsoft Teams as a log file. Only send messages that people will read.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

### Permissions for channel

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ChannelMessage.Send | Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Teamwork.Migrate.All | Not available. |

Note

- The Group.ReadWrite.All permission is supported only for backward compatibility. We recommend that you update your solutions to use the alternative permissions listed in the table.
- Application permissions are only supported for [migration](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/import-messages/import-external-messages-to-teams). In the future, Microsoft might require you or your customers to pay additional fees based on the amount of data imported.

### Permissions for chat

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ChannelMessage.Send | Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Teamwork.Migrate.All | Not available. |

## HTTP request

**Sending message in a channel**

```http
POST /teams/{team-id}/channels/{channel-id}/messages
```

**Sending replies in a channel**

```http
POST /teams/{team-id}/channels/{channel-id}/messages/{message-id}/replies
```

**Sending message in a chat**

```http
POST /chats/{chat-id}/messages
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {code}. Required. |
| Content-type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) object. Only the body property is mandatory; other properties are optional.

## Response

If successful, this method returns a `201 Created` response code and a new [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) object in the response body.

## Examples

In the following examples, the URL can use the [HTTP syntax](#http-request) described to [send a message to a chat](https://learn.microsoft.com/en-us/graph/api/chat-post-messages?view=graph-rest-1.0), [send a message to a channel](https://learn.microsoft.com/en-us/graph/api/channel-post-messages?view=graph-rest-1.0), or [send reply to a channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-post-replies?view=graph-rest-1.0).

Note

The Teams client has specific HTML restrictions. Therefore, the HTML elements supported by the Microsoft Graph API are compatible with the Teams client. For example, certain elements like `<div>` and inline styles may not function as intended.

### Example 1: Send a Hello World message in a channel

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
POST https://graph.microsoft.com/v1.0/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2/messages
Content-type: application/json

{
  "body": {
    "content": "Hello World"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ChatMessage
{
	Body = new ItemBody
	{
		Content = "Hello World",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages.PostAsync(requestBody);
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
body := graphmodels.NewItemBody()
content := "Hello World"
body.SetContent(&content) 
requestBody.SetBody(body)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
ItemBody body = new ItemBody();
body.setContent("Hello World");
chatMessage.setBody(body);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
  body: {
    content: 'Hello World'
  }
};

await client.api('/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$body = new ItemBody();
$body->setContent('Hello World');
$requestBody->setBody($body);

$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	body = @{
		content = "Hello World"
	}
}

New-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	body = ItemBody(
		content = "Hello World",
	),
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('fbe2bf47-16c8-47cf-b4a5-4b9b187c508b')/channels('19%3A4a95f7d8db4c4e7fae857bcebe0623e6%40thread.tacv2')/messages/$entity",
    "id": "1616990032035",
    "replyToId": null,
    "etag": "1616990032035",
    "messageType": "message",
    "createdDateTime": "2021-03-29T03:53:52.035Z",
    "lastModifiedDateTime": "2021-03-29T03:53:52.035Z",
    "lastEditedDateTime": null,
    "deletedDateTime": null,
    "subject": null,
    "summary": null,
    "chatId": null,
    "importance": "normal",
    "locale": "en-us",
    "webUrl": "https://teams.microsoft.com/l/message/19%3A4a95f7d8db4c4e7fae857bcebe0623e6%40thread.tacv2/1616990032035?groupId=fbe2bf47-16c8-47cf-b4a5-4b9b187c508b&tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34&createdTime=1616990032035&parentMessageId=1616990032035",
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "user": {
            "@odata.type": "#microsoft.graph.teamworkUserIdentity",
            "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
            "displayName": "Robin Kline",
            "userIdentityType": "aadUser",
            "tenantId": "e61ef81e-8bd8-476a-92e8-4a62f8426fca"
        }
    },
    "body": {
        "contentType": "text",
        "content": "Hello World"
    },
    "channelIdentity": {
        "teamId": "fbe2bf47-16c8-47cf-b4a5-4b9b187c508b",
        "channelId": "19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2"
    },
    "attachments": [],
    "mentions": [],
    "reactions": [],
    "messageHistory": []
}
```

### Example 2: @mentions a user in a channel message

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
POST https://graph.microsoft.com/v1.0/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2/messages
Content-type: application/json

{
  "body": {
    "contentType": "html",
    "content": "Hello World <at id=\"0\">Jane Smith</at>"
  },
  "mentions": [
    {
      "id": 0,
      "mentionText": "Jane Smith",
      "mentioned": {
        "user": {
          "displayName": "Jane Smith",
          "id": "ef1c916a-3135-4417-ba27-8eb7bd084193",
          "userIdentityType": "aadUser"
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
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "Hello World <at id=\"0\">Jane Smith</at>",
	},
	Mentions = new List<ChatMessageMention>
	{
		new ChatMessageMention
		{
			Id = 0,
			MentionText = "Jane Smith",
			Mentioned = new ChatMessageMentionedIdentitySet
			{
				User = new Identity
				{
					DisplayName = "Jane Smith",
					Id = "ef1c916a-3135-4417-ba27-8eb7bd084193",
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
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages.PostAsync(requestBody);
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
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "Hello World <at id=\"0\">Jane Smith</at>"
body.SetContent(&content) 
requestBody.SetBody(body)


chatMessageMention := graphmodels.NewChatMessageMention()
id := int32(0)
chatMessageMention.SetId(&id) 
mentionText := "Jane Smith"
chatMessageMention.SetMentionText(&mentionText) 
mentioned := graphmodels.NewChatMessageMentionedIdentitySet()
user := graphmodels.NewIdentity()
displayName := "Jane Smith"
user.SetDisplayName(&displayName) 
id := "ef1c916a-3135-4417-ba27-8eb7bd084193"
user.SetId(&id) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
mentioned.SetUser(user)
chatMessageMention.SetMentioned(mentioned)

mentions := []graphmodels.ChatMessageMentionable {
	chatMessageMention,
}
requestBody.SetMentions(mentions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("Hello World <at id=\"0\">Jane Smith</at>");
chatMessage.setBody(body);
LinkedList<ChatMessageMention> mentions = new LinkedList<ChatMessageMention>();
ChatMessageMention chatMessageMention = new ChatMessageMention();
chatMessageMention.setId(0);
chatMessageMention.setMentionText("Jane Smith");
ChatMessageMentionedIdentitySet mentioned = new ChatMessageMentionedIdentitySet();
Identity user = new Identity();
user.setDisplayName("Jane Smith");
user.setId("ef1c916a-3135-4417-ba27-8eb7bd084193");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("userIdentityType", "aadUser");
user.setAdditionalData(additionalData);
mentioned.setUser(user);
chatMessageMention.setMentioned(mentioned);
mentions.add(chatMessageMention);
chatMessage.setMentions(mentions);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
  body: {
    contentType: 'html',
    content: 'Hello World <at id=\"0\">Jane Smith</at>'
  },
  mentions: [
    {
      id: 0,
      mentionText: 'Jane Smith',
      mentioned: {
        user: {
          displayName: 'Jane Smith',
          id: 'ef1c916a-3135-4417-ba27-8eb7bd084193',
          userIdentityType: 'aadUser'
        }
      }
    }
  ]
};

await client.api('/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageMention;
use Microsoft\Graph\Generated\Models\ChatMessageMentionedIdentitySet;
use Microsoft\Graph\Generated\Models\Identity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('Hello World <at id=\"0\">Jane Smith</at>');
$requestBody->setBody($body);
$mentionsChatMessageMention1 = new ChatMessageMention();
$mentionsChatMessageMention1->setId(0);
$mentionsChatMessageMention1->setMentionText('Jane Smith');
$mentionsChatMessageMention1Mentioned = new ChatMessageMentionedIdentitySet();
$mentionsChatMessageMention1MentionedUser = new Identity();
$mentionsChatMessageMention1MentionedUser->setDisplayName('Jane Smith');
$mentionsChatMessageMention1MentionedUser->setId('ef1c916a-3135-4417-ba27-8eb7bd084193');
$additionalData = [
	'userIdentityType' => 'aadUser',
];
$mentionsChatMessageMention1MentionedUser->setAdditionalData($additionalData);
$mentionsChatMessageMention1Mentioned->setUser($mentionsChatMessageMention1MentionedUser);
$mentionsChatMessageMention1->setMentioned($mentionsChatMessageMention1Mentioned);
$mentionsArray []= $mentionsChatMessageMention1;
$requestBody->setMentions($mentionsArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	body = @{
		contentType = "html"
		content = "Hello World <at id="0">Jane Smith</at>"
	}
	mentions = @(
		@{
			id = 0
			mentionText = "Jane Smith"
			mentioned = @{
				user = @{
					displayName = "Jane Smith"
					id = "ef1c916a-3135-4417-ba27-8eb7bd084193"
					userIdentityType = "aadUser"
				}
			}
		}
	)
}

New-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_mention import ChatMessageMention
from msgraph.generated.models.chat_message_mentioned_identity_set import ChatMessageMentionedIdentitySet
from msgraph.generated.models.identity import Identity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	body = ItemBody(
		content_type = BodyType.Html,
		content = "Hello World <at id=\"0\">Jane Smith</at>",
	),
	mentions = [
		ChatMessageMention(
			id = 0,
			mention_text = "Jane Smith",
			mentioned = ChatMessageMentionedIdentitySet(
				user = Identity(
					display_name = "Jane Smith",
					id = "ef1c916a-3135-4417-ba27-8eb7bd084193",
					additional_data = {
							"user_identity_type" : "aadUser",
					}
				),
			),
		),
	],
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('fbe2bf47-16c8-47cf-b4a5-4b9b187c508b')/channels('19%3A4a95f7d8db4c4e7fae857bcebe0623e6%40thread.tacv2')/messages/$entity",
    "id": "1616965872395",
    "replyToId": null,
    "etag": "1616965872395",
    "messageType": "message",
    "createdDateTime": "2021-03-28T21:11:12.395Z",
    "lastModifiedDateTime": "2021-03-28T21:11:12.395Z",
    "lastEditedDateTime": null,
    "deletedDateTime": null,
    "subject": null,
    "summary": null,
    "chatId": null,
    "importance": "normal",
    "locale": "en-us",
    "webUrl": "https://teams.microsoft.com/l/message/19%3A4a95f7d8db4c4e7fae857bcebe0623e6%40thread.tacv2/1616965872395?groupId=fbe2bf47-16c8-47cf-b4a5-4b9b187c508b&tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34&createdTime=1616965872395&parentMessageId=1616965872395",
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "user": {
            "@odata.type": "#microsoft.graph.teamworkUserIdentity",
            "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
            "displayName": "Robin Kline",
            "userIdentityType": "aadUser",
            "tenantId": "e61ef81e-8bd8-476a-92e8-4a62f8426fca"
        }
    },
    "body": {
        "contentType": "html",
        "content": "Hello World <at id=\"0\">Jane Smith</at>"
    },
    "channelIdentity": {
        "teamId": "fbe2bf47-16c8-47cf-b4a5-4b9b187c508b",
        "channelId": "19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2"
    },
    "attachments": [],
    "mentions": [
        {
            "id": 0,
            "mentionText": "Jane Smith",
            "mentioned": {
                "application": null,
                "device": null,
                "conversation": null,
                "user": {
                    "id": "ef1c916a-3135-4417-ba27-8eb7bd084193",
                    "displayName": "Jane Smith",
                    "userIdentityType": "aadUser"
                }
            }
        }
    ],
    "reactions": [],
    "messageHistory": []
}
```

### Example 3: Send a message containing cards

#### Request

The following example shows a request.

> **Note:** The attachment's ID must be unique and can be a new randomly generated GUID. However, the attachment's ID must be the same in the *body* and *attachments* elements.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2/messages
Content-type: application/json

{
    "subject": null,
    "body": {
        "contentType": "html",
        "content": "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>"
    },
    "attachments": [
        {
            "id": "74d20c7f34aa4a7fb74e2b30004247c5",
            "contentType": "application/vnd.microsoft.card.thumbnail",
            "contentUrl": null,
            "content": "{\r\n  \"title\": \"This is an example of posting a card\",\r\n  \"subtitle\": \"<h3>This is the subtitle</h3>\",\r\n  \"text\": \"Here is some body text. <br>\\r\\nAnd a <a href=\\\"http://microsoft.com/\\\">hyperlink</a>. <br>\\r\\nAnd below that is some buttons:\",\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"Login to FakeBot\",\r\n      \"text\": \"login\",\r\n      \"displayText\": \"login\",\r\n      \"value\": \"login\"\r\n    }\r\n  ]\r\n}",
            "name": null,
            "thumbnailUrl": null
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
	Subject = null,
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>",
	},
	Attachments = new List<ChatMessageAttachment>
	{
		new ChatMessageAttachment
		{
			Id = "74d20c7f34aa4a7fb74e2b30004247c5",
			ContentType = "application/vnd.microsoft.card.thumbnail",
			ContentUrl = null,
			Content = "{\r\n  \"title\": \"This is an example of posting a card\",\r\n  \"subtitle\": \"<h3>This is the subtitle</h3>\",\r\n  \"text\": \"Here is some body text. <br>\r\nAnd a <a href=\"http://microsoft.com/\">hyperlink</a>. <br>\r\nAnd below that is some buttons:\",\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"Login to FakeBot\",\r\n      \"text\": \"login\",\r\n      \"displayText\": \"login\",\r\n      \"value\": \"login\"\r\n    }\r\n  ]\r\n}",
			Name = null,
			ThumbnailUrl = null,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages.PostAsync(requestBody);
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
subject := null
requestBody.SetSubject(&subject) 
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>"
body.SetContent(&content) 
requestBody.SetBody(body)


chatMessageAttachment := graphmodels.NewChatMessageAttachment()
id := "74d20c7f34aa4a7fb74e2b30004247c5"
chatMessageAttachment.SetId(&id) 
contentType := "application/vnd.microsoft.card.thumbnail"
chatMessageAttachment.SetContentType(&contentType) 
contentUrl := null
chatMessageAttachment.SetContentUrl(&contentUrl) 
content := "{\r\n  \"title\": \"This is an example of posting a card\",\r\n  \"subtitle\": \"<h3>This is the subtitle</h3>\",\r\n  \"text\": \"Here is some body text. <br>\r\nAnd a <a href=\"http://microsoft.com/\">hyperlink</a>. <br>\r\nAnd below that is some buttons:\",\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"Login to FakeBot\",\r\n      \"text\": \"login\",\r\n      \"displayText\": \"login\",\r\n      \"value\": \"login\"\r\n    }\r\n  ]\r\n}"
chatMessageAttachment.SetContent(&content) 
name := null
chatMessageAttachment.SetName(&name) 
thumbnailUrl := null
chatMessageAttachment.SetThumbnailUrl(&thumbnailUrl) 

attachments := []graphmodels.ChatMessageAttachmentable {
	chatMessageAttachment,
}
requestBody.SetAttachments(attachments)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
chatMessage.setSubject(null);
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>");
chatMessage.setBody(body);
LinkedList<ChatMessageAttachment> attachments = new LinkedList<ChatMessageAttachment>();
ChatMessageAttachment chatMessageAttachment = new ChatMessageAttachment();
chatMessageAttachment.setId("74d20c7f34aa4a7fb74e2b30004247c5");
chatMessageAttachment.setContentType("application/vnd.microsoft.card.thumbnail");
chatMessageAttachment.setContentUrl(null);
chatMessageAttachment.setContent("{\r\n  \"title\": \"This is an example of posting a card\",\r\n  \"subtitle\": \"<h3>This is the subtitle</h3>\",\r\n  \"text\": \"Here is some body text. <br>\r\nAnd a <a href=\"http://microsoft.com/\">hyperlink</a>. <br>\r\nAnd below that is some buttons:\",\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"Login to FakeBot\",\r\n      \"text\": \"login\",\r\n      \"displayText\": \"login\",\r\n      \"value\": \"login\"\r\n    }\r\n  ]\r\n}");
chatMessageAttachment.setName(null);
chatMessageAttachment.setThumbnailUrl(null);
attachments.add(chatMessageAttachment);
chatMessage.setAttachments(attachments);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
    subject: null,
    body: {
        contentType: 'html',
        content: '<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>'
    },
    attachments: [
        {
            id: '74d20c7f34aa4a7fb74e2b30004247c5',
            contentType: 'application/vnd.microsoft.card.thumbnail',
            contentUrl: null,
            content: '{\r\n  \"title\': \'This is an example of posting a card\",\r\n  \"subtitle\': \'<h3>This is the subtitle</h3>\",\r\n  \"text\': \'Here is some body text. <br>\\r\\nAnd a <a href=\\\"http://microsoft.com/\\\">hyperlink</a>. <br>\\r\\nAnd below that is some buttons:\",\r\n  \"buttons\': [\r\n    {\r\n      \'type\': \'messageBack\",\r\n      \"title\': \'Login to FakeBot\",\r\n      \"text\': \'login\",\r\n      \"displayText\': \'login\",\r\n      \"value\': \"login\"\r\n    }\r\n  ]\r\n}",
            name: null,
            thumbnailUrl: null
        }
    ]
};

await client.api('/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageAttachment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$requestBody->setSubject(null);
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>');
$requestBody->setBody($body);
$attachmentsChatMessageAttachment1 = new ChatMessageAttachment();
$attachmentsChatMessageAttachment1->setId('74d20c7f34aa4a7fb74e2b30004247c5');
$attachmentsChatMessageAttachment1->setContentType('application/vnd.microsoft.card.thumbnail');
$attachmentsChatMessageAttachment1->setContentUrl(null);
$attachmentsChatMessageAttachment1->setContent('{\r\n  \"title\": \"This is an example of posting a card\",\r\n  \"subtitle\": \"<h3>This is the subtitle</h3>\",\r\n  \"text\": \"Here is some body text. <br>\r\nAnd a <a href=\"http://microsoft.com/\">hyperlink</a>. <br>\r\nAnd below that is some buttons:\",\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"Login to FakeBot\",\r\n      \"text\": \"login\",\r\n      \"displayText\": \"login\",\r\n      \"value\": \"login\"\r\n    }\r\n  ]\r\n}');
$attachmentsChatMessageAttachment1->setName(null);
$attachmentsChatMessageAttachment1->setThumbnailUrl(null);
$attachmentsArray []= $attachmentsChatMessageAttachment1;
$requestBody->setAttachments($attachmentsArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	subject = $null
	body = @{
		contentType = "html"
		content = "<attachment id="74d20c7f34aa4a7fb74e2b30004247c5"></attachment>"
	}
	attachments = @(
		@{
			id = "74d20c7f34aa4a7fb74e2b30004247c5"
			contentType = "application/vnd.microsoft.card.thumbnail"
			contentUrl = $null
			content = '{
  "title": "This is an example of posting a card",
  "subtitle": "<h3>This is the subtitle</h3>",
  "text": "Here is some body text. <br>\r\nAnd a <a href=\"http://microsoft.com/\">hyperlink</a>. <br>\r\nAnd below that is some buttons:",
  "buttons": [
    {
      "type": "messageBack",
      "title": "Login to FakeBot",
      "text": "login",
      "displayText": "login",
      "value": "login"
    }
  ]
}'
			name = $null
			thumbnailUrl = $null
		}
	)
}

New-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_attachment import ChatMessageAttachment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	subject = None,
	body = ItemBody(
		content_type = BodyType.Html,
		content = "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>",
	),
	attachments = [
		ChatMessageAttachment(
			id = "74d20c7f34aa4a7fb74e2b30004247c5",
			content_type = "application/vnd.microsoft.card.thumbnail",
			content_url = None,
			content = "{\r\n  \"title\": \"This is an example of posting a card\",\r\n  \"subtitle\": \"<h3>This is the subtitle</h3>\",\r\n  \"text\": \"Here is some body text. <br>\r\nAnd a <a href=\"http://microsoft.com/\">hyperlink</a>. <br>\r\nAnd below that is some buttons:\",\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"Login to FakeBot\",\r\n      \"text\": \"login\",\r\n      \"displayText\": \"login\",\r\n      \"value\": \"login\"\r\n    }\r\n  ]\r\n}",
			name = None,
			thumbnail_url = None,
		),
	],
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('fbe2bf47-16c8-47cf-b4a5-4b9b187c508b')/channels('19%3A4a95f7d8db4c4e7fae857bcebe0623e6%40thread.tacv2')/messages/$entity",
    "id": "1616991851162",
    "replyToId": null,
    "etag": "1616991851162",
    "messageType": "message",
    "createdDateTime": "2021-03-29T04:24:11.162Z",
    "lastModifiedDateTime": "2021-03-29T04:24:11.162Z",
    "lastEditedDateTime": null,
    "deletedDateTime": null,
    "subject": null,
    "summary": null,
    "chatId": null,
    "importance": "normal",
    "locale": "en-us",
    "webUrl": "https://teams.microsoft.com/l/message/19%3A4a95f7d8db4c4e7fae857bcebe0623e6%40thread.tacv2/1616991851162?groupId=fbe2bf47-16c8-47cf-b4a5-4b9b187c508b&tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34&createdTime=1616991851162&parentMessageId=1616991851162",
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "user": {
            "@odata.type": "#microsoft.graph.teamworkUserIdentity",
            "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
            "displayName": "Robin Kline",
            "userIdentityType": "aadUser",
            "tenantId": "e61ef81e-8bd8-476a-92e8-4a62f8426fca"
        }
    },
    "body": {
        "contentType": "html",
        "content": "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>"
    },
    "channelIdentity": {
        "teamId": "fbe2bf47-16c8-47cf-b4a5-4b9b187c508b",
        "channelId": "19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2"
    },
    "attachments": [
        {
            "id": "74d20c7f34aa4a7fb74e2b30004247c5",
            "contentType": "application/vnd.microsoft.card.thumbnail",
            "contentUrl": null,
            "content": "{  \"title\": \"This is an example of posting a card\",  \"subtitle\": \"<h3>This is the subtitle</h3>\",  \"text\": \"Here is some body text. <br>\\\\And a <a href=\\\"http://microsoft.com/\\\">hyperlink</a>. <br>\\\\And below that is some buttons:\",  \"buttons\": [    {      \"type\": \"messageBack\",      \"title\": \"Login to FakeBot\",      \"text\": \"login\",      \"displayText\": \"login\",      \"value\": \"login\"    }  ]}",
            "name": null,
            "thumbnailUrl": null
        }
    ],
    "mentions": [],
    "reactions": [],
    "messageHistory": []
}
```

### Example 4: Send a message with file attachment in it

#### Request

The following example shows a request.

> **Notes:**
> 
> - The file to attach must already be in SharePoint. To access the file properties, [GET the **driveItem** for the file](https://learn.microsoft.com/en-us/graph/api/driveitem-get). The **eTag** of the **driveItem** has a GUID that is your attachment ID. The **webDavUrl** of the **driveItem** is your attachment **contentURL**. You can use the name of the **driveItem** as your attachment name. You can use /drives/{drive-id}/items/{item-id} to get a drive item resource. To get **webDavUrl**, you have to explicitly select it via $select=webDavUrl or $select=\*,webDavUrl.
> - Microsoft Graph supports the `OpenUrl` card action. Bots are required for other card actions.

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```http
POST https://graph.microsoft.com/v1.0/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2/messages
Content-type: application/json

{
    "body": {
        "contentType": "html",
        "content": "Here's the latest budget. <attachment id=\"153fa47d-18c9-4179-be08-9879815a9f90\"></attachment>"
    },
    "attachments": [
        {
            "id": "153fa47d-18c9-4179-be08-9879815a9f90",
            "contentType": "reference",
            "contentUrl": "https://m365x987948.sharepoint.com/sites/test/Shared%20Documents/General/test%20doc.docx",
            "name": "Budget.docx"
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
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "Here's the latest budget. <attachment id=\"153fa47d-18c9-4179-be08-9879815a9f90\"></attachment>",
	},
	Attachments = new List<ChatMessageAttachment>
	{
		new ChatMessageAttachment
		{
			Id = "153fa47d-18c9-4179-be08-9879815a9f90",
			ContentType = "reference",
			ContentUrl = "https://m365x987948.sharepoint.com/sites/test/Shared%20Documents/General/test%20doc.docx",
			Name = "Budget.docx",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages.PostAsync(requestBody);
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
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "Here's the latest budget. <attachment id=\"153fa47d-18c9-4179-be08-9879815a9f90\"></attachment>"
body.SetContent(&content) 
requestBody.SetBody(body)


chatMessageAttachment := graphmodels.NewChatMessageAttachment()
id := "153fa47d-18c9-4179-be08-9879815a9f90"
chatMessageAttachment.SetId(&id) 
contentType := "reference"
chatMessageAttachment.SetContentType(&contentType) 
contentUrl := "https://m365x987948.sharepoint.com/sites/test/Shared%20Documents/General/test%20doc.docx"
chatMessageAttachment.SetContentUrl(&contentUrl) 
name := "Budget.docx"
chatMessageAttachment.SetName(&name) 

attachments := []graphmodels.ChatMessageAttachmentable {
	chatMessageAttachment,
}
requestBody.SetAttachments(attachments)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("Here's the latest budget. <attachment id=\"153fa47d-18c9-4179-be08-9879815a9f90\"></attachment>");
chatMessage.setBody(body);
LinkedList<ChatMessageAttachment> attachments = new LinkedList<ChatMessageAttachment>();
ChatMessageAttachment chatMessageAttachment = new ChatMessageAttachment();
chatMessageAttachment.setId("153fa47d-18c9-4179-be08-9879815a9f90");
chatMessageAttachment.setContentType("reference");
chatMessageAttachment.setContentUrl("https://m365x987948.sharepoint.com/sites/test/Shared%20Documents/General/test%20doc.docx");
chatMessageAttachment.setName("Budget.docx");
attachments.add(chatMessageAttachment);
chatMessage.setAttachments(attachments);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
    body: {
        contentType: 'html',
        content: 'Here\'s the latest budget. <attachment id=\"153fa47d-18c9-4179-be08-9879815a9f90\"></attachment>'
    },
    attachments: [
        {
            id: '153fa47d-18c9-4179-be08-9879815a9f90',
            contentType: 'reference',
            contentUrl: 'https://m365x987948.sharepoint.com/sites/test/Shared%20Documents/General/test%20doc.docx',
            name: 'Budget.docx'
        }
    ]
};

await client.api('/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageAttachment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('Here\'s the latest budget. <attachment id=\"153fa47d-18c9-4179-be08-9879815a9f90\"></attachment>');
$requestBody->setBody($body);
$attachmentsChatMessageAttachment1 = new ChatMessageAttachment();
$attachmentsChatMessageAttachment1->setId('153fa47d-18c9-4179-be08-9879815a9f90');
$attachmentsChatMessageAttachment1->setContentType('reference');
$attachmentsChatMessageAttachment1->setContentUrl('https://m365x987948.sharepoint.com/sites/test/Shared%20Documents/General/test%20doc.docx');
$attachmentsChatMessageAttachment1->setName('Budget.docx');
$attachmentsArray []= $attachmentsChatMessageAttachment1;
$requestBody->setAttachments($attachmentsArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	body = @{
		contentType = "html"
		content = "Here's the latest budget. <attachment id="153fa47d-18c9-4179-be08-9879815a9f90"></attachment>"
	}
	attachments = @(
		@{
			id = "153fa47d-18c9-4179-be08-9879815a9f90"
			contentType = "reference"
			contentUrl = "https://m365x987948.sharepoint.com/sites/test/Shared%20Documents/General/test%20doc.docx"
			name = "Budget.docx"
		}
	)
}

New-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_attachment import ChatMessageAttachment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	body = ItemBody(
		content_type = BodyType.Html,
		content = "Here's the latest budget. <attachment id=\"153fa47d-18c9-4179-be08-9879815a9f90\"></attachment>",
	),
	attachments = [
		ChatMessageAttachment(
			id = "153fa47d-18c9-4179-be08-9879815a9f90",
			content_type = "reference",
			content_url = "https://m365x987948.sharepoint.com/sites/test/Shared%20Documents/General/test%20doc.docx",
			name = "Budget.docx",
		),
	],
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('fbe2bf47-16c8-47cf-b4a5-4b9b187c508b')/channels('19%3A4a95f7d8db4c4e7fae857bcebe0623e6%40thread.tacv2')/messages/$entity",
    "id": "1616991899452",
    "replyToId": null,
    "etag": "1616991899452",
    "messageType": "message",
    "createdDateTime": "2021-03-29T04:24:59.452Z",
    "lastModifiedDateTime": "2021-03-29T04:24:59.452Z",
    "lastEditedDateTime": null,
    "deletedDateTime": null,
    "subject": null,
    "summary": null,
    "chatId": null,
    "importance": "normal",
    "locale": "en-us",
    "webUrl": "https://teams.microsoft.com/l/message/19%3A4a95f7d8db4c4e7fae857bcebe0623e6%40thread.tacv2/1616991899452?groupId=fbe2bf47-16c8-47cf-b4a5-4b9b187c508b&tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34&createdTime=1616991899452&parentMessageId=1616991899452",
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "user": {
            "@odata.type": "#microsoft.graph.teamworkUserIdentity",
            "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
            "displayName": "Robin Kline",
            "userIdentityType": "aadUser",
            "tenantId": "e61ef81e-8bd8-476a-92e8-4a62f8426fca"
        }
    },
    "body": {
        "contentType": "html",
        "content": "Here's the latest budget. <attachment id=\"153fa47d-18c9-4179-be08-9879815a9f90\"></attachment>"
    },
    "channelIdentity": {
        "teamId": "fbe2bf47-16c8-47cf-b4a5-4b9b187c508b",
        "channelId": "19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2"
    },
    "attachments": [
        {
            "id": "153fa47d-18c9-4179-be08-9879815a9f90",
            "contentType": "reference",
            "contentUrl": "https://m365x987948.sharepoint.com/sites/test/Shared%20Documents/General/test%20doc.docx",
            "content": null,
            "name": "Budget.docx",
            "thumbnailUrl": null
        }
    ],
    "mentions": [],
    "reactions": [],
    "messageHistory": []
}
```

### Example 5: Send a message that includes a file attachment using a file share link

The following example shows how to send a message that includes a file attachment using a file share link.

#### Request

The following example shows a request.

> **Notes:**
> 
> - The file to be attached must already be located in SharePoint. Use any GUID as your attachment ID and the file share link as the **contentURL**. Users must have permissions to access the drive item via the [share link](https://learn.microsoft.com/en-us/graph/api/shares-get?view=graph-rest-1.0).
> - Using a file share link to send messages isn't supported in a [migration](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/import-messages/import-external-messages-to-teams) scenario.

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```http
POST https://graph.microsoft.com/v1.0/teams/1e769eab-06a8-4b2e-ac42-1f040a4e52a1/channels/19:e28d1f9b354f4de88d2e9e4d8b983763@thread.tacv2/messages
Content-type: application/json

{
  "body": {
    "contentType": "html",
    "content": "Testing with file share link. <attachment id=\"668f7fa8-8129-4de7-b32b-fe1b442e6ef1\"></attachment>"
  },
  "attachments": [
    {
      "id": "668f7fa8-8129-4de7-b32b-fe1b442e6ef1",
      "contentType": "reference",
      "contentUrl": "https://teamsgraph-my.sharepoint.com/:w:/g/personal/test_teamsgraph_onmicrosoft_com/Eah_j2YpgedNsyv-G0QubvEBma6Sd_76UtYkXwoJ-nYVEg?e=0H2Ibm"
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
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "Testing with file share link. <attachment id=\"668f7fa8-8129-4de7-b32b-fe1b442e6ef1\"></attachment>",
	},
	Attachments = new List<ChatMessageAttachment>
	{
		new ChatMessageAttachment
		{
			Id = "668f7fa8-8129-4de7-b32b-fe1b442e6ef1",
			ContentType = "reference",
			ContentUrl = "https://teamsgraph-my.sharepoint.com/:w:/g/personal/test_teamsgraph_onmicrosoft_com/Eah_j2YpgedNsyv-G0QubvEBma6Sd_76UtYkXwoJ-nYVEg?e=0H2Ibm",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages.PostAsync(requestBody);
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
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "Testing with file share link. <attachment id=\"668f7fa8-8129-4de7-b32b-fe1b442e6ef1\"></attachment>"
body.SetContent(&content) 
requestBody.SetBody(body)


chatMessageAttachment := graphmodels.NewChatMessageAttachment()
id := "668f7fa8-8129-4de7-b32b-fe1b442e6ef1"
chatMessageAttachment.SetId(&id) 
contentType := "reference"
chatMessageAttachment.SetContentType(&contentType) 
contentUrl := "https://teamsgraph-my.sharepoint.com/:w:/g/personal/test_teamsgraph_onmicrosoft_com/Eah_j2YpgedNsyv-G0QubvEBma6Sd_76UtYkXwoJ-nYVEg?e=0H2Ibm"
chatMessageAttachment.SetContentUrl(&contentUrl) 

attachments := []graphmodels.ChatMessageAttachmentable {
	chatMessageAttachment,
}
requestBody.SetAttachments(attachments)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("Testing with file share link. <attachment id=\"668f7fa8-8129-4de7-b32b-fe1b442e6ef1\"></attachment>");
chatMessage.setBody(body);
LinkedList<ChatMessageAttachment> attachments = new LinkedList<ChatMessageAttachment>();
ChatMessageAttachment chatMessageAttachment = new ChatMessageAttachment();
chatMessageAttachment.setId("668f7fa8-8129-4de7-b32b-fe1b442e6ef1");
chatMessageAttachment.setContentType("reference");
chatMessageAttachment.setContentUrl("https://teamsgraph-my.sharepoint.com/:w:/g/personal/test_teamsgraph_onmicrosoft_com/Eah_j2YpgedNsyv-G0QubvEBma6Sd_76UtYkXwoJ-nYVEg?e=0H2Ibm");
attachments.add(chatMessageAttachment);
chatMessage.setAttachments(attachments);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
  body: {
    contentType: 'html',
    content: 'Testing with file share link. <attachment id=\"668f7fa8-8129-4de7-b32b-fe1b442e6ef1\"></attachment>'
  },
  attachments: [
    {
      id: '668f7fa8-8129-4de7-b32b-fe1b442e6ef1',
      contentType: 'reference',
      contentUrl: 'https://teamsgraph-my.sharepoint.com/:w:/g/personal/test_teamsgraph_onmicrosoft_com/Eah_j2YpgedNsyv-G0QubvEBma6Sd_76UtYkXwoJ-nYVEg?e=0H2Ibm'
    }
  ]
};

await client.api('/teams/1e769eab-06a8-4b2e-ac42-1f040a4e52a1/channels/19:e28d1f9b354f4de88d2e9e4d8b983763@thread.tacv2/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageAttachment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('Testing with file share link. <attachment id=\"668f7fa8-8129-4de7-b32b-fe1b442e6ef1\"></attachment>');
$requestBody->setBody($body);
$attachmentsChatMessageAttachment1 = new ChatMessageAttachment();
$attachmentsChatMessageAttachment1->setId('668f7fa8-8129-4de7-b32b-fe1b442e6ef1');
$attachmentsChatMessageAttachment1->setContentType('reference');
$attachmentsChatMessageAttachment1->setContentUrl('https://teamsgraph-my.sharepoint.com/:w:/g/personal/test_teamsgraph_onmicrosoft_com/Eah_j2YpgedNsyv-G0QubvEBma6Sd_76UtYkXwoJ-nYVEg?e=0H2Ibm');
$attachmentsArray []= $attachmentsChatMessageAttachment1;
$requestBody->setAttachments($attachmentsArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	body = @{
		contentType = "html"
		content = "Testing with file share link. <attachment id="668f7fa8-8129-4de7-b32b-fe1b442e6ef1"></attachment>"
	}
	attachments = @(
		@{
			id = "668f7fa8-8129-4de7-b32b-fe1b442e6ef1"
			contentType = "reference"
			contentUrl = "https://teamsgraph-my.sharepoint.com/:w:/g/personal/test_teamsgraph_onmicrosoft_com/Eah_j2YpgedNsyv-G0QubvEBma6Sd_76UtYkXwoJ-nYVEg?e=0H2Ibm"
		}
	)
}

New-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_attachment import ChatMessageAttachment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	body = ItemBody(
		content_type = BodyType.Html,
		content = "Testing with file share link. <attachment id=\"668f7fa8-8129-4de7-b32b-fe1b442e6ef1\"></attachment>",
	),
	attachments = [
		ChatMessageAttachment(
			id = "668f7fa8-8129-4de7-b32b-fe1b442e6ef1",
			content_type = "reference",
			content_url = "https://teamsgraph-my.sharepoint.com/:w:/g/personal/test_teamsgraph_onmicrosoft_com/Eah_j2YpgedNsyv-G0QubvEBma6Sd_76UtYkXwoJ-nYVEg?e=0H2Ibm",
		),
	],
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('1e769eab-06a8-4b2e-ac42-1f040a4e52a1')/channels('19%3Ae28d1f9b354f4de88d2e9e4d8b983763%40thread.tacv2')/messages/$entity",
  "id": "1709663385319",
  "replyToId": null,
  "etag": "1709663385319",
  "messageType": "message",
  "createdDateTime": "2024-03-05T18:29:45.319Z",
  "lastModifiedDateTime": "2024-03-05T18:29:45.319Z",
  "lastEditedDateTime": null,
  "deletedDateTime": null,
  "subject": null,
  "summary": null,
  "chatId": null,
  "importance": "normal",
  "locale": "en-us",
  "webUrl": "https://teams.microsoft.com/l/message/19%3Ae28d1f9b354f4de88d2e9e4d8b983763%40thread.tacv2/1709663385319?groupId=1e769eab-06a8-4b2e-ac42-1f040a4e52a1&tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34&createdTime=1709663385319&parentMessageId=1709663385319",
  "policyViolation": null,
  "eventDetail": null,
  "from": {
    "application": null,
    "device": null,
    "user": {
      "@odata.type": "#microsoft.graph.teamworkUserIdentity",
      "id": "28c10244-4bad-4fda-993c-f332faef94f0",
      "displayName": "Test User",
      "userIdentityType": "aadUser"
    }
  },
  "body": {
    "contentType": "html",
    "content": "Testing with file share link. <attachment id=\"668f7fa8-8129-4de7-b32b-fe1b442e6ef1\"></attachment>"
  },
  "channelIdentity": {
    "teamId": "1e769eab-06a8-4b2e-ac42-1f040a4e52a1",
    "channelId": "19:e28d1f9b354f4de88d2e9e4d8b983763@thread.tacv2"
  },
  "attachments": [
    {
      "id": "668f7fa8-8129-4de7-b32b-fe1b442e6ef1",
      "contentType": "reference",
      "contentUrl": "https://teamsgraph-my.sharepoint.com/personal/test_teamsgraph_onmicrosoft_com/Documents/Personal%20Drive%20file%201.docx",
      "content": null,
      "name": "Personal Drive file 1.docx",
      "thumbnailUrl": null,
      "teamsAppId": null
    }
  ],
  "mentions": [],
  "reactions": []
}
```

### Example 6: Send inline images along with the message

#### Request

The following example shows a request.

> **Note:** The **temporaryId** in the **hostedContents** collection is a random ID but must be the same across the **body** and **hostedContents** elements. \(Notice the **temporaryId** set to `1` and the reference in the body as `../hostedContents/1/$value`.\)

**contentBytes** must be set to binary string Base64-encoded bytes. You can convert an item to binary Base64-encoded bytes in C# by using `Convert.ToBase64String(File.ReadAllBytes("image.png"));`, for example. Microsoft .NET SDK users don't need to convert to Base64 encoded bytes as the SDK handles it for you.

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
POST https://graph.microsoft.com/v1.0/chats/19:2da4c29f6d7041eca70b638b43d45437@thread.v2/messages
Content-type: application/json

{
	"body": {
        "contentType": "html",
        "content": "<img height=\"297\" src=\"../hostedContents/1/$value\" width=\"297\">"
    },
    "hostedContents":[
        {
          "@microsoft.graph.temporaryId": "1",
          "contentBytes": "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",
            "contentType": "image/png"
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
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "<img height=\"297\" src=\"../hostedContents/1/$value\" width=\"297\">",
	},
	HostedContents = new List<ChatMessageHostedContent>
	{
		new ChatMessageHostedContent
		{
			ContentBytes = Convert.FromBase64String("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"),
			ContentType = "image/png",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"@microsoft.graph.temporaryId" , "1"
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Chats["{chat-id}"].Messages.PostAsync(requestBody);
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
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "<img height=\"297\" src=\"../hostedContents/1/$value\" width=\"297\">"
body.SetContent(&content) 
requestBody.SetBody(body)


chatMessageHostedContent := graphmodels.NewChatMessageHostedContent()
contentBytes := []byte("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")
chatMessageHostedContent.SetContentBytes(&contentBytes) 
contentType := "image/png"
chatMessageHostedContent.SetContentType(&contentType) 
additionalData := map[string]interface{}{
	"@microsoft.graph.temporaryId" : "1", 
}
chatMessageHostedContent.SetAdditionalData(additionalData)

hostedContents := []graphmodels.ChatMessageHostedContentable {
	chatMessageHostedContent,
}
requestBody.SetHostedContents(hostedContents)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Chats().ByChatId("chat-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("<img height=\"297\" src=\"../hostedContents/1/$value\" width=\"297\">");
chatMessage.setBody(body);
LinkedList<ChatMessageHostedContent> hostedContents = new LinkedList<ChatMessageHostedContent>();
ChatMessageHostedContent chatMessageHostedContent = new ChatMessageHostedContent();
byte[] contentBytes = Base64.getDecoder().decode("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");
chatMessageHostedContent.setContentBytes(contentBytes);
chatMessageHostedContent.setContentType("image/png");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@microsoft.graph.temporaryId", "1");
chatMessageHostedContent.setAdditionalData(additionalData);
hostedContents.add(chatMessageHostedContent);
chatMessage.setHostedContents(hostedContents);
ChatMessage result = graphClient.chats().byChatId("{chat-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
	body: {
        contentType: 'html',
        content: '<img height=\"297\" src=\"../hostedContents/1/$value\" width=\"297\">'
    },
    hostedContents: [
        {
          '@microsoft.graph.temporaryId': '1',
          contentBytes: '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',
            contentType: 'image/png'
        }
    ]
};

await client.api('/chats/19:2da4c29f6d7041eca70b638b43d45437@thread.v2/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageHostedContent;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('<img height=\"297\" src=\"../hostedContents/1/$value\" width=\"297\">');
$requestBody->setBody($body);
$hostedContentsChatMessageHostedContent1 = new ChatMessageHostedContent();
$hostedContentsChatMessageHostedContent1->setContentBytes(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('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')));
$hostedContentsChatMessageHostedContent1->setContentType('image/png');
$additionalData = [
	'@microsoft.graph.temporaryId' => '1',
];
$hostedContentsChatMessageHostedContent1->setAdditionalData($additionalData);
$hostedContentsArray []= $hostedContentsChatMessageHostedContent1;
$requestBody->setHostedContents($hostedContentsArray);


$result = $graphServiceClient->chats()->byChatId('chat-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	body = @{
		contentType = "html"
		content = "<img height="297" src="../hostedContents/1/$value" width="297">"
	}
	hostedContents = @(
		@{
			"@microsoft.graph.temporaryId" = "1"
			contentBytes = [System.Text.Encoding]::ASCII.GetBytes("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")
			contentType = "image/png"
		}
	)
}

New-MgChatMessage -ChatId $chatId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_hosted_content import ChatMessageHostedContent
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	body = ItemBody(
		content_type = BodyType.Html,
		content = "<img height=\"297\" src=\"../hostedContents/1/$value\" width=\"297\">",
	),
	hosted_contents = [
		ChatMessageHostedContent(
			content_bytes = base64.urlsafe_b64decode("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"),
			content_type = "image/png",
			additional_data = {
					"@microsoft_graph_temporary_id" : "1",
			}
		),
	],
)

result = await graph_client.chats.by_chat_id('chat-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#chats('19%3A2da4c29f6d7041eca70b638b43d45437%40thread.v2')/messages/$entity",
    "id": "1616991962672",
    "replyToId": null,
    "etag": "1616991962672",
    "messageType": "message",
    "createdDateTime": "2021-03-29T04:26:02.672Z",
    "lastModifiedDateTime": "2021-03-29T04:26:02.672Z",
    "lastEditedDateTime": null,
    "deletedDateTime": null,
    "subject": null,
    "summary": null,
    "chatId": "19:2da4c29f6d7041eca70b638b43d45437@thread.v2",
    "importance": "normal",
    "locale": "en-us",
    "webUrl": null,
    "channelIdentity": null,
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "user": {
            "@odata.type": "#microsoft.graph.teamworkUserIdentity",
            "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
            "displayName": "Robin Kline",
            "userIdentityType": "aadUser",
            "tenantId": "e61ef81e-8bd8-476a-92e8-4a62f8426fca"
        }
    },
    "body": {
        "contentType": "html",
        "content": "<img height=\"297\" src=\"https://graph.microsoft.com/v1.0/chats/19:97641583cf154265a237da28ebbde27a@thread.v2/messages/1736180156294/hostedContents/aWQ9eF8wLWV1cy1kMTQtYjUxMDlhMDhkODZkM2ZjODBkNzFlYjUzMWM4ZDlmZGEsdHlwZT0xLHVybD1odHRwczovL3VzLWFwaS5hc20uc2t5cGUuY29tL3YxL29iamVjdHMvMC1ldXMtZDE0LWI1MTA5YTA4ZDg2ZDNmYzgwZDcxZWI1MzFjOGQ5ZmRhL3ZpZXdzL2ltZ3BzaF9mdWxsc2l6ZQ==/$value\" width=\"297\">"
    },
    "attachments": [],
    "mentions": [],
    "reactions": [],
    "messageHistory": []
}
```

### Example 7: Send a card with inline images

#### Request

The following example shows a request.

> **Notes:**
> 
> - The **temporaryId** in the **hostedContents** collection is a random ID, but must be the same across the **content** \(in **attachments**\) and **hostedContents** elements. \(Notice the **temporaryId** set to `1` and the reference in content as `../hostedContents/1/$value`.\).
> - The maximum possible size of hosted content is 4 MB.

**contentBytes** must be set to binary string Base64-encoded bytes. You can do it in C# by using `Convert.ToBase64String(File.ReadAllBytes("image.png"));`. Microsoft .NET SDK users don't need to convert to Base64 encoded bytes as the SDK handles it for you.

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
POST https://graph.microsoft.com/v1.0/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2/messages
Content-type: application/json

{
    "subject": null,
    "body": {
        "contentType": "html",
        "content": "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>"
    },
    "attachments": [{
        "id": "74d20c7f34aa4a7fb74e2b30004247c5",
        "contentType": "application/vnd.microsoft.card.adaptive",
        "contentUrl": null,
        "content": "{\r\n  \"$schema\": \"http://adaptivecards.io/schemas/adaptive-card.json\",\r\n  \"type\": \"AdaptiveCard\",\r\n  \"version\": \"1.2\",\r\n  \"speak\": \"The Seattle Seahawks beat the Carolina Panthers 40-7\",\r\n  \"body\": [\r\n    {\r\n      \"type\": \"Container\",\r\n      \"items\": [\r\n        {\r\n          \"type\": \"ColumnSet\",\r\n          \"columns\": [\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"auto\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"Image\",\r\n                  \"url\": \"../hostedContents/1/$value\",\r\n                  \"size\": \"Medium\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"SHADES\",\r\n                  \"horizontalAlignment\": \"Center\",\r\n                  \"weight\": \"Bolder\"\r\n                }\r\n              ]\r\n            },\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"stretch\",\r\n              \"separator\": true,\r\n              \"spacing\": \"Medium\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"2019-08-31T19:30:00Z\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"Final\",\r\n                  \"spacing\": \"None\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"40 - 7\",\r\n                  \"size\": \"ExtraLarge\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                }\r\n              ]\r\n            },\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"auto\",\r\n              \"separator\": true,\r\n              \"spacing\": \"Medium\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"Image\",\r\n                  \"url\": \"../hostedContents/2/$value\",\r\n                  \"size\": \"Medium\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"SKINS\",\r\n                  \"horizontalAlignment\": \"Center\",\r\n                  \"weight\": \"Bolder\"\r\n                }\r\n              ]\r\n            }\r\n          ]\r\n        }\r\n      ]\r\n    }\r\n  ]\r\n}",
        "name": null,
        "thumbnailUrl": null
    }],
    "hostedContents": [{
        "@microsoft.graph.temporaryId": "1",
        "contentBytes": "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",
        "contentType": "image/png"
    }, {
        "@microsoft.graph.temporaryId": "2",
        "contentBytes": "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",
        "contentType": "image/png"
    }]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ChatMessage
{
	Subject = null,
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>",
	},
	Attachments = new List<ChatMessageAttachment>
	{
		new ChatMessageAttachment
		{
			Id = "74d20c7f34aa4a7fb74e2b30004247c5",
			ContentType = "application/vnd.microsoft.card.adaptive",
			ContentUrl = null,
			Content = "{\r\n  \"$schema\": \"http://adaptivecards.io/schemas/adaptive-card.json\",\r\n  \"type\": \"AdaptiveCard\",\r\n  \"version\": \"1.2\",\r\n  \"speak\": \"The Seattle Seahawks beat the Carolina Panthers 40-7\",\r\n  \"body\": [\r\n    {\r\n      \"type\": \"Container\",\r\n      \"items\": [\r\n        {\r\n          \"type\": \"ColumnSet\",\r\n          \"columns\": [\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"auto\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"Image\",\r\n                  \"url\": \"../hostedContents/1/$value\",\r\n                  \"size\": \"Medium\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"SHADES\",\r\n                  \"horizontalAlignment\": \"Center\",\r\n                  \"weight\": \"Bolder\"\r\n                }\r\n              ]\r\n            },\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"stretch\",\r\n              \"separator\": true,\r\n              \"spacing\": \"Medium\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"2019-08-31T19:30:00Z\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"Final\",\r\n                  \"spacing\": \"None\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"40 - 7\",\r\n                  \"size\": \"ExtraLarge\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                }\r\n              ]\r\n            },\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"auto\",\r\n              \"separator\": true,\r\n              \"spacing\": \"Medium\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"Image\",\r\n                  \"url\": \"../hostedContents/2/$value\",\r\n                  \"size\": \"Medium\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"SKINS\",\r\n                  \"horizontalAlignment\": \"Center\",\r\n                  \"weight\": \"Bolder\"\r\n                }\r\n              ]\r\n            }\r\n          ]\r\n        }\r\n      ]\r\n    }\r\n  ]\r\n}",
			Name = null,
			ThumbnailUrl = null,
		},
	},
	HostedContents = new List<ChatMessageHostedContent>
	{
		new ChatMessageHostedContent
		{
			ContentBytes = Convert.FromBase64String("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"),
			ContentType = "image/png",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"@microsoft.graph.temporaryId" , "1"
				},
			},
		},
		new ChatMessageHostedContent
		{
			ContentBytes = Convert.FromBase64String("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"),
			ContentType = "image/png",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"@microsoft.graph.temporaryId" , "2"
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages.PostAsync(requestBody);
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
subject := null
requestBody.SetSubject(&subject) 
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>"
body.SetContent(&content) 
requestBody.SetBody(body)


chatMessageAttachment := graphmodels.NewChatMessageAttachment()
id := "74d20c7f34aa4a7fb74e2b30004247c5"
chatMessageAttachment.SetId(&id) 
contentType := "application/vnd.microsoft.card.adaptive"
chatMessageAttachment.SetContentType(&contentType) 
contentUrl := null
chatMessageAttachment.SetContentUrl(&contentUrl) 
content := "{\r\n  \"$schema\": \"http://adaptivecards.io/schemas/adaptive-card.json\",\r\n  \"type\": \"AdaptiveCard\",\r\n  \"version\": \"1.2\",\r\n  \"speak\": \"The Seattle Seahawks beat the Carolina Panthers 40-7\",\r\n  \"body\": [\r\n    {\r\n      \"type\": \"Container\",\r\n      \"items\": [\r\n        {\r\n          \"type\": \"ColumnSet\",\r\n          \"columns\": [\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"auto\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"Image\",\r\n                  \"url\": \"../hostedContents/1/$value\",\r\n                  \"size\": \"Medium\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"SHADES\",\r\n                  \"horizontalAlignment\": \"Center\",\r\n                  \"weight\": \"Bolder\"\r\n                }\r\n              ]\r\n            },\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"stretch\",\r\n              \"separator\": true,\r\n              \"spacing\": \"Medium\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"2019-08-31T19:30:00Z\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"Final\",\r\n                  \"spacing\": \"None\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"40 - 7\",\r\n                  \"size\": \"ExtraLarge\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                }\r\n              ]\r\n            },\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"auto\",\r\n              \"separator\": true,\r\n              \"spacing\": \"Medium\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"Image\",\r\n                  \"url\": \"../hostedContents/2/$value\",\r\n                  \"size\": \"Medium\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"SKINS\",\r\n                  \"horizontalAlignment\": \"Center\",\r\n                  \"weight\": \"Bolder\"\r\n                }\r\n              ]\r\n            }\r\n          ]\r\n        }\r\n      ]\r\n    }\r\n  ]\r\n}"
chatMessageAttachment.SetContent(&content) 
name := null
chatMessageAttachment.SetName(&name) 
thumbnailUrl := null
chatMessageAttachment.SetThumbnailUrl(&thumbnailUrl) 

attachments := []graphmodels.ChatMessageAttachmentable {
	chatMessageAttachment,
}
requestBody.SetAttachments(attachments)


chatMessageHostedContent := graphmodels.NewChatMessageHostedContent()
contentBytes := []byte("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")
chatMessageHostedContent.SetContentBytes(&contentBytes) 
contentType := "image/png"
chatMessageHostedContent.SetContentType(&contentType) 
additionalData := map[string]interface{}{
	"@microsoft.graph.temporaryId" : "1", 
}
chatMessageHostedContent.SetAdditionalData(additionalData)
chatMessageHostedContent1 := graphmodels.NewChatMessageHostedContent()
contentBytes := []byte("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")
chatMessageHostedContent1.SetContentBytes(&contentBytes) 
contentType := "image/png"
chatMessageHostedContent1.SetContentType(&contentType) 
additionalData := map[string]interface{}{
	"@microsoft.graph.temporaryId" : "2", 
}
chatMessageHostedContent1.SetAdditionalData(additionalData)

hostedContents := []graphmodels.ChatMessageHostedContentable {
	chatMessageHostedContent,
	chatMessageHostedContent1,
}
requestBody.SetHostedContents(hostedContents)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
chatMessage.setSubject(null);
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>");
chatMessage.setBody(body);
LinkedList<ChatMessageAttachment> attachments = new LinkedList<ChatMessageAttachment>();
ChatMessageAttachment chatMessageAttachment = new ChatMessageAttachment();
chatMessageAttachment.setId("74d20c7f34aa4a7fb74e2b30004247c5");
chatMessageAttachment.setContentType("application/vnd.microsoft.card.adaptive");
chatMessageAttachment.setContentUrl(null);
chatMessageAttachment.setContent("{\r\n  \"$schema\": \"http://adaptivecards.io/schemas/adaptive-card.json\",\r\n  \"type\": \"AdaptiveCard\",\r\n  \"version\": \"1.2\",\r\n  \"speak\": \"The Seattle Seahawks beat the Carolina Panthers 40-7\",\r\n  \"body\": [\r\n    {\r\n      \"type\": \"Container\",\r\n      \"items\": [\r\n        {\r\n          \"type\": \"ColumnSet\",\r\n          \"columns\": [\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"auto\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"Image\",\r\n                  \"url\": \"../hostedContents/1/$value\",\r\n                  \"size\": \"Medium\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"SHADES\",\r\n                  \"horizontalAlignment\": \"Center\",\r\n                  \"weight\": \"Bolder\"\r\n                }\r\n              ]\r\n            },\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"stretch\",\r\n              \"separator\": true,\r\n              \"spacing\": \"Medium\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"2019-08-31T19:30:00Z\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"Final\",\r\n                  \"spacing\": \"None\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"40 - 7\",\r\n                  \"size\": \"ExtraLarge\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                }\r\n              ]\r\n            },\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"auto\",\r\n              \"separator\": true,\r\n              \"spacing\": \"Medium\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"Image\",\r\n                  \"url\": \"../hostedContents/2/$value\",\r\n                  \"size\": \"Medium\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"SKINS\",\r\n                  \"horizontalAlignment\": \"Center\",\r\n                  \"weight\": \"Bolder\"\r\n                }\r\n              ]\r\n            }\r\n          ]\r\n        }\r\n      ]\r\n    }\r\n  ]\r\n}");
chatMessageAttachment.setName(null);
chatMessageAttachment.setThumbnailUrl(null);
attachments.add(chatMessageAttachment);
chatMessage.setAttachments(attachments);
LinkedList<ChatMessageHostedContent> hostedContents = new LinkedList<ChatMessageHostedContent>();
ChatMessageHostedContent chatMessageHostedContent = new ChatMessageHostedContent();
byte[] contentBytes = Base64.getDecoder().decode("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");
chatMessageHostedContent.setContentBytes(contentBytes);
chatMessageHostedContent.setContentType("image/png");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@microsoft.graph.temporaryId", "1");
chatMessageHostedContent.setAdditionalData(additionalData);
hostedContents.add(chatMessageHostedContent);
ChatMessageHostedContent chatMessageHostedContent1 = new ChatMessageHostedContent();
byte[] contentBytes1 = Base64.getDecoder().decode("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");
chatMessageHostedContent1.setContentBytes(contentBytes1);
chatMessageHostedContent1.setContentType("image/png");
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("@microsoft.graph.temporaryId", "2");
chatMessageHostedContent1.setAdditionalData(additionalData1);
hostedContents.add(chatMessageHostedContent1);
chatMessage.setHostedContents(hostedContents);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
    subject: null,
    body: {
        contentType: 'html',
        content: '<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>'
    },
    attachments: [{
        id: '74d20c7f34aa4a7fb74e2b30004247c5',
        contentType: 'application/vnd.microsoft.card.adaptive',
        contentUrl: null,
        content: '{\r\n  \"$schema\': \'http://adaptivecards.io/schemas/adaptive-card.json\",\r\n  \"type\': \'AdaptiveCard\",\r\n  \"version\': \'1.2\",\r\n  \"speak\': \'The Seattle Seahawks beat the Carolina Panthers 40-7\",\r\n  \"body\': [\r\n    {\r\n      \'type\': \'Container\",\r\n      \"items\': [\r\n        {\r\n          \'type\': \'ColumnSet\",\r\n          \"columns\': [\r\n            {\r\n              \'type\': \'Column\",\r\n              \"width\': \'auto\",\r\n              \"items\': [\r\n                {\r\n                  \'type\': \'Image\",\r\n                  \"url\': \'../hostedContents/1/$value\",\r\n                  \"size\': \'Medium\"\r\n                },\r\n                {\r\n                  \"type\': \'TextBlock\",\r\n                  \"text\': \'SHADES\",\r\n                  \"horizontalAlignment\': \'Center\",\r\n                  \"weight\': \'Bolder\"\r\n                }\r\n              ]\r\n            },\r\n            {\r\n              \"type\': \'Column\",\r\n              \"width\': \'stretch\",\r\n              \"separator\': true,\r\n              \'spacing\': \'Medium\",\r\n              \"items\': [\r\n                {\r\n                  \'type\': \'TextBlock\",\r\n                  \"text\': \'2019-08-31T19:30:00Z\",\r\n                  \"horizontalAlignment\': \'Center\"\r\n                },\r\n                {\r\n                  \"type\': \'TextBlock\",\r\n                  \"text\': \'Final\",\r\n                  \"spacing\': \'None\",\r\n                  \"horizontalAlignment\': \'Center\"\r\n                },\r\n                {\r\n                  \"type\': \'TextBlock\",\r\n                  \"text\': \'40 - 7\",\r\n                  \"size\': \'ExtraLarge\",\r\n                  \"horizontalAlignment\': \'Center\"\r\n                }\r\n              ]\r\n            },\r\n            {\r\n              \"type\': \'Column\",\r\n              \"width\': \'auto\",\r\n              \"separator\': true,\r\n              \'spacing\': \'Medium\",\r\n              \"items\': [\r\n                {\r\n                  \'type\': \'Image\",\r\n                  \"url\': \'../hostedContents/2/$value\",\r\n                  \"size\': \'Medium\",\r\n                  \"horizontalAlignment\': \'Center\"\r\n                },\r\n                {\r\n                  \"type\': \'TextBlock\",\r\n                  \"text\': \'SKINS\",\r\n                  \"horizontalAlignment\': \'Center\",\r\n                  \"weight\': \"Bolder\"\r\n                }\r\n              ]\r\n            }\r\n          ]\r\n        }\r\n      ]\r\n    }\r\n  ]\r\n}",
        name: null,
        thumbnailUrl: null
    }],
    hostedContents: [{
        '@microsoft.graph.temporaryId': '1',
        contentBytes: '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',
        contentType: 'image/png'
    }, {
        '@microsoft.graph.temporaryId': '2',
        contentBytes: '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',
        contentType: 'image/png'
    }]
};

await client.api('/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageAttachment;
use Microsoft\Graph\Generated\Models\ChatMessageHostedContent;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$requestBody->setSubject(null);
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>');
$requestBody->setBody($body);
$attachmentsChatMessageAttachment1 = new ChatMessageAttachment();
$attachmentsChatMessageAttachment1->setId('74d20c7f34aa4a7fb74e2b30004247c5');
$attachmentsChatMessageAttachment1->setContentType('application/vnd.microsoft.card.adaptive');
$attachmentsChatMessageAttachment1->setContentUrl(null);
$attachmentsChatMessageAttachment1->setContent('{\r\n  \"$schema\": \"http://adaptivecards.io/schemas/adaptive-card.json\",\r\n  \"type\": \"AdaptiveCard\",\r\n  \"version\": \"1.2\",\r\n  \"speak\": \"The Seattle Seahawks beat the Carolina Panthers 40-7\",\r\n  \"body\": [\r\n    {\r\n      \"type\": \"Container\",\r\n      \"items\": [\r\n        {\r\n          \"type\": \"ColumnSet\",\r\n          \"columns\": [\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"auto\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"Image\",\r\n                  \"url\": \"../hostedContents/1/$value\",\r\n                  \"size\": \"Medium\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"SHADES\",\r\n                  \"horizontalAlignment\": \"Center\",\r\n                  \"weight\": \"Bolder\"\r\n                }\r\n              ]\r\n            },\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"stretch\",\r\n              \"separator\": true,\r\n              \"spacing\": \"Medium\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"2019-08-31T19:30:00Z\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"Final\",\r\n                  \"spacing\": \"None\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"40 - 7\",\r\n                  \"size\": \"ExtraLarge\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                }\r\n              ]\r\n            },\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"auto\",\r\n              \"separator\": true,\r\n              \"spacing\": \"Medium\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"Image\",\r\n                  \"url\": \"../hostedContents/2/$value\",\r\n                  \"size\": \"Medium\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"SKINS\",\r\n                  \"horizontalAlignment\": \"Center\",\r\n                  \"weight\": \"Bolder\"\r\n                }\r\n              ]\r\n            }\r\n          ]\r\n        }\r\n      ]\r\n    }\r\n  ]\r\n}');
$attachmentsChatMessageAttachment1->setName(null);
$attachmentsChatMessageAttachment1->setThumbnailUrl(null);
$attachmentsArray []= $attachmentsChatMessageAttachment1;
$requestBody->setAttachments($attachmentsArray);

$hostedContentsChatMessageHostedContent1 = new ChatMessageHostedContent();
$hostedContentsChatMessageHostedContent1->setContentBytes(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('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')));
$hostedContentsChatMessageHostedContent1->setContentType('image/png');
$additionalData = [
'@microsoft.graph.temporaryId' => '1',
];
$hostedContentsChatMessageHostedContent1->setAdditionalData($additionalData);
$hostedContentsArray []= $hostedContentsChatMessageHostedContent1;
$hostedContentsChatMessageHostedContent2 = new ChatMessageHostedContent();
$hostedContentsChatMessageHostedContent2->setContentBytes(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('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')));
$hostedContentsChatMessageHostedContent2->setContentType('image/png');
$additionalData = [
'@microsoft.graph.temporaryId' => '2',
];
$hostedContentsChatMessageHostedContent2->setAdditionalData($additionalData);
$hostedContentsArray []= $hostedContentsChatMessageHostedContent2;
$requestBody->setHostedContents($hostedContentsArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	subject = $null
	body = @{
		contentType = "html"
		content = "<attachment id="74d20c7f34aa4a7fb74e2b30004247c5"></attachment>"
	}
	attachments = @(
		@{
			id = "74d20c7f34aa4a7fb74e2b30004247c5"
			contentType = "application/vnd.microsoft.card.adaptive"
			contentUrl = $null
			content = '{
  "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
  "type": "AdaptiveCard",
  "version": "1.2",
  "speak": "The Seattle Seahawks beat the Carolina Panthers 40-7",
  "body": [
    {
      "type": "Container",
      "items": [
        {
          "type": "ColumnSet",
          "columns": [
            {
              "type": "Column",
              "width": "auto",
              "items": [
                {
                  "type": "Image",
                  "url": "../hostedContents/1/$value",
                  "size": "Medium"
                },
                {
                  "type": "TextBlock",
                  "text": "SHADES",
                  "horizontalAlignment": "Center",
                  "weight": "Bolder"
                }
              ]
            },
            {
              "type": "Column",
              "width": "stretch",
              "separator": true,
              "spacing": "Medium",
              "items": [
                {
                  "type": "TextBlock",
                  "text": "2019-08-31T19:30:00Z",
                  "horizontalAlignment": "Center"
                },
                {
                  "type": "TextBlock",
                  "text": "Final",
                  "spacing": "None",
                  "horizontalAlignment": "Center"
                },
                {
                  "type": "TextBlock",
                  "text": "40 - 7",
                  "size": "ExtraLarge",
                  "horizontalAlignment": "Center"
                }
              ]
            },
            {
              "type": "Column",
              "width": "auto",
              "separator": true,
              "spacing": "Medium",
              "items": [
                {
                  "type": "Image",
                  "url": "../hostedContents/2/$value",
                  "size": "Medium",
                  "horizontalAlignment": "Center"
                },
                {
                  "type": "TextBlock",
                  "text": "SKINS",
                  "horizontalAlignment": "Center",
                  "weight": "Bolder"
                }
              ]
            }
          ]
        }
      ]
    }
  ]
}'
			name = $null
			thumbnailUrl = $null
		}
	)
	hostedContents = @(
		@{
			"@microsoft.graph.temporaryId" = "1"
			contentBytes = [System.Text.Encoding]::ASCII.GetBytes("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")
			contentType = "image/png"
		}
		@{
			"@microsoft.graph.temporaryId" = "2"
			contentBytes = [System.Text.Encoding]::ASCII.GetBytes("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")
			contentType = "image/png"
		}
	)
}

New-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_attachment import ChatMessageAttachment
from msgraph.generated.models.chat_message_hosted_content import ChatMessageHostedContent
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	subject = None,
	body = ItemBody(
		content_type = BodyType.Html,
		content = "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>",
	),
	attachments = [
		ChatMessageAttachment(
			id = "74d20c7f34aa4a7fb74e2b30004247c5",
			content_type = "application/vnd.microsoft.card.adaptive",
			content_url = None,
			content = "{\r\n  \"$schema\": \"http://adaptivecards.io/schemas/adaptive-card.json\",\r\n  \"type\": \"AdaptiveCard\",\r\n  \"version\": \"1.2\",\r\n  \"speak\": \"The Seattle Seahawks beat the Carolina Panthers 40-7\",\r\n  \"body\": [\r\n    {\r\n      \"type\": \"Container\",\r\n      \"items\": [\r\n        {\r\n          \"type\": \"ColumnSet\",\r\n          \"columns\": [\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"auto\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"Image\",\r\n                  \"url\": \"../hostedContents/1/$value\",\r\n                  \"size\": \"Medium\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"SHADES\",\r\n                  \"horizontalAlignment\": \"Center\",\r\n                  \"weight\": \"Bolder\"\r\n                }\r\n              ]\r\n            },\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"stretch\",\r\n              \"separator\": true,\r\n              \"spacing\": \"Medium\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"2019-08-31T19:30:00Z\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"Final\",\r\n                  \"spacing\": \"None\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"40 - 7\",\r\n                  \"size\": \"ExtraLarge\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                }\r\n              ]\r\n            },\r\n            {\r\n              \"type\": \"Column\",\r\n              \"width\": \"auto\",\r\n              \"separator\": true,\r\n              \"spacing\": \"Medium\",\r\n              \"items\": [\r\n                {\r\n                  \"type\": \"Image\",\r\n                  \"url\": \"../hostedContents/2/$value\",\r\n                  \"size\": \"Medium\",\r\n                  \"horizontalAlignment\": \"Center\"\r\n                },\r\n                {\r\n                  \"type\": \"TextBlock\",\r\n                  \"text\": \"SKINS\",\r\n                  \"horizontalAlignment\": \"Center\",\r\n                  \"weight\": \"Bolder\"\r\n                }\r\n              ]\r\n            }\r\n          ]\r\n        }\r\n      ]\r\n    }\r\n  ]\r\n}",
			name = None,
			thumbnail_url = None,
		),
	],
	hosted_contents = [
		ChatMessageHostedContent(
			content_bytes = base64.urlsafe_b64decode("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"),
			content_type = "image/png",
			additional_data = {
					"@microsoft_graph_temporary_id" : "1",
			}
		),
		ChatMessageHostedContent(
			content_bytes = base64.urlsafe_b64decode("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"),
			content_type = "image/png",
			additional_data = {
					"@microsoft_graph_temporary_id" : "2",
			}
		),
	],
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('fbe2bf47-16c8-47cf-b4a5-4b9b187c508b')/channels('19%3A4a95f7d8db4c4e7fae857bcebe0623e6%40thread.tacv2')/messages/$entity",
    "id": "1616992043931",
    "replyToId": null,
    "etag": "1616992043931",
    "messageType": "message",
    "createdDateTime": "2021-03-29T04:27:23.931Z",
    "lastModifiedDateTime": "2021-03-29T04:27:23.931Z",
    "lastEditedDateTime": null,
    "deletedDateTime": null,
    "subject": null,
    "summary": null,
    "chatId": null,
    "importance": "normal",
    "locale": "en-us",
    "webUrl": "https://teams.microsoft.com/l/message/19%3A4a95f7d8db4c4e7fae857bcebe0623e6%40thread.tacv2/1616992043931?groupId=fbe2bf47-16c8-47cf-b4a5-4b9b187c508b&tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34&createdTime=1616992043931&parentMessageId=1616992043931",
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "user": {
            "@odata.type": "#microsoft.graph.teamworkUserIdentity",
            "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
            "displayName": "Robin Kline",
            "userIdentityType": "aadUser",
            "tenantId": "e61ef81e-8bd8-476a-92e8-4a62f8426fca"
        }
    },
    "body": {
        "contentType": "html",
        "content": "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>"
    },
    "channelIdentity": {
        "teamId": "fbe2bf47-16c8-47cf-b4a5-4b9b187c508b",
        "channelId": "19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2"
    },
    "attachments": [
        {
            "id": "74d20c7f34aa4a7fb74e2b30004247c5",
            "contentType": "application/vnd.microsoft.card.adaptive",
            "contentUrl": null,
            "content": "{  \"type\": \"AdaptiveCard\",  \"body\": [    {      \"items\": [        {          \"columns\": [            {              \"width\": \"auto\",              \"items\": [                {                  \"size\": \"medium\",                  \"url\": \"https://graph.microsoft.com/v1.0/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2/messages/1616992043931/hostedContents/aWQ9LHR5cGU9MSx1cmw9aHR0cHM6Ly91cy1hcGkuYXNtLnNreXBlLmNvbS92MS9vYmplY3RzLzAtd3VzLWQyLWEyNDc1OWVjOGZiZDRmOWFjYTkxN2M5N2EyOGNlNTQ1L3ZpZXdzL2ltZ28=/$value\",                  \"height\": \"auto\",                  \"type\": \"Image\"                },                {                  \"horizontalAlignment\": \"center\",                  \"text\": \"SHADES\",                  \"weight\": \"bolder\",                  \"type\": \"TextBlock\"                }              ],              \"type\": \"Column\"            },            {              \"width\": \"stretch\",              \"items\": [                {                  \"horizontalAlignment\": \"center\",                  \"text\": \"08/31/2019 19:30:00\",                  \"type\": \"TextBlock\"                },                {                  \"horizontalAlignment\": \"center\",                  \"text\": \"Final\",                  \"spacing\": \"None\",                  \"type\": \"TextBlock\"                },                {                  \"horizontalAlignment\": \"center\",                  \"size\": \"extraLarge\",                  \"text\": \"40 - 7\",                  \"type\": \"TextBlock\"                }              ],              \"spacing\": \"Medium\",              \"separator\": true,              \"type\": \"Column\"            },            {              \"width\": \"auto\",              \"items\": [                {                  \"horizontalAlignment\": \"center\",                  \"size\": \"medium\",                  \"url\": \"https://graph.microsoft.com/v1.0/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2/messages/1616992043931/hostedContents/aWQ9LHR5cGU9MSx1cmw9aHR0cHM6Ly91cy1hcGkuYXNtLnNreXBlLmNvbS92MS9vYmplY3RzLzAtd3VzLWQ1LTg1ZmNmMDQyNDc3MDJjNjkxODdiOTMwZjcwNTY3OTFhL3ZpZXdzL2ltZ28=/$value\",                  \"height\": \"auto\",                  \"type\": \"Image\"                },                {                  \"horizontalAlignment\": \"center\",                  \"text\": \"SKINS\",                  \"weight\": \"bolder\",                  \"type\": \"TextBlock\"                }              ],              \"spacing\": \"Medium\",              \"separator\": true,              \"type\": \"Column\"            }          ],          \"type\": \"ColumnSet\"        }      ],      \"type\": \"Container\"    }  ],  \"speak\": \"The Seattle Seahawks beat the Carolina Panthers 40-7\",  \"$schema\": \"http://adaptivecards.io/schemas/adaptive-card.json\",  \"version\": \"1.2\"}",
            "name": null,
            "thumbnailUrl": null
        }
    ],
    "mentions": [],
    "reactions": [],
    "messageHistory": []
}
```

### Example 8: @mention a channel in a channel message

#### Request

The following example shows a request. For information about how to get a list of channels in a team, see [List channels](https://learn.microsoft.com/en-us/graph/api/channel-list?view=graph-rest-1.0).

> Note: **conversationIdentityType** must be set to `channel` to @mention a channel.

- [HTTP](#tabpanel_8_http)
- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [JavaScript](#tabpanel_8_javascript)
- [PHP](#tabpanel_8_php)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)

```http
POST https://graph.microsoft.com/v1.0/teams/68a3e365-f7d9-4a56-b499-24332a9cc572/channels/19:0b50940236084d258c97b21bd01917b0@thread.skype/messages
Content-type: application/json

{
    "body": {
        "contentType": "html",
        "content": "<at id=\"0\">General</at>&nbsp;Hello there!"
    },
    "mentions": [
        {
            "id": 0,
            "mentionText": "General",
            "mentioned": {
                "conversation": {
                    "id": "19:0b50940236084d258c97b21bd01917b0@thread.skype",
                    "displayName": "General",
                    "conversationIdentityType": "channel"
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
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "<at id=\"0\">General</at>&nbsp;Hello there!",
	},
	Mentions = new List<ChatMessageMention>
	{
		new ChatMessageMention
		{
			Id = 0,
			MentionText = "General",
			Mentioned = new ChatMessageMentionedIdentitySet
			{
				Conversation = new TeamworkConversationIdentity
				{
					Id = "19:0b50940236084d258c97b21bd01917b0@thread.skype",
					DisplayName = "General",
					ConversationIdentityType = TeamworkConversationIdentityType.Channel,
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages.PostAsync(requestBody);
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
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "<at id=\"0\">General</at>&nbsp;Hello there!"
body.SetContent(&content) 
requestBody.SetBody(body)


chatMessageMention := graphmodels.NewChatMessageMention()
id := int32(0)
chatMessageMention.SetId(&id) 
mentionText := "General"
chatMessageMention.SetMentionText(&mentionText) 
mentioned := graphmodels.NewChatMessageMentionedIdentitySet()
conversation := graphmodels.NewTeamworkConversationIdentity()
id := "19:0b50940236084d258c97b21bd01917b0@thread.skype"
conversation.SetId(&id) 
displayName := "General"
conversation.SetDisplayName(&displayName) 
conversationIdentityType := graphmodels.CHANNEL_TEAMWORKCONVERSATIONIDENTITYTYPE 
conversation.SetConversationIdentityType(&conversationIdentityType) 
mentioned.SetConversation(conversation)
chatMessageMention.SetMentioned(mentioned)

mentions := []graphmodels.ChatMessageMentionable {
	chatMessageMention,
}
requestBody.SetMentions(mentions)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("<at id=\"0\">General</at>&nbsp;Hello there!");
chatMessage.setBody(body);
LinkedList<ChatMessageMention> mentions = new LinkedList<ChatMessageMention>();
ChatMessageMention chatMessageMention = new ChatMessageMention();
chatMessageMention.setId(0);
chatMessageMention.setMentionText("General");
ChatMessageMentionedIdentitySet mentioned = new ChatMessageMentionedIdentitySet();
TeamworkConversationIdentity conversation = new TeamworkConversationIdentity();
conversation.setId("19:0b50940236084d258c97b21bd01917b0@thread.skype");
conversation.setDisplayName("General");
conversation.setConversationIdentityType(TeamworkConversationIdentityType.Channel);
mentioned.setConversation(conversation);
chatMessageMention.setMentioned(mentioned);
mentions.add(chatMessageMention);
chatMessage.setMentions(mentions);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
    body: {
        contentType: 'html',
        content: '<at id=\"0\">General</at>&nbsp;Hello there!'
    },
    mentions: [
        {
            id: 0,
            mentionText: 'General',
            mentioned: {
                conversation: {
                    id: '19:0b50940236084d258c97b21bd01917b0@thread.skype',
                    displayName: 'General',
                    conversationIdentityType: 'channel'
                }
            }
        }
    ]
};

await client.api('/teams/68a3e365-f7d9-4a56-b499-24332a9cc572/channels/19:0b50940236084d258c97b21bd01917b0@thread.skype/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageMention;
use Microsoft\Graph\Generated\Models\ChatMessageMentionedIdentitySet;
use Microsoft\Graph\Generated\Models\TeamworkConversationIdentity;
use Microsoft\Graph\Generated\Models\TeamworkConversationIdentityType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('<at id=\"0\">General</at>&nbsp;Hello there!');
$requestBody->setBody($body);
$mentionsChatMessageMention1 = new ChatMessageMention();
$mentionsChatMessageMention1->setId(0);
$mentionsChatMessageMention1->setMentionText('General');
$mentionsChatMessageMention1Mentioned = new ChatMessageMentionedIdentitySet();
$mentionsChatMessageMention1MentionedConversation = new TeamworkConversationIdentity();
$mentionsChatMessageMention1MentionedConversation->setId('19:0b50940236084d258c97b21bd01917b0@thread.skype');
$mentionsChatMessageMention1MentionedConversation->setDisplayName('General');
$mentionsChatMessageMention1MentionedConversation->setConversationIdentityType(new TeamworkConversationIdentityType('channel'));
$mentionsChatMessageMention1Mentioned->setConversation($mentionsChatMessageMention1MentionedConversation);
$mentionsChatMessageMention1->setMentioned($mentionsChatMessageMention1Mentioned);
$mentionsArray []= $mentionsChatMessageMention1;
$requestBody->setMentions($mentionsArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	body = @{
		contentType = "html"
		content = "<at id="0">General</at>&nbsp;Hello there!"
	}
	mentions = @(
		@{
			id = 0
			mentionText = "General"
			mentioned = @{
				conversation = @{
					id = "19:0b50940236084d258c97b21bd01917b0@thread.skype"
					displayName = "General"
					conversationIdentityType = "channel"
				}
			}
		}
	)
}

New-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_mention import ChatMessageMention
from msgraph.generated.models.chat_message_mentioned_identity_set import ChatMessageMentionedIdentitySet
from msgraph.generated.models.teamwork_conversation_identity import TeamworkConversationIdentity
from msgraph.generated.models.teamwork_conversation_identity_type import TeamworkConversationIdentityType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	body = ItemBody(
		content_type = BodyType.Html,
		content = "<at id=\"0\">General</at>&nbsp;Hello there!",
	),
	mentions = [
		ChatMessageMention(
			id = 0,
			mention_text = "General",
			mentioned = ChatMessageMentionedIdentitySet(
				conversation = TeamworkConversationIdentity(
					id = "19:0b50940236084d258c97b21bd01917b0@thread.skype",
					display_name = "General",
					conversation_identity_type = TeamworkConversationIdentityType.Channel,
				),
			),
		),
	],
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('68a3e365-f7d9-4a56-b499-24332a9cc572')/channels('19%3A0b50940236084d258c97b21bd01917b0%40thread.skype')/messages/$entity",
    "id": "1625727486746",
    "replyToId": null,
    "etag": "1625727486746",
    "messageType": "message",
    "createdDateTime": "2021-07-08T06:58:06.746Z",
    "lastModifiedDateTime": "2021-07-08T06:58:06.746Z",
    "lastEditedDateTime": null,
    "deletedDateTime": null,
    "subject": null,
    "summary": null,
    "chatId": null,
    "importance": "normal",
    "locale": "en-us",
    "webUrl": "https://teams.microsoft.com/l/message/19%3A0b50940236084d258c97b21bd01917b0%40thread.skype/1625727486746?groupId=68a3e365-f7d9-4a56-b499-24332a9cc572&tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34&createdTime=1625727486746&parentMessageId=1625727486746",
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "user": {
            "@odata.type": "#microsoft.graph.teamworkUserIdentity",
            "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
            "displayName": "Robin Kline",
            "userIdentityType": "aadUser",
            "tenantId": "e61ef81e-8bd8-476a-92e8-4a62f8426fca"
        }
    },
    "body": {
        "contentType": "html",
        "content": "<at id=\"0\">General</at>&nbsp;Hello there!"
    },
    "channelIdentity": {
        "teamId": "68a3e365-f7d9-4a56-b499-24332a9cc572",
        "channelId": "19:0b50940236084d258c97b21bd01917b0@thread.skype"
    },
    "attachments": [],
    "mentions": [
        {
            "id": 0,
            "mentionText": "General",
            "mentioned": {
                "application": null,
                "device": null,
                "user": null,
                "tag": null,
                "conversation": {
                    "id": "19:0b50940236084d258c97b21bd01917b0@thread.skype",
                    "displayName": "General",
                    "conversationIdentityType": "channel"
                }
            }
        }
    ],
    "reactions": [],
    "messageHistory": []
}
```

### Example 9: @mention a team in a channel message

#### Request

The following example shows a request.

> Note: **conversationIdentityType** must be set to `team` to @mention a team.

- [HTTP](#tabpanel_9_http)
- [C#](#tabpanel_9_csharp)
- [Go](#tabpanel_9_go)
- [Java](#tabpanel_9_java)
- [JavaScript](#tabpanel_9_javascript)
- [PHP](#tabpanel_9_php)
- [PowerShell](#tabpanel_9_powershell)
- [Python](#tabpanel_9_python)

```http
POST https://graph.microsoft.com/v1.0/teams/68a3e365-f7d9-4a56-b499-24332a9cc572/channels/19:0b50940236084d258c97b21bd01917b0@thread.skype/messages
Content-type: application/json

{
    "body": {
        "contentType": "html",
        "content": "<at id=\"0\">GraphTesting</at>&nbsp;Hello team"
    },
    "mentions": [
        {
            "id": 0,
            "mentionText": "GraphTesting",
            "mentioned": {
                "conversation": {
                    "id": "68a3e365-f7d9-4a56-b499-24332a9cc572",
                    "displayName": "GraphTesting",
                    "conversationIdentityType": "team"
                }
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
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "<at id=\"0\">GraphTesting</at>&nbsp;Hello team",
	},
	Mentions = new List<ChatMessageMention>
	{
		new ChatMessageMention
		{
			Id = 0,
			MentionText = "GraphTesting",
			Mentioned = new ChatMessageMentionedIdentitySet
			{
				Conversation = new TeamworkConversationIdentity
				{
					Id = "68a3e365-f7d9-4a56-b499-24332a9cc572",
					DisplayName = "GraphTesting",
					ConversationIdentityType = TeamworkConversationIdentityType.Team,
				},
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
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages.PostAsync(requestBody);
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
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "<at id=\"0\">GraphTesting</at>&nbsp;Hello team"
body.SetContent(&content) 
requestBody.SetBody(body)


chatMessageMention := graphmodels.NewChatMessageMention()
id := int32(0)
chatMessageMention.SetId(&id) 
mentionText := "GraphTesting"
chatMessageMention.SetMentionText(&mentionText) 
mentioned := graphmodels.NewChatMessageMentionedIdentitySet()
conversation := graphmodels.NewTeamworkConversationIdentity()
id := "68a3e365-f7d9-4a56-b499-24332a9cc572"
conversation.SetId(&id) 
displayName := "GraphTesting"
conversation.SetDisplayName(&displayName) 
conversationIdentityType := graphmodels.TEAM_TEAMWORKCONVERSATIONIDENTITYTYPE 
conversation.SetConversationIdentityType(&conversationIdentityType) 
mentioned.SetConversation(conversation)
chatMessageMention.SetMentioned(mentioned)

mentions := []graphmodels.ChatMessageMentionable {
	chatMessageMention,
}
requestBody.SetMentions(mentions)
reactions := []graphmodels.ChatMessageReactionable {

}
requestBody.SetReactions(reactions)
messageHistory := []graphmodels.ChatMessageHistoryItemable {

}
requestBody.SetMessageHistory(messageHistory)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("<at id=\"0\">GraphTesting</at>&nbsp;Hello team");
chatMessage.setBody(body);
LinkedList<ChatMessageMention> mentions = new LinkedList<ChatMessageMention>();
ChatMessageMention chatMessageMention = new ChatMessageMention();
chatMessageMention.setId(0);
chatMessageMention.setMentionText("GraphTesting");
ChatMessageMentionedIdentitySet mentioned = new ChatMessageMentionedIdentitySet();
TeamworkConversationIdentity conversation = new TeamworkConversationIdentity();
conversation.setId("68a3e365-f7d9-4a56-b499-24332a9cc572");
conversation.setDisplayName("GraphTesting");
conversation.setConversationIdentityType(TeamworkConversationIdentityType.Team);
mentioned.setConversation(conversation);
chatMessageMention.setMentioned(mentioned);
mentions.add(chatMessageMention);
chatMessage.setMentions(mentions);
LinkedList<ChatMessageReaction> reactions = new LinkedList<ChatMessageReaction>();
chatMessage.setReactions(reactions);
LinkedList<ChatMessageHistoryItem> messageHistory = new LinkedList<ChatMessageHistoryItem>();
chatMessage.setMessageHistory(messageHistory);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
    body: {
        contentType: 'html',
        content: '<at id=\"0\">GraphTesting</at>&nbsp;Hello team'
    },
    mentions: [
        {
            id: 0,
            mentionText: 'GraphTesting',
            mentioned: {
                conversation: {
                    id: '68a3e365-f7d9-4a56-b499-24332a9cc572',
                    displayName: 'GraphTesting',
                    conversationIdentityType: 'team'
                }
            }
        }
    ],
    reactions: [],
    messageHistory: []
};

await client.api('/teams/68a3e365-f7d9-4a56-b499-24332a9cc572/channels/19:0b50940236084d258c97b21bd01917b0@thread.skype/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageMention;
use Microsoft\Graph\Generated\Models\ChatMessageMentionedIdentitySet;
use Microsoft\Graph\Generated\Models\TeamworkConversationIdentity;
use Microsoft\Graph\Generated\Models\TeamworkConversationIdentityType;
use Microsoft\Graph\Generated\Models\ChatMessageReaction;
use Microsoft\Graph\Generated\Models\ChatMessageHistoryItem;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('<at id=\"0\">GraphTesting</at>&nbsp;Hello team');
$requestBody->setBody($body);
$mentionsChatMessageMention1 = new ChatMessageMention();
$mentionsChatMessageMention1->setId(0);
$mentionsChatMessageMention1->setMentionText('GraphTesting');
$mentionsChatMessageMention1Mentioned = new ChatMessageMentionedIdentitySet();
$mentionsChatMessageMention1MentionedConversation = new TeamworkConversationIdentity();
$mentionsChatMessageMention1MentionedConversation->setId('68a3e365-f7d9-4a56-b499-24332a9cc572');
$mentionsChatMessageMention1MentionedConversation->setDisplayName('GraphTesting');
$mentionsChatMessageMention1MentionedConversation->setConversationIdentityType(new TeamworkConversationIdentityType('team'));
$mentionsChatMessageMention1Mentioned->setConversation($mentionsChatMessageMention1MentionedConversation);
$mentionsChatMessageMention1->setMentioned($mentionsChatMessageMention1Mentioned);
$mentionsArray []= $mentionsChatMessageMention1;
$requestBody->setMentions($mentionsArray);

$requestBody->setReactions([]);
$requestBody->setMessageHistory([]);

$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	body = @{
		contentType = "html"
		content = "<at id="0">GraphTesting</at>&nbsp;Hello team"
	}
	mentions = @(
		@{
			id = 0
			mentionText = "GraphTesting"
			mentioned = @{
				conversation = @{
					id = "68a3e365-f7d9-4a56-b499-24332a9cc572"
					displayName = "GraphTesting"
					conversationIdentityType = "team"
				}
			}
		}
	)
	reactions = @(
	)
	messageHistory = @(
	)
}

New-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_mention import ChatMessageMention
from msgraph.generated.models.chat_message_mentioned_identity_set import ChatMessageMentionedIdentitySet
from msgraph.generated.models.teamwork_conversation_identity import TeamworkConversationIdentity
from msgraph.generated.models.teamwork_conversation_identity_type import TeamworkConversationIdentityType
from msgraph.generated.models.chat_message_reaction import ChatMessageReaction
from msgraph.generated.models.chat_message_history_item import ChatMessageHistoryItem
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	body = ItemBody(
		content_type = BodyType.Html,
		content = "<at id=\"0\">GraphTesting</at>&nbsp;Hello team",
	),
	mentions = [
		ChatMessageMention(
			id = 0,
			mention_text = "GraphTesting",
			mentioned = ChatMessageMentionedIdentitySet(
				conversation = TeamworkConversationIdentity(
					id = "68a3e365-f7d9-4a56-b499-24332a9cc572",
					display_name = "GraphTesting",
					conversation_identity_type = TeamworkConversationIdentityType.Team,
				),
			),
		),
	],
	reactions = [
	],
	message_history = [
	],
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('68a3e365-f7d9-4a56-b499-24332a9cc572')/channels('19%3A0b50940236084d258c97b21bd01917b0%40thread.skype')/messages/$entity",
    "id": "1625727671938",
    "replyToId": null,
    "etag": "1625727671938",
    "messageType": "message",
    "createdDateTime": "2021-07-08T07:01:11.938Z",
    "lastModifiedDateTime": "2021-07-08T07:01:11.938Z",
    "lastEditedDateTime": null,
    "deletedDateTime": null,
    "subject": null,
    "summary": null,
    "chatId": null,
    "importance": "normal",
    "locale": "en-us",
    "webUrl": "https://teams.microsoft.com/l/message/19%3A0b50940236084d258c97b21bd01917b0%40thread.skype/1625727671938?groupId=68a3e365-f7d9-4a56-b499-24332a9cc572&tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34&createdTime=1625727671938&parentMessageId=1625727671938",
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "user": {
            "@odata.type": "#microsoft.graph.teamworkUserIdentity",
            "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
            "displayName": "Robin Kline",
            "userIdentityType": "aadUser",
            "tenantId": "e61ef81e-8bd8-476a-92e8-4a62f8426fca"
        }
    },
    "body": {
        "contentType": "html",
        "content": "<at id=\"0\">GraphTesting</at>&nbsp;Hello team"
    },
    "channelIdentity": {
        "teamId": "68a3e365-f7d9-4a56-b499-24332a9cc572",
        "channelId": "19:0b50940236084d258c97b21bd01917b0@thread.skype"
    },
    "attachments": [],
    "mentions": [
        {
            "id": 0,
            "mentionText": "GraphTesting",
            "mentioned": {
                "application": null,
                "device": null,
                "user": null,
                "tag": null,
                "conversation": {
                    "id": "68a3e365-f7d9-4a56-b499-24332a9cc572",
                    "displayName": "GraphTesting",
                    "conversationIdentityType": "team"
                }
            }
        }
    ],
    "reactions": [],
    "messageHistory": []
}
```

### Example 10: Send message that contains cards that are attributed to a Teams app

#### Request

The following example shows a request.

> **Note:** When specifying a Teams app to attribute a card to, the Microsoft Entra app ID used to make the call must match the Microsoft Entra app ID of the Teams app. The Microsoft Entra app ID of the Teams app can be specified in the *webApplicationInfo* section of the app's manifest. Refer to the following documentation on the current [Teams app manifest schema](https://learn.microsoft.com/en-us/microsoftteams/platform/resources/schema/manifest-schema).
> 
> Furthermore, the app specified in the payload must be installed for the user sending the message or in the chat or channel in which the message is being sent.

- [HTTP](#tabpanel_10_http)
- [C#](#tabpanel_10_csharp)
- [Go](#tabpanel_10_go)
- [Java](#tabpanel_10_java)
- [JavaScript](#tabpanel_10_javascript)
- [PHP](#tabpanel_10_php)
- [PowerShell](#tabpanel_10_powershell)
- [Python](#tabpanel_10_python)

```http
POST https://graph.microsoft.com/v1.0/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2/messages
Content-type: application/json

{
    "subject": null,
    "body": {
        "contentType": "html",
        "content": "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>"
    },
    "attachments": [
        {
            "id": "74d20c7f34aa4a7fb74e2b30004247c5",
            "contentType": "application/vnd.microsoft.card.thumbnail",
            "contentUrl": null,
            "content": "{\r\n  \"title\": \"This is an example of posting a card\",\r\n  \"subtitle\": \"<h3>This is the subtitle</h3>\",\r\n  \"text\": \"Here is some body text. <br>\\r\\nAnd a <a href=\\\"http://microsoft.com/\\\">hyperlink</a>. <br>\\r\\nAnd below that is some buttons:\",\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"Login to FakeBot\",\r\n      \"text\": \"login\",\r\n      \"displayText\": \"login\",\r\n      \"value\": \"login\"\r\n    }\r\n  ]\r\n}",
            "name": null,
            "thumbnailUrl": null,
            "teamsAppId": "881b8843-fd91-49e5-9ac2-47ec497ffbe5"
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
	Subject = null,
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>",
	},
	Attachments = new List<ChatMessageAttachment>
	{
		new ChatMessageAttachment
		{
			Id = "74d20c7f34aa4a7fb74e2b30004247c5",
			ContentType = "application/vnd.microsoft.card.thumbnail",
			ContentUrl = null,
			Content = "{\r\n  \"title\": \"This is an example of posting a card\",\r\n  \"subtitle\": \"<h3>This is the subtitle</h3>\",\r\n  \"text\": \"Here is some body text. <br>\r\nAnd a <a href=\"http://microsoft.com/\">hyperlink</a>. <br>\r\nAnd below that is some buttons:\",\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"Login to FakeBot\",\r\n      \"text\": \"login\",\r\n      \"displayText\": \"login\",\r\n      \"value\": \"login\"\r\n    }\r\n  ]\r\n}",
			Name = null,
			ThumbnailUrl = null,
			TeamsAppId = "881b8843-fd91-49e5-9ac2-47ec497ffbe5",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages.PostAsync(requestBody);
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
subject := null
requestBody.SetSubject(&subject) 
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>"
body.SetContent(&content) 
requestBody.SetBody(body)


chatMessageAttachment := graphmodels.NewChatMessageAttachment()
id := "74d20c7f34aa4a7fb74e2b30004247c5"
chatMessageAttachment.SetId(&id) 
contentType := "application/vnd.microsoft.card.thumbnail"
chatMessageAttachment.SetContentType(&contentType) 
contentUrl := null
chatMessageAttachment.SetContentUrl(&contentUrl) 
content := "{\r\n  \"title\": \"This is an example of posting a card\",\r\n  \"subtitle\": \"<h3>This is the subtitle</h3>\",\r\n  \"text\": \"Here is some body text. <br>\r\nAnd a <a href=\"http://microsoft.com/\">hyperlink</a>. <br>\r\nAnd below that is some buttons:\",\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"Login to FakeBot\",\r\n      \"text\": \"login\",\r\n      \"displayText\": \"login\",\r\n      \"value\": \"login\"\r\n    }\r\n  ]\r\n}"
chatMessageAttachment.SetContent(&content) 
name := null
chatMessageAttachment.SetName(&name) 
thumbnailUrl := null
chatMessageAttachment.SetThumbnailUrl(&thumbnailUrl) 
teamsAppId := "881b8843-fd91-49e5-9ac2-47ec497ffbe5"
chatMessageAttachment.SetTeamsAppId(&teamsAppId) 

attachments := []graphmodels.ChatMessageAttachmentable {
	chatMessageAttachment,
}
requestBody.SetAttachments(attachments)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
chatMessage.setSubject(null);
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>");
chatMessage.setBody(body);
LinkedList<ChatMessageAttachment> attachments = new LinkedList<ChatMessageAttachment>();
ChatMessageAttachment chatMessageAttachment = new ChatMessageAttachment();
chatMessageAttachment.setId("74d20c7f34aa4a7fb74e2b30004247c5");
chatMessageAttachment.setContentType("application/vnd.microsoft.card.thumbnail");
chatMessageAttachment.setContentUrl(null);
chatMessageAttachment.setContent("{\r\n  \"title\": \"This is an example of posting a card\",\r\n  \"subtitle\": \"<h3>This is the subtitle</h3>\",\r\n  \"text\": \"Here is some body text. <br>\r\nAnd a <a href=\"http://microsoft.com/\">hyperlink</a>. <br>\r\nAnd below that is some buttons:\",\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"Login to FakeBot\",\r\n      \"text\": \"login\",\r\n      \"displayText\": \"login\",\r\n      \"value\": \"login\"\r\n    }\r\n  ]\r\n}");
chatMessageAttachment.setName(null);
chatMessageAttachment.setThumbnailUrl(null);
chatMessageAttachment.setTeamsAppId("881b8843-fd91-49e5-9ac2-47ec497ffbe5");
attachments.add(chatMessageAttachment);
chatMessage.setAttachments(attachments);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
    subject: null,
    body: {
        contentType: 'html',
        content: '<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>'
    },
    attachments: [
        {
            id: '74d20c7f34aa4a7fb74e2b30004247c5',
            contentType: 'application/vnd.microsoft.card.thumbnail',
            contentUrl: null,
            content: '{\r\n  \"title\': \'This is an example of posting a card\",\r\n  \"subtitle\': \'<h3>This is the subtitle</h3>\",\r\n  \"text\': \'Here is some body text. <br>\\r\\nAnd a <a href=\\\"http://microsoft.com/\\\">hyperlink</a>. <br>\\r\\nAnd below that is some buttons:\",\r\n  \"buttons\': [\r\n    {\r\n      \'type\': \'messageBack\",\r\n      \"title\': \'Login to FakeBot\",\r\n      \"text\': \'login\",\r\n      \"displayText\': \'login\",\r\n      \"value\': \"login\"\r\n    }\r\n  ]\r\n}",
            name: null,
            thumbnailUrl: null,
            teamsAppId: '881b8843-fd91-49e5-9ac2-47ec497ffbe5'
        }
    ]
};

await client.api('/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageAttachment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$requestBody->setSubject(null);
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>');
$requestBody->setBody($body);
$attachmentsChatMessageAttachment1 = new ChatMessageAttachment();
$attachmentsChatMessageAttachment1->setId('74d20c7f34aa4a7fb74e2b30004247c5');
$attachmentsChatMessageAttachment1->setContentType('application/vnd.microsoft.card.thumbnail');
$attachmentsChatMessageAttachment1->setContentUrl(null);
$attachmentsChatMessageAttachment1->setContent('{\r\n  \"title\": \"This is an example of posting a card\",\r\n  \"subtitle\": \"<h3>This is the subtitle</h3>\",\r\n  \"text\": \"Here is some body text. <br>\r\nAnd a <a href=\"http://microsoft.com/\">hyperlink</a>. <br>\r\nAnd below that is some buttons:\",\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"Login to FakeBot\",\r\n      \"text\": \"login\",\r\n      \"displayText\": \"login\",\r\n      \"value\": \"login\"\r\n    }\r\n  ]\r\n}');
$attachmentsChatMessageAttachment1->setName(null);
$attachmentsChatMessageAttachment1->setThumbnailUrl(null);
$attachmentsChatMessageAttachment1->setTeamsAppId('881b8843-fd91-49e5-9ac2-47ec497ffbe5');
$attachmentsArray []= $attachmentsChatMessageAttachment1;
$requestBody->setAttachments($attachmentsArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	subject = $null
	body = @{
		contentType = "html"
		content = "<attachment id="74d20c7f34aa4a7fb74e2b30004247c5"></attachment>"
	}
	attachments = @(
		@{
			id = "74d20c7f34aa4a7fb74e2b30004247c5"
			contentType = "application/vnd.microsoft.card.thumbnail"
			contentUrl = $null
			content = '{
  "title": "This is an example of posting a card",
  "subtitle": "<h3>This is the subtitle</h3>",
  "text": "Here is some body text. <br>\r\nAnd a <a href=\"http://microsoft.com/\">hyperlink</a>. <br>\r\nAnd below that is some buttons:",
  "buttons": [
    {
      "type": "messageBack",
      "title": "Login to FakeBot",
      "text": "login",
      "displayText": "login",
      "value": "login"
    }
  ]
}'
			name = $null
			thumbnailUrl = $null
			teamsAppId = "881b8843-fd91-49e5-9ac2-47ec497ffbe5"
		}
	)
}

New-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_attachment import ChatMessageAttachment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	subject = None,
	body = ItemBody(
		content_type = BodyType.Html,
		content = "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>",
	),
	attachments = [
		ChatMessageAttachment(
			id = "74d20c7f34aa4a7fb74e2b30004247c5",
			content_type = "application/vnd.microsoft.card.thumbnail",
			content_url = None,
			content = "{\r\n  \"title\": \"This is an example of posting a card\",\r\n  \"subtitle\": \"<h3>This is the subtitle</h3>\",\r\n  \"text\": \"Here is some body text. <br>\r\nAnd a <a href=\"http://microsoft.com/\">hyperlink</a>. <br>\r\nAnd below that is some buttons:\",\r\n  \"buttons\": [\r\n    {\r\n      \"type\": \"messageBack\",\r\n      \"title\": \"Login to FakeBot\",\r\n      \"text\": \"login\",\r\n      \"displayText\": \"login\",\r\n      \"value\": \"login\"\r\n    }\r\n  ]\r\n}",
			name = None,
			thumbnail_url = None,
			teams_app_id = "881b8843-fd91-49e5-9ac2-47ec497ffbe5",
		),
	],
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('fbe2bf47-16c8-47cf-b4a5-4b9b187c508b')/channels('19%3A4a95f7d8db4c4e7fae857bcebe0623e6%40thread.tacv2')/messages/$entity",
    "id": "1616991851162",
    "replyToId": null,
    "etag": "1616991851162",
    "messageType": "message",
    "createdDateTime": "2021-03-29T04:24:11.162Z",
    "lastModifiedDateTime": "2021-03-29T04:24:11.162Z",
    "lastEditedDateTime": null,
    "deletedDateTime": null,
    "subject": null,
    "summary": null,
    "chatId": null,
    "importance": "normal",
    "locale": "en-us",
    "webUrl": "https://teams.microsoft.com/l/message/19%3A4a95f7d8db4c4e7fae857bcebe0623e6%40thread.tacv2/1616991851162?groupId=fbe2bf47-16c8-47cf-b4a5-4b9b187c508b&tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34&createdTime=1616991851162&parentMessageId=1616991851162",
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "user": {
            "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
            "displayName": "Robin Kline",
            "userIdentityType": "aadUser"
        }
    },
    "body": {
        "contentType": "html",
        "content": "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>"
    },
    "channelIdentity": {
        "teamId": "fbe2bf47-16c8-47cf-b4a5-4b9b187c508b",
        "channelId": "19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2"
    },
    "attachments": [
        {
            "id": "74d20c7f34aa4a7fb74e2b30004247c5",
            "contentType": "application/vnd.microsoft.card.thumbnail",
            "contentUrl": null,
            "content": "{  \"title\": \"This is an example of posting a card\",  \"subtitle\": \"<h3>This is the subtitle</h3>\",  \"text\": \"Here is some body text. <br>\\\\And a <a href=\\\"http://microsoft.com/\\\">hyperlink</a>. <br>\\\\And below that is some buttons:\",  \"buttons\": [    {      \"type\": \"messageBack\",      \"title\": \"Login to FakeBot\",      \"text\": \"login\",      \"displayText\": \"login\",      \"value\": \"login\"    }  ]}",
            "name": null,
            "thumbnailUrl": null,
            "teamsAppId": "881b8843-fd91-49e5-9ac2-47ec497ffbe5"
        }
    ],
    "onBehalfOf": null,
    "mentions": [],
    "reactions": [],
    "messageHistory": []
}
```

### Example 11: Send a message that contains an announcement

#### Request

The following example shows a request.

> **Note:** The Base64-encoded value for the **contentBytes** property is shortened for readability.

- [HTTP](#tabpanel_11_http)
- [C#](#tabpanel_11_csharp)
- [Go](#tabpanel_11_go)
- [Java](#tabpanel_11_java)
- [JavaScript](#tabpanel_11_javascript)
- [PHP](#tabpanel_11_php)
- [PowerShell](#tabpanel_11_powershell)
- [Python](#tabpanel_11_python)

```http
POST https://graph.microsoft.com/v1.0/teams/5c884e2f-83f8-4cff-af8e-0177f260b9f8/channels/19:81f49626414645c99469ee65a1a7e1a4@thread.tacv2/messages
Content-type: application/json

{
    "subject": "Announcement Subheading",
    "body": {
        "contentType": "text",
        "content": "<attachment id=\"d7ddbf876ae340c3a03bada395ec7da7\"></attachment>Announcement text"
    },
    "attachments": [
        {
            "id": "d7ddbf876ae340c3a03bada395ec7da7",
            "contentType": "application/vnd.microsoft.teams.messaging-announcementBanner",
            "contentUrl": null,
            "content": "{\"title\":\"\",\"cardImageType\":\"uploadedImage\",\"cardImageDetails\":{\"uploadedImageDetail\":{\"originalImage\":{\"source\":\"../hostedContents/2/$value\",\"imageContentType\":\"image/jpg\"},\"croppedImage\":{\"source\":\"../hostedContents/1/$value\"}}}}",
            "name": null,
            "thumbnailUrl": null
        }
    ],
    "hostedContents": [
        {
            "@microsoft.graph.temporaryId": "1",
            "contentBytes": "iVBORw0KGgoAAAANSUhEUgAABWMAAAEMCAYAAAChuaTsAAAAAXNSR0IArs4",
            "contentType": "image/png"
        },
        {
            "@microsoft.graph.temporaryId": "2",
            "contentBytes": "iVBORw0KGgoAAAANSUhEUgAAA5YAAAB4CAYAAACJrW0RAAAAAXNSR0IArs4",
            "contentType": "image/png"
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
	Subject = "Announcement Subheading",
	Body = new ItemBody
	{
		ContentType = BodyType.Text,
		Content = "<attachment id=\"d7ddbf876ae340c3a03bada395ec7da7\"></attachment>Announcement text",
	},
	Attachments = new List<ChatMessageAttachment>
	{
		new ChatMessageAttachment
		{
			Id = "d7ddbf876ae340c3a03bada395ec7da7",
			ContentType = "application/vnd.microsoft.teams.messaging-announcementBanner",
			ContentUrl = null,
			Content = "{\"title\":\"\",\"cardImageType\":\"uploadedImage\",\"cardImageDetails\":{\"uploadedImageDetail\":{\"originalImage\":{\"source\":\"../hostedContents/2/$value\",\"imageContentType\":\"image/jpg\"},\"croppedImage\":{\"source\":\"../hostedContents/1/$value\"}}}}",
			Name = null,
			ThumbnailUrl = null,
		},
	},
	HostedContents = new List<ChatMessageHostedContent>
	{
		new ChatMessageHostedContent
		{
			ContentBytes = Convert.FromBase64String("iVBORw0KGgoAAAANSUhEUgAABWMAAAEMCAYAAAChuaTsAAAAAXNSR0IArs4"),
			ContentType = "image/png",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"@microsoft.graph.temporaryId" , "1"
				},
			},
		},
		new ChatMessageHostedContent
		{
			ContentBytes = Convert.FromBase64String("iVBORw0KGgoAAAANSUhEUgAAA5YAAAB4CAYAAACJrW0RAAAAAXNSR0IArs4"),
			ContentType = "image/png",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"@microsoft.graph.temporaryId" , "2"
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages.PostAsync(requestBody);
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
subject := "Announcement Subheading"
requestBody.SetSubject(&subject) 
body := graphmodels.NewItemBody()
contentType := graphmodels.TEXT_BODYTYPE 
body.SetContentType(&contentType) 
content := "<attachment id=\"d7ddbf876ae340c3a03bada395ec7da7\"></attachment>Announcement text"
body.SetContent(&content) 
requestBody.SetBody(body)


chatMessageAttachment := graphmodels.NewChatMessageAttachment()
id := "d7ddbf876ae340c3a03bada395ec7da7"
chatMessageAttachment.SetId(&id) 
contentType := "application/vnd.microsoft.teams.messaging-announcementBanner"
chatMessageAttachment.SetContentType(&contentType) 
contentUrl := null
chatMessageAttachment.SetContentUrl(&contentUrl) 
content := "{\"title\":\"\",\"cardImageType\":\"uploadedImage\",\"cardImageDetails\":{\"uploadedImageDetail\":{\"originalImage\":{\"source\":\"../hostedContents/2/$value\",\"imageContentType\":\"image/jpg\"},\"croppedImage\":{\"source\":\"../hostedContents/1/$value\"}}}}"
chatMessageAttachment.SetContent(&content) 
name := null
chatMessageAttachment.SetName(&name) 
thumbnailUrl := null
chatMessageAttachment.SetThumbnailUrl(&thumbnailUrl) 

attachments := []graphmodels.ChatMessageAttachmentable {
	chatMessageAttachment,
}
requestBody.SetAttachments(attachments)


chatMessageHostedContent := graphmodels.NewChatMessageHostedContent()
contentBytes := []byte("iVBORw0KGgoAAAANSUhEUgAABWMAAAEMCAYAAAChuaTsAAAAAXNSR0IArs4")
chatMessageHostedContent.SetContentBytes(&contentBytes) 
contentType := "image/png"
chatMessageHostedContent.SetContentType(&contentType) 
additionalData := map[string]interface{}{
	"@microsoft.graph.temporaryId" : "1", 
}
chatMessageHostedContent.SetAdditionalData(additionalData)
chatMessageHostedContent1 := graphmodels.NewChatMessageHostedContent()
contentBytes := []byte("iVBORw0KGgoAAAANSUhEUgAAA5YAAAB4CAYAAACJrW0RAAAAAXNSR0IArs4")
chatMessageHostedContent1.SetContentBytes(&contentBytes) 
contentType := "image/png"
chatMessageHostedContent1.SetContentType(&contentType) 
additionalData := map[string]interface{}{
	"@microsoft.graph.temporaryId" : "2", 
}
chatMessageHostedContent1.SetAdditionalData(additionalData)

hostedContents := []graphmodels.ChatMessageHostedContentable {
	chatMessageHostedContent,
	chatMessageHostedContent1,
}
requestBody.SetHostedContents(hostedContents)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
chatMessage.setSubject("Announcement Subheading");
ItemBody body = new ItemBody();
body.setContentType(BodyType.Text);
body.setContent("<attachment id=\"d7ddbf876ae340c3a03bada395ec7da7\"></attachment>Announcement text");
chatMessage.setBody(body);
LinkedList<ChatMessageAttachment> attachments = new LinkedList<ChatMessageAttachment>();
ChatMessageAttachment chatMessageAttachment = new ChatMessageAttachment();
chatMessageAttachment.setId("d7ddbf876ae340c3a03bada395ec7da7");
chatMessageAttachment.setContentType("application/vnd.microsoft.teams.messaging-announcementBanner");
chatMessageAttachment.setContentUrl(null);
chatMessageAttachment.setContent("{\"title\":\"\",\"cardImageType\":\"uploadedImage\",\"cardImageDetails\":{\"uploadedImageDetail\":{\"originalImage\":{\"source\":\"../hostedContents/2/$value\",\"imageContentType\":\"image/jpg\"},\"croppedImage\":{\"source\":\"../hostedContents/1/$value\"}}}}");
chatMessageAttachment.setName(null);
chatMessageAttachment.setThumbnailUrl(null);
attachments.add(chatMessageAttachment);
chatMessage.setAttachments(attachments);
LinkedList<ChatMessageHostedContent> hostedContents = new LinkedList<ChatMessageHostedContent>();
ChatMessageHostedContent chatMessageHostedContent = new ChatMessageHostedContent();
byte[] contentBytes = Base64.getDecoder().decode("iVBORw0KGgoAAAANSUhEUgAABWMAAAEMCAYAAAChuaTsAAAAAXNSR0IArs4");
chatMessageHostedContent.setContentBytes(contentBytes);
chatMessageHostedContent.setContentType("image/png");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@microsoft.graph.temporaryId", "1");
chatMessageHostedContent.setAdditionalData(additionalData);
hostedContents.add(chatMessageHostedContent);
ChatMessageHostedContent chatMessageHostedContent1 = new ChatMessageHostedContent();
byte[] contentBytes1 = Base64.getDecoder().decode("iVBORw0KGgoAAAANSUhEUgAAA5YAAAB4CAYAAACJrW0RAAAAAXNSR0IArs4");
chatMessageHostedContent1.setContentBytes(contentBytes1);
chatMessageHostedContent1.setContentType("image/png");
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("@microsoft.graph.temporaryId", "2");
chatMessageHostedContent1.setAdditionalData(additionalData1);
hostedContents.add(chatMessageHostedContent1);
chatMessage.setHostedContents(hostedContents);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
    subject: 'Announcement Subheading',
    body: {
        contentType: 'text',
        content: '<attachment id=\"d7ddbf876ae340c3a03bada395ec7da7\"></attachment>Announcement text'
    },
    attachments: [
        {
            id: 'd7ddbf876ae340c3a03bada395ec7da7',
            contentType: 'application/vnd.microsoft.teams.messaging-announcementBanner',
            contentUrl: null,
            content: '{\"title\':\'\",\"cardImageType\':\'uploadedImage\",\"cardImageDetails\':{\'uploadedImageDetail\':{\'originalImage\':{\'source\':\'../hostedContents/2/$value\",\"imageContentType\':\'image/jpg\"},\"croppedImage\':{\'source\':\"../hostedContents/1/$value\"}}}}",
            name: null,
            thumbnailUrl: null
        }
    ],
    hostedContents: [
        {
            '@microsoft.graph.temporaryId': '1',
            contentBytes: 'iVBORw0KGgoAAAANSUhEUgAABWMAAAEMCAYAAAChuaTsAAAAAXNSR0IArs4',
            contentType: 'image/png'
        },
        {
            '@microsoft.graph.temporaryId': '2',
            contentBytes: 'iVBORw0KGgoAAAANSUhEUgAAA5YAAAB4CAYAAACJrW0RAAAAAXNSR0IArs4',
            contentType: 'image/png'
        }
    ]
};

await client.api('/teams/5c884e2f-83f8-4cff-af8e-0177f260b9f8/channels/19:81f49626414645c99469ee65a1a7e1a4@thread.tacv2/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageAttachment;
use Microsoft\Graph\Generated\Models\ChatMessageHostedContent;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$requestBody->setSubject('Announcement Subheading');
$body = new ItemBody();
$body->setContentType(new BodyType('text'));
$body->setContent('<attachment id=\"d7ddbf876ae340c3a03bada395ec7da7\"></attachment>Announcement text');
$requestBody->setBody($body);
$attachmentsChatMessageAttachment1 = new ChatMessageAttachment();
$attachmentsChatMessageAttachment1->setId('d7ddbf876ae340c3a03bada395ec7da7');
$attachmentsChatMessageAttachment1->setContentType('application/vnd.microsoft.teams.messaging-announcementBanner');
$attachmentsChatMessageAttachment1->setContentUrl(null);
$attachmentsChatMessageAttachment1->setContent('{\"title\":\"\",\"cardImageType\":\"uploadedImage\",\"cardImageDetails\":{\"uploadedImageDetail\":{\"originalImage\":{\"source\":\"../hostedContents/2/$value\",\"imageContentType\":\"image/jpg\"},\"croppedImage\":{\"source\":\"../hostedContents/1/$value\"}}}}');
$attachmentsChatMessageAttachment1->setName(null);
$attachmentsChatMessageAttachment1->setThumbnailUrl(null);
$attachmentsArray []= $attachmentsChatMessageAttachment1;
$requestBody->setAttachments($attachmentsArray);

$hostedContentsChatMessageHostedContent1 = new ChatMessageHostedContent();
$hostedContentsChatMessageHostedContent1->setContentBytes(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('iVBORw0KGgoAAAANSUhEUgAABWMAAAEMCAYAAAChuaTsAAAAAXNSR0IArs4')));
$hostedContentsChatMessageHostedContent1->setContentType('image/png');
$additionalData = [
'@microsoft.graph.temporaryId' => '1',
];
$hostedContentsChatMessageHostedContent1->setAdditionalData($additionalData);
$hostedContentsArray []= $hostedContentsChatMessageHostedContent1;
$hostedContentsChatMessageHostedContent2 = new ChatMessageHostedContent();
$hostedContentsChatMessageHostedContent2->setContentBytes(\GuzzleHttp\Psr7\Utils::streamFor(base64_decode('iVBORw0KGgoAAAANSUhEUgAAA5YAAAB4CAYAAACJrW0RAAAAAXNSR0IArs4')));
$hostedContentsChatMessageHostedContent2->setContentType('image/png');
$additionalData = [
'@microsoft.graph.temporaryId' => '2',
];
$hostedContentsChatMessageHostedContent2->setAdditionalData($additionalData);
$hostedContentsArray []= $hostedContentsChatMessageHostedContent2;
$requestBody->setHostedContents($hostedContentsArray);


$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	subject = "Announcement Subheading"
	body = @{
		contentType = "text"
		content = "<attachment id="d7ddbf876ae340c3a03bada395ec7da7"></attachment>Announcement text"
	}
	attachments = @(
		@{
			id = "d7ddbf876ae340c3a03bada395ec7da7"
			contentType = "application/vnd.microsoft.teams.messaging-announcementBanner"
			contentUrl = $null
			content = '{"title":"","cardImageType":"uploadedImage","cardImageDetails":{"uploadedImageDetail":{"originalImage":{"source":"../hostedContents/2/$value","imageContentType":"image/jpg"},"croppedImage":{"source":"../hostedContents/1/$value"}}}}'
			name = $null
			thumbnailUrl = $null
		}
	)
	hostedContents = @(
		@{
			"@microsoft.graph.temporaryId" = "1"
			contentBytes = [System.Text.Encoding]::ASCII.GetBytes("iVBORw0KGgoAAAANSUhEUgAABWMAAAEMCAYAAAChuaTsAAAAAXNSR0IArs4")
			contentType = "image/png"
		}
		@{
			"@microsoft.graph.temporaryId" = "2"
			contentBytes = [System.Text.Encoding]::ASCII.GetBytes("iVBORw0KGgoAAAANSUhEUgAAA5YAAAB4CAYAAACJrW0RAAAAAXNSR0IArs4")
			contentType = "image/png"
		}
	)
}

New-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_attachment import ChatMessageAttachment
from msgraph.generated.models.chat_message_hosted_content import ChatMessageHostedContent
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	subject = "Announcement Subheading",
	body = ItemBody(
		content_type = BodyType.Text,
		content = "<attachment id=\"d7ddbf876ae340c3a03bada395ec7da7\"></attachment>Announcement text",
	),
	attachments = [
		ChatMessageAttachment(
			id = "d7ddbf876ae340c3a03bada395ec7da7",
			content_type = "application/vnd.microsoft.teams.messaging-announcementBanner",
			content_url = None,
			content = "{\"title\":\"\",\"cardImageType\":\"uploadedImage\",\"cardImageDetails\":{\"uploadedImageDetail\":{\"originalImage\":{\"source\":\"../hostedContents/2/$value\",\"imageContentType\":\"image/jpg\"},\"croppedImage\":{\"source\":\"../hostedContents/1/$value\"}}}}",
			name = None,
			thumbnail_url = None,
		),
	],
	hosted_contents = [
		ChatMessageHostedContent(
			content_bytes = base64.urlsafe_b64decode("iVBORw0KGgoAAAANSUhEUgAABWMAAAEMCAYAAAChuaTsAAAAAXNSR0IArs4"),
			content_type = "image/png",
			additional_data = {
					"@microsoft_graph_temporary_id" : "1",
			}
		),
		ChatMessageHostedContent(
			content_bytes = base64.urlsafe_b64decode("iVBORw0KGgoAAAANSUhEUgAAA5YAAAB4CAYAAACJrW0RAAAAAXNSR0IArs4"),
			content_type = "image/png",
			additional_data = {
					"@microsoft_graph_temporary_id" : "2",
			}
		),
	],
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('5c884e2f-83f8-4cff-af8e-0177f260b9f8')/channels('19%3A81f49626414645c99469ee65a1a7e1a4%40thread.tacv2')/messages/$entity",
    "id": "1675104302171",
    "replyToId": null,
    "etag": "1675104302171",
    "messageType": "message",
    "createdDateTime": "2023-01-30T18:45:02.171Z",
    "lastModifiedDateTime": "2023-01-30T18:45:02.171Z",
    "lastEditedDateTime": null,
    "deletedDateTime": null,
    "subject": "Announcement Subheading",
    "summary": null,
    "chatId": null,
    "importance": "normal",
    "locale": "en-us",
    "webUrl": "https://teams.microsoft.com/l/message/19%3A81f49626414645c99469ee65a1a7e1a4%40thread.tacv2/1675104302171?groupId=5c884e2f-83f8-4cff-af8e-0177f260b9f8&tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34&createdTime=1675104302171&parentMessageId=1675104302171",
    "onBehalfOf": null,
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "user": {
            "id": "28c10244-4bad-4fda-993c-f332faef94f0",
            "displayName": "Test User",
            "userIdentityType": "aadUser"
        }
    },
    "body": {
        "contentType": "text",
        "content": "<attachment id=\"d7ddbf876ae340c3a03bada395ec7da7\"></attachment>Announcement text"
    },
    "channelIdentity": {
        "teamId": "5c884e2f-83f8-4cff-af8e-0177f260b9f8",
        "channelId": "19:81f49626414645c99469ee65a1a7e1a4@thread.tacv2"
    },
    "attachments": [
        {
            "id": "d7ddbf876ae340c3a03bada395ec7da7",
            "contentType": "application/vnd.microsoft.teams.messaging-announcementBanner",
            "contentUrl": null,
            "content": "{\"title\":\"Test title\",\"cardImageType\":\"uploadedImage\",\"cardImageDetails\":{\"uploadedImageDetail\":{\"originalImage\":{\"source\":\"https://graph.microsoft.com/v1.0/teams/5c884e2f-83f8-4cff-af8e-0177f260b9f8/channels/19%3A81f49626414645c99469ee65a1a7e1a4%40thread.tacv2/messages/1736180726031/hostedContents/aWQ9LHR5cGU9MSx1cmw9aHR0cHM6Ly91cy1hcGkuYXNtLnNreXBlLmNvbS92MS9vYmplY3RzLzAtd3VzLWQ5LTEzMzNjYzJhOWFlYTdjOWYwMWJmNjc2YWU5YWE3NTdhL3ZpZXdzL2ltZ3BzaF9mdWxsc2l6ZQ==/$value\",\"width\":1317,\"height\":366,\"croppedWidth\":1317.0,\"croppedHeight\":366.0,\"leftMargin\":0.0,\"topMargin\":0.0},\"croppedImage\":{\"source\":\"https://graph.microsoft.com/v1.0/teams/5c884e2f-83f8-4cff-af8e-0177f260b9f8/channels/19%3A81f49626414645c99469ee65a1a7e1a4%40thread.tacv2/messages/1736180726031/hostedContents/aWQ9LHR5cGU9MSx1cmw9aHR0cHM6Ly91cy1hcGkuYXNtLnNreXBlLmNvbS92MS9vYmplY3RzLzAtd3VzLWQ5LTEzMzNjYzJhOWFlYTdjOWYwMWJmNjc2YWU5YWE3NTdhL3ZpZXdzL2ltZ3BzaF9mdWxsc2l6ZQ==/$value\"}}}}",
            "name": null,
            "thumbnailUrl": null,
            "teamsAppId": null
        }
    ],
    "mentions": [],
    "reactions": [],
    "messageHistory": []
}
```

### Example 12: Send a message with an emoji

#### Request

The following example shows a request.

- [HTTP](#tabpanel_12_http)
- [C#](#tabpanel_12_csharp)
- [Go](#tabpanel_12_go)
- [Java](#tabpanel_12_java)
- [JavaScript](#tabpanel_12_javascript)
- [PHP](#tabpanel_12_php)
- [PowerShell](#tabpanel_12_powershell)
- [Python](#tabpanel_12_python)

```http
POST https://graph.microsoft.com/v1.0/chats/19:b7867210a3fa4848a5a2a30c210eb9ae@thread.v2/messages
Content-type: application/json

{
    "body": {
        "contentType": "html",
        "content": "<emoji alt=\"😶‍🌫️\"></emoji>"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ChatMessage
{
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "<emoji alt=\"😶‍🌫️\"></emoji>",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Chats["{chat-id}"].Messages.PostAsync(requestBody);
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
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "<emoji alt=\"😶‍🌫️\"></emoji>"
body.SetContent(&content) 
requestBody.SetBody(body)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Chats().ByChatId("chat-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("<emoji alt=\"😶‍🌫️\"></emoji>");
chatMessage.setBody(body);
ChatMessage result = graphClient.chats().byChatId("{chat-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
    body: {
        contentType: 'html',
        content: '<emoji alt=\"😶‍🌫️\"></emoji>'
    }
};

await client.api('/chats/19:b7867210a3fa4848a5a2a30c210eb9ae@thread.v2/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('<emoji alt=\"😶‍🌫️\"></emoji>');
$requestBody->setBody($body);

$result = $graphServiceClient->chats()->byChatId('chat-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	body = @{
		contentType = "html"
		content = "<emoji alt="😶‍🌫️"></emoji>"
	}
}

New-MgChatMessage -ChatId $chatId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	body = ItemBody(
		content_type = BodyType.Html,
		content = "<emoji alt=\"😶‍🌫️\"></emoji>",
	),
)

result = await graph_client.chats.by_chat_id('chat-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#chats('19%3Ab7867210a3fa4848a5a2a30c210eb9ae%40thread.v2')/messages/$entity",
    "id": "1678894699092",
    "replyToId": null,
    "etag": "1678894699092",
    "messageType": "message",
    "createdDateTime": "2023-03-15T15:38:19.092Z",
    "lastModifiedDateTime": "2023-03-15T15:38:19.092Z",
    "lastEditedDateTime": null,
    "deletedDateTime": null,
    "subject": null,
    "summary": null,
    "chatId": "19:b7867210a3fa4848a5a2a30c210eb9ae@thread.v2",
    "importance": "normal",
    "locale": "en-us",
    "webUrl": null,
    "channelIdentity": null,
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "user": {
            "@odata.type": "#microsoft.graph.teamworkUserIdentity",
            "id": "cf944cab-afa6-4b26-81d6-bdf9f6ea04f2",
            "displayName": "Ramjot Singh",
            "userIdentityType": "aadUser"
        }
    },
    "body": {
        "contentType": "html",
        "content": "<emoji id=\"faceinclouds\" alt=\"😶‍🌫️\" title=\"Face in clouds\"></emoji>"
    },
    "attachments": [],
    "mentions": [],
    "reactions": []
}
```

### Example 13: Send a message with a Loop component

The following example shows how to send a message with an embedded Loop component. The Loop component is a special type of message that allows users to collaborate in real-time on a shared task or project. It can be used to create a collaborative workspace within a chat or channel.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_13_http)
- [C#](#tabpanel_13_csharp)
- [Go](#tabpanel_13_go)
- [Java](#tabpanel_13_java)
- [JavaScript](#tabpanel_13_javascript)
- [PHP](#tabpanel_13_php)
- [PowerShell](#tabpanel_13_powershell)
- [Python](#tabpanel_13_python)

```msgraph
POST https://graph.microsoft.com/v1.0/chats/19:7fb82b685f9c457296a0ab6a1d98b4c1@thread.v2/messages
Content-Type: application/json

{
  "body": {
    "contentType": "html",
    "content": "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>"
  },
  "attachments": [
    {
      "id": "74d20c7f34aa4a7fb74e2b30004247c5",
      "contentType": "application/vnd.microsoft.card.fluidEmbedCard",
      "content": "{\"componentUrl\": \"{LoopComponent_url}\", \"sourceType\": \"Compose\"}",
      "name": null,
      "thumbnailUrl": null,
      "teamsAppId": "FluidEmbedCard"
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
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>",
	},
	Attachments = new List<ChatMessageAttachment>
	{
		new ChatMessageAttachment
		{
			Id = "74d20c7f34aa4a7fb74e2b30004247c5",
			ContentType = "application/vnd.microsoft.card.fluidEmbedCard",
			Content = "{\"componentUrl\": \"{LoopComponent_url}\", \"sourceType\": \"Compose\"}",
			Name = null,
			ThumbnailUrl = null,
			TeamsAppId = "FluidEmbedCard",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Chats["{chat-id}"].Messages.PostAsync(requestBody);
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
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>"
body.SetContent(&content) 
requestBody.SetBody(body)


chatMessageAttachment := graphmodels.NewChatMessageAttachment()
id := "74d20c7f34aa4a7fb74e2b30004247c5"
chatMessageAttachment.SetId(&id) 
contentType := "application/vnd.microsoft.card.fluidEmbedCard"
chatMessageAttachment.SetContentType(&contentType) 
content := "{\"componentUrl\": \"{LoopComponent_url}\", \"sourceType\": \"Compose\"}"
chatMessageAttachment.SetContent(&content) 
name := null
chatMessageAttachment.SetName(&name) 
thumbnailUrl := null
chatMessageAttachment.SetThumbnailUrl(&thumbnailUrl) 
teamsAppId := "FluidEmbedCard"
chatMessageAttachment.SetTeamsAppId(&teamsAppId) 

attachments := []graphmodels.ChatMessageAttachmentable {
	chatMessageAttachment,
}
requestBody.SetAttachments(attachments)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Chats().ByChatId("chat-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>");
chatMessage.setBody(body);
LinkedList<ChatMessageAttachment> attachments = new LinkedList<ChatMessageAttachment>();
ChatMessageAttachment chatMessageAttachment = new ChatMessageAttachment();
chatMessageAttachment.setId("74d20c7f34aa4a7fb74e2b30004247c5");
chatMessageAttachment.setContentType("application/vnd.microsoft.card.fluidEmbedCard");
chatMessageAttachment.setContent("{\"componentUrl\": \"{LoopComponent_url}\", \"sourceType\": \"Compose\"}");
chatMessageAttachment.setName(null);
chatMessageAttachment.setThumbnailUrl(null);
chatMessageAttachment.setTeamsAppId("FluidEmbedCard");
attachments.add(chatMessageAttachment);
chatMessage.setAttachments(attachments);
ChatMessage result = graphClient.chats().byChatId("{chat-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
  body: {
    contentType: 'html',
    content: '<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>'
  },
  attachments: [
    {
      id: '74d20c7f34aa4a7fb74e2b30004247c5',
      contentType: 'application/vnd.microsoft.card.fluidEmbedCard',
      content: '{\"componentUrl\': \'{LoopComponent_url}\", \"sourceType\': \"Compose\"}",
      name: null,
      thumbnailUrl: null,
      teamsAppId: 'FluidEmbedCard'
    }
  ]
};

await client.api('/chats/19:7fb82b685f9c457296a0ab6a1d98b4c1@thread.v2/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\ChatMessageAttachment;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>');
$requestBody->setBody($body);
$attachmentsChatMessageAttachment1 = new ChatMessageAttachment();
$attachmentsChatMessageAttachment1->setId('74d20c7f34aa4a7fb74e2b30004247c5');
$attachmentsChatMessageAttachment1->setContentType('application/vnd.microsoft.card.fluidEmbedCard');
$attachmentsChatMessageAttachment1->setContent('{\"componentUrl\": \"{LoopComponent_url}\", \"sourceType\": \"Compose\"}');
$attachmentsChatMessageAttachment1->setName(null);
$attachmentsChatMessageAttachment1->setThumbnailUrl(null);
$attachmentsChatMessageAttachment1->setTeamsAppId('FluidEmbedCard');
$attachmentsArray []= $attachmentsChatMessageAttachment1;
$requestBody->setAttachments($attachmentsArray);


$result = $graphServiceClient->chats()->byChatId('chat-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	body = @{
		contentType = "html"
		content = "<attachment id="74d20c7f34aa4a7fb74e2b30004247c5"></attachment>"
	}
	attachments = @(
		@{
			id = "74d20c7f34aa4a7fb74e2b30004247c5"
			contentType = "application/vnd.microsoft.card.fluidEmbedCard"
			content = '{"componentUrl": '{LoopComponent_url}', "sourceType": "Compose"}'
			name = $null
			thumbnailUrl = $null
			teamsAppId = "FluidEmbedCard"
		}
	)
}

New-MgChatMessage -ChatId $chatId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.chat_message_attachment import ChatMessageAttachment
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	body = ItemBody(
		content_type = BodyType.Html,
		content = "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>",
	),
	attachments = [
		ChatMessageAttachment(
			id = "74d20c7f34aa4a7fb74e2b30004247c5",
			content_type = "application/vnd.microsoft.card.fluidEmbedCard",
			content = "{\"componentUrl\": \"{LoopComponent_url}\", \"sourceType\": \"Compose\"}",
			name = None,
			thumbnail_url = None,
			teams_app_id = "FluidEmbedCard",
		),
	],
)

result = await graph_client.chats.by_chat_id('chat-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('5c884e2f-83f8-4cff-af8e-0177f260b9f8')/channels('19%3A81f49626414645c99469ee65a1a7e1a4%40thread.tacv2')/messages/$entity",
  "id": "1675104302171",
  "replyToId": null,
  "etag": "1675104302171",
  "messageType": "message",
  "createdDateTime": "2023-01-30T18:45:02.171Z",
  "lastModifiedDateTime": "2023-01-30T18:45:02.171Z",
  "lastEditedDateTime": null,
  "deletedDateTime": null,
  "subject": "Announcement Subheading",
  "summary": null,
  "chatId": null,
  "importance": "normal",
  "locale": "en-us",
  "webUrl": "https://teams.microsoft.com/l/message/19%3A81f49626414645c99469ee65a1a7e1a4%40thread.tacv2/1675104302171?groupId=5c884e2f-83f8-4cff-af8e-0177f260b9f8&tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34&createdTime=1675104302171&parentMessageId=1675104302171",
  "onBehalfOf": null,
  "policyViolation": null,
  "eventDetail": null,
  "from": {
    "application": null,
    "device": null,
    "user": {
      "id": "28c10244-4bad-4fda-993c-f332faef94f0",
      "displayName": "Adele Vance",
      "userIdentityType": "aadUser"
    }
  },
  "body": {
    "contentType": "text",
    "content": "<attachment id=\"74d20c7f34aa4a7fb74e2b30004247c5\"></attachment>"
  },
  "channelIdentity": {
    "teamId": "5c884e2f-83f8-4cff-af8e-0177f260b9f8",
    "channelId": "19:81f49626414645c99469ee65a1a7e1a4@thread.tacv2"
  },
  "attachments": [
    {
      "id": "74d20c7f34aa4a7fb74e2b30004247c5",
      "contentType": "application/vnd.microsoft.card.fluidEmbedCard",
      "contentUrl": null,
      "content": "{\"componentUrl\": \"{LoopComponent_url}\", \"sourceType\": \"Compose\"}",
      "name": null,
      "thumbnailUrl": null,
      "teamsAppId": "FluidEmbedCard"
    }
  ],
  "mentions": [],
  "reactions": []
}
```

### Example 14: Send a message with a code block

The following example shows how to send a message with a code block.

Note

- To specify a language for syntax highlighting in a code block, use the `class` attribute in the `<codeblock>` HTML element.
- If no language is specified, the code block defaults to plaintext formatting.
- Supported languages include: `bash`, `c`, `cpp`, `csharp`, `css`, `dart`, `dockerfile`, `dos`, `go`, `graphql`, `html`, `http`, `java`, `javascript`, `json`, `jsp`, `jsx`, `kotlin`, `markdown`, `objectivec`, `octave`, `perl`, `php`, `powershell`, `python`, `r`, `ruby`, `rust`, `scala`, `scss`, `shell`, `sql`, `swift`, `typescript`, `vbnet`, `vbscript`, `verilog`, `vhdl`, `xml`, `yaml`, and `plaintext`.

#### Request

The following example shows a request.

Note

- Highlighted code isn't supported when sending chat messages with code blocks

- [HTTP](#tabpanel_14_http)
- [C#](#tabpanel_14_csharp)
- [Go](#tabpanel_14_go)
- [Java](#tabpanel_14_java)
- [JavaScript](#tabpanel_14_javascript)
- [PHP](#tabpanel_14_php)
- [PowerShell](#tabpanel_14_powershell)
- [Python](#tabpanel_14_python)

```http
POST https://graph.microsoft.com/v1.0/chats/19:7fb82b685f9c457296a0ab6a1d98b4c1@thread.v2/messages
Content-type: application/json

{
  "body": {
    "contentType": "html",
    "content": "<codeblock class=\"plaintext\"><code>Hello world</code></codeblock>"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ChatMessage
{
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "<codeblock class=\"plaintext\"><code>Hello world</code></codeblock>",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Chats["{chat-id}"].Messages.PostAsync(requestBody);
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
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "<codeblock class=\"plaintext\"><code>Hello world</code></codeblock>"
body.SetContent(&content) 
requestBody.SetBody(body)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Chats().ByChatId("chat-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("<codeblock class=\"plaintext\"><code>Hello world</code></codeblock>");
chatMessage.setBody(body);
ChatMessage result = graphClient.chats().byChatId("{chat-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
  body: {
    contentType: 'html',
    content: '<codeblock class=\"plaintext\"><code>Hello world</code></codeblock>'
  }
};

await client.api('/chats/19:7fb82b685f9c457296a0ab6a1d98b4c1@thread.v2/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('<codeblock class=\"plaintext\"><code>Hello world</code></codeblock>');
$requestBody->setBody($body);

$result = $graphServiceClient->chats()->byChatId('chat-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	body = @{
		contentType = "html"
		content = "<codeblock class="plaintext"><code>Hello world</code></codeblock>"
	}
}

New-MgChatMessage -ChatId $chatId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	body = ItemBody(
		content_type = BodyType.Html,
		content = "<codeblock class=\"plaintext\"><code>Hello world</code></codeblock>",
	),
)

result = await graph_client.chats.by_chat_id('chat-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#chatMessage/$entity",
  "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET chats('<key>')/messages('<key>')?$select=attachments,body",
  "id": "1741124357685",
  "replyToId": null,
  "etag": "1741124357685",
  "messageType": "message",
  "createdDateTime": "2025-03-04T21:39:17.685Z",
  "lastModifiedDateTime": "2025-03-04T21:39:17.685Z",
  "lastEditedDateTime": null,
  "deletedDateTime": null,
  "subject": null,
  "summary": null,
  "chatId": "19:e2ed97baac8e4bffbb91299a38996790@thread.v2",
  "importance": "normal",
  "locale": "en-us",
  "webUrl": null,
  "channelIdentity": null,
  "onBehalfOf": null,
  "policyViolation": null,
  "eventDetail": null,
  "from": {
    "application": null,
    "device": null,
    "user": {
      "@odata.type": "#microsoft.graph.teamworkUserIdentity",
      "id": "28c10244-4bad-4fda-993c-f332faef94f0",
      "displayName": "Adele Vance",
      "userIdentityType": "aadUser",
      "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34"
    }
  },
  "body": {
    "contentType": "html",
    "content": "\n<codeblock class=\"plaintext\"><code>Hello world</code></codeblock>"
  },
  "attachments": [],
  "mentions": [],
  "reactions": []
}
```

### Example 15: Import a message into a chat

The following example shows how to import a message into a chat on behalf of a user during a migration session. The target chat must be in migration mode. For more information, see [Import messages into Microsoft Teams chats and channels using Microsoft Graph](https://learn.microsoft.com/en-us/graph/teams-import-messages).

Note

The permission scope `Teamwork.Migrate.All` is required for this scenario.

Important

The **createdDateTime** must be unique down to the millisecond within the target chat. If a message with the same **createdDateTime** exists, the request fails with `409 Conflict`. Adjust the **createdDateTime** and retry.

#### Request

The following example shows a request. The **createdDateTime** and **from** properties are used to attribute the message to a specific user at a specific time in the past.

- [HTTP](#tabpanel_15_http)
- [C#](#tabpanel_15_csharp)
- [Go](#tabpanel_15_go)
- [Java](#tabpanel_15_java)
- [JavaScript](#tabpanel_15_javascript)
- [PHP](#tabpanel_15_php)
- [PowerShell](#tabpanel_15_powershell)
- [Python](#tabpanel_15_python)

```http
POST https://graph.microsoft.com/v1.0/chats/19:4b6bed8d24574f6a9e436813cb2617d8@thread.tacv2/messages

{
   "createdDateTime": "2019-02-04T19:58:15.511Z",
   "from": {
      "user": {
         "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
         "displayName": "Robin Kline",
         "userIdentityType": "aadUser"
      }
   },
   "body": {
      "contentType": "html",
      "content": "Hello World"
   }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ChatMessage
{
	CreatedDateTime = DateTimeOffset.Parse("2019-02-04T19:58:15.511Z"),
	From = new ChatMessageFromIdentitySet
	{
		User = new Identity
		{
			Id = "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
			DisplayName = "Robin Kline",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"userIdentityType" , "aadUser"
				},
			},
		},
	},
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "Hello World",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Chats["{chat-id}"].Messages.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewChatMessage()
createdDateTime , err := time.Parse(time.RFC3339, "2019-02-04T19:58:15.511Z")
requestBody.SetCreatedDateTime(&createdDateTime) 
from := graphmodels.NewChatMessageFromIdentitySet()
user := graphmodels.NewIdentity()
id := "8ea0e38b-efb3-4757-924a-5f94061cf8c2"
user.SetId(&id) 
displayName := "Robin Kline"
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
from.SetUser(user)
requestBody.SetFrom(from)
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "Hello World"
body.SetContent(&content) 
requestBody.SetBody(body)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Chats().ByChatId("chat-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
OffsetDateTime createdDateTime = OffsetDateTime.parse("2019-02-04T19:58:15.511Z");
chatMessage.setCreatedDateTime(createdDateTime);
ChatMessageFromIdentitySet from = new ChatMessageFromIdentitySet();
Identity user = new Identity();
user.setId("8ea0e38b-efb3-4757-924a-5f94061cf8c2");
user.setDisplayName("Robin Kline");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("userIdentityType", "aadUser");
user.setAdditionalData(additionalData);
from.setUser(user);
chatMessage.setFrom(from);
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("Hello World");
chatMessage.setBody(body);
ChatMessage result = graphClient.chats().byChatId("{chat-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
   createdDateTime: '2019-02-04T19:58:15.511Z',
   from: {
      user: {
         id: '8ea0e38b-efb3-4757-924a-5f94061cf8c2',
         displayName: 'Robin Kline',
         userIdentityType: 'aadUser'
      }
   },
   body: {
      contentType: 'html',
      content: 'Hello World'
   }
};

await client.api('/chats/19:4b6bed8d24574f6a9e436813cb2617d8@thread.tacv2/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ChatMessageFromIdentitySet;
use Microsoft\Graph\Generated\Models\Identity;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$requestBody->setCreatedDateTime(new \DateTime('2019-02-04T19:58:15.511Z'));
$from = new ChatMessageFromIdentitySet();
$fromUser = new Identity();
$fromUser->setId('8ea0e38b-efb3-4757-924a-5f94061cf8c2');
$fromUser->setDisplayName('Robin Kline');
$additionalData = [
	'userIdentityType' => 'aadUser',
];
$fromUser->setAdditionalData($additionalData);
$from->setUser($fromUser);
$requestBody->setFrom($from);
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('Hello World');
$requestBody->setBody($body);

$result = $graphServiceClient->chats()->byChatId('chat-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	createdDateTime = [System.DateTime]::Parse("2019-02-04T19:58:15.511Z")
	from = @{
		user = @{
			id = "8ea0e38b-efb3-4757-924a-5f94061cf8c2"
			displayName = "Robin Kline"
			userIdentityType = "aadUser"
		}
	}
	body = @{
		contentType = "html"
		content = "Hello World"
	}
}

New-MgChatMessage -ChatId $chatId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.chat_message_from_identity_set import ChatMessageFromIdentitySet
from msgraph.generated.models.identity import Identity
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	created_date_time = "2019-02-04T19:58:15.511Z",
	from = ChatMessageFromIdentitySet(
		user = Identity(
			id = "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
			display_name = "Robin Kline",
			additional_data = {
					"user_identity_type" : "aadUser",
			}
		),
	),
	body = ItemBody(
		content_type = BodyType.Html,
		content = "Hello World",
	),
)

result = await graph_client.chats.by_chat_id('chat-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#chats('19%3A4b6bed8d24574f6a9e436813cb2617d8%40thread.tacv2')/messages/$entity",
    "id": "1616991463150",
    "replyToId": null,
    "etag": "1616991463150",
    "messageType": "message",
    "createdDateTime": "2019-02-04T19:58:15.511Z",
    "lastModifiedDateTime": null,
    "deletedDateTime": null,
    "subject": null,
    "summary": null,
    "chatId": "19:4b6bed8d24574f6a9e436813cb2617d8@thread.tacv2",
    "importance": "normal",
    "locale": "en-us",
    "webUrl": null,
    "channelIdentity": null,
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "conversation": null,
        "user": {
            "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
            "displayName": "Robin Kline",
            "userIdentityType": "aadUser"
        }
    },
    "body": {
        "contentType": "html",
        "content": "Hello World"
    },
    "attachments": [],
    "mentions": [],
    "reactions": []
}
```

### Example 16: Import a message into a channel

The following example shows how to import a message into a channel on behalf of a user during a migration session. The target channel must be in migration mode. For more information, see [Import messages into Microsoft Teams chats and channels using Microsoft Graph](https://learn.microsoft.com/en-us/graph/teams-import-messages).

Note

The permission scope `Teamwork.Migrate.All` is required for this scenario.

Important

The **createdDateTime** must be unique down to the millisecond within the target channel. If a message with the same **createdDateTime** exists, the request fails with `409 Conflict`. Adjust the **createdDateTime** and retry.

#### Request

The following example shows a request. The **createdDateTime** and **from** properties are used to attribute the message to a specific user at a specific time in the past.

- [HTTP](#tabpanel_16_http)
- [C#](#tabpanel_16_csharp)
- [Go](#tabpanel_16_go)
- [Java](#tabpanel_16_java)
- [JavaScript](#tabpanel_16_javascript)
- [PHP](#tabpanel_16_php)
- [PowerShell](#tabpanel_16_powershell)
- [Python](#tabpanel_16_python)

```http
POST https://graph.microsoft.com/v1.0/teams/57fb72d0-d811-46f4-8947-305e6072eaa5/channels/19:4b6bed8d24574f6a9e436813cb2617d8@thread.tacv2/messages

{
   "createdDateTime": "2019-02-04T19:58:15.511Z",
   "from": {
      "user": {
         "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
         "displayName": "Robin Kline",
         "userIdentityType": "aadUser"
      }
   },
   "body": {
      "contentType": "html",
      "content": "Hello World"
   }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ChatMessage
{
	CreatedDateTime = DateTimeOffset.Parse("2019-02-04T19:58:15.511Z"),
	From = new ChatMessageFromIdentitySet
	{
		User = new Identity
		{
			Id = "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
			DisplayName = "Robin Kline",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"userIdentityType" , "aadUser"
				},
			},
		},
	},
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "Hello World",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewChatMessage()
createdDateTime , err := time.Parse(time.RFC3339, "2019-02-04T19:58:15.511Z")
requestBody.SetCreatedDateTime(&createdDateTime) 
from := graphmodels.NewChatMessageFromIdentitySet()
user := graphmodels.NewIdentity()
id := "8ea0e38b-efb3-4757-924a-5f94061cf8c2"
user.SetId(&id) 
displayName := "Robin Kline"
user.SetDisplayName(&displayName) 
additionalData := map[string]interface{}{
	"userIdentityType" : "aadUser", 
}
user.SetAdditionalData(additionalData)
from.SetUser(user)
requestBody.SetFrom(from)
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "Hello World"
body.SetContent(&content) 
requestBody.SetBody(body)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ChatMessage chatMessage = new ChatMessage();
OffsetDateTime createdDateTime = OffsetDateTime.parse("2019-02-04T19:58:15.511Z");
chatMessage.setCreatedDateTime(createdDateTime);
ChatMessageFromIdentitySet from = new ChatMessageFromIdentitySet();
Identity user = new Identity();
user.setId("8ea0e38b-efb3-4757-924a-5f94061cf8c2");
user.setDisplayName("Robin Kline");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("userIdentityType", "aadUser");
user.setAdditionalData(additionalData);
from.setUser(user);
chatMessage.setFrom(from);
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("Hello World");
chatMessage.setBody(body);
ChatMessage result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
   createdDateTime: '2019-02-04T19:58:15.511Z',
   from: {
      user: {
         id: '8ea0e38b-efb3-4757-924a-5f94061cf8c2',
         displayName: 'Robin Kline',
         userIdentityType: 'aadUser'
      }
   },
   body: {
      contentType: 'html',
      content: 'Hello World'
   }
};

await client.api('/teams/57fb72d0-d811-46f4-8947-305e6072eaa5/channels/19:4b6bed8d24574f6a9e436813cb2617d8@thread.tacv2/messages')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ChatMessageFromIdentitySet;
use Microsoft\Graph\Generated\Models\Identity;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ChatMessage();
$requestBody->setCreatedDateTime(new \DateTime('2019-02-04T19:58:15.511Z'));
$from = new ChatMessageFromIdentitySet();
$fromUser = new Identity();
$fromUser->setId('8ea0e38b-efb3-4757-924a-5f94061cf8c2');
$fromUser->setDisplayName('Robin Kline');
$additionalData = [
	'userIdentityType' => 'aadUser',
];
$fromUser->setAdditionalData($additionalData);
$from->setUser($fromUser);
$requestBody->setFrom($from);
$body = new ItemBody();
$body->setContentType(new BodyType('html'));
$body->setContent('Hello World');
$requestBody->setBody($body);

$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	createdDateTime = [System.DateTime]::Parse("2019-02-04T19:58:15.511Z")
	from = @{
		user = @{
			id = "8ea0e38b-efb3-4757-924a-5f94061cf8c2"
			displayName = "Robin Kline"
			userIdentityType = "aadUser"
		}
	}
	body = @{
		contentType = "html"
		content = "Hello World"
	}
}

New-MgTeamChannelMessage -TeamId $teamId -ChannelId $channelId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.chat_message_from_identity_set import ChatMessageFromIdentitySet
from msgraph.generated.models.identity import Identity
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ChatMessage(
	created_date_time = "2019-02-04T19:58:15.511Z",
	from = ChatMessageFromIdentitySet(
		user = Identity(
			id = "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
			display_name = "Robin Kline",
			additional_data = {
					"user_identity_type" : "aadUser",
			}
		),
	),
	body = ItemBody(
		content_type = BodyType.Html,
		content = "Hello World",
	),
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('57fb72d0-d811-46f4-8947-305e6072eaa5')/channels('19%3A4b6bed8d24574f6a9e436813cb2617d8%40thread.tacv2')/messages/$entity",
    "id": "1616991463150",
    "replyToId": null,
    "etag": "1616991463150",
    "messageType": "message",
    "createdDateTime": "2019-02-04T19:58:15.511Z",
    "lastModifiedDateTime": null,
    "deletedDateTime": null,
    "subject": null,
    "summary": null,
    "chatId": null,
    "importance": "normal",
    "locale": "en-us",
    "webUrl": null,
    "policyViolation": null,
    "eventDetail": null,
    "from": {
        "application": null,
        "device": null,
        "conversation": null,
        "user": {
            "id": "8ea0e38b-efb3-4757-924a-5f94061cf8c2",
            "displayName": "Robin Kline",
            "userIdentityType": "aadUser"
        }
    },
    "body": {
        "contentType": "html",
        "content": "Hello World"
    },
    "channelIdentity": {
        "teamId": "57fb72d0-d811-46f4-8947-305e6072eaa5",
        "channelId": "19:4b6bed8d24574f6a9e436813cb2617d8@thread.tacv2"
    },
    "attachments": [],
    "mentions": [],
    "reactions": []
}
```

## Related content

[Cards reference](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/cards/cards-reference)
