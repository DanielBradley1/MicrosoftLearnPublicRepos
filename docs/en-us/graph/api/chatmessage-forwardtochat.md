<!-- Source: https://learn.microsoft.com/en-us/graph/api/chatmessage-forwardtochat?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-03-20 -->

# chatMessage: forwardToChat

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Forward a [chat message](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-beta), a [channel message](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-beta), or a [channel message reply](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-beta) to a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ChatMessage.Send | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

Forward a **chatMessage** in a **chat** to a **chat**:

```http
POST /chats/{chatId}/messages/forwardToChat
```

Forward a **chatMessage** in a **channel** to a **chat**:

```http
POST /teams/{teamId}/channels/{channelId}/messages/forwardToChat
POST /teams/{teamId}/channels/{channelId}/messages/{messageId}/replies/forwardToChat
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| additionalMessage | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-beta) | Message body of the forwarded message. |
| messageIds | String collection | List of message IDs in a chat or channel that are being forwarded. Currently, only one message ID is supported. |
| targetChatIds | String collection | List of target chat IDs where a message can be forwarded. Currently, only one target chat ID is supported. |

## Response

If successful, this method returns a `200 OK` response code and a collection of [forwardToChatResult](https://learn.microsoft.com/en-us/graph/api/resources/forwardtochatresult?view=graph-rest-beta) objects in the response body.

Note

Because only a single target chat ID is supported in the request payload, the response contains only one value.

## Examples

### Example 1: Forward a message from a chat to a chat

The following example shows how to forward a message from a chat to a chat.

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
POST https://graph.microsoft.com/beta/chats/19:97641583cf154265a237da28ebbde27a@thread.v2/messages/forwardToChat
Content-Type: application/json

{
  "targetChatIds": [
    "19:e2ed97baac8e4bffbb91299a38996790@thread.v2"
  ],
  "messageIds": [
    "1728088338580"
  ],
  "additionalMessage": {
    "body": {
      "content": "Hello World"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Chats.Item.Messages.ForwardToChat;
using Microsoft.Graph.Beta.Models;

var requestBody = new ForwardToChatPostRequestBody
{
	TargetChatIds = new List<string>
	{
		"19:e2ed97baac8e4bffbb91299a38996790@thread.v2",
	},
	MessageIds = new List<string>
	{
		"1728088338580",
	},
	AdditionalMessage = new ChatMessage
	{
		Body = new ChatMessageBody
		{
			Content = "Hello World",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Chats["{chat-id}"].Messages.ForwardToChat.PostAsForwardToChatPostResponseAsync(requestBody);
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
	  graphchats "github.com/microsoftgraph/msgraph-beta-sdk-go/chats"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphchats.NewForwardToChatPostRequestBody()
targetChatIds := []string {
	"19:e2ed97baac8e4bffbb91299a38996790@thread.v2",
}
requestBody.SetTargetChatIds(targetChatIds)
messageIds := []string {
	"1728088338580",
}
requestBody.SetMessageIds(messageIds)
additionalMessage := graphmodels.NewChatMessage()
body := graphmodels.NewChatMessageBody()
content := "Hello World"
body.SetContent(&content) 
additionalMessage.SetBody(body)
requestBody.SetAdditionalMessage(additionalMessage)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
forwardToChat, err := graphClient.Chats().ByChatId("chat-id").Messages().ForwardToChat().PostAsForwardToChatPostResponse(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.chats.item.messages.forwardtochat.ForwardToChatPostRequestBody forwardToChatPostRequestBody = new com.microsoft.graph.beta.chats.item.messages.forwardtochat.ForwardToChatPostRequestBody();
LinkedList<String> targetChatIds = new LinkedList<String>();
targetChatIds.add("19:e2ed97baac8e4bffbb91299a38996790@thread.v2");
forwardToChatPostRequestBody.setTargetChatIds(targetChatIds);
LinkedList<String> messageIds = new LinkedList<String>();
messageIds.add("1728088338580");
forwardToChatPostRequestBody.setMessageIds(messageIds);
ChatMessage additionalMessage = new ChatMessage();
ChatMessageBody body = new ChatMessageBody();
body.setContent("Hello World");
additionalMessage.setBody(body);
forwardToChatPostRequestBody.setAdditionalMessage(additionalMessage);
var result = graphClient.chats().byChatId("{chat-id}").messages().forwardToChat().post(forwardToChatPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const actionResultPart = {
  targetChatIds: [
    '19:e2ed97baac8e4bffbb91299a38996790@thread.v2'
  ],
  messageIds: [
    '1728088338580'
  ],
  additionalMessage: {
    body: {
      content: 'Hello World'
    }
  }
};

await client.api('/chats/19:97641583cf154265a237da28ebbde27a@thread.v2/messages/forwardToChat')
	.version('beta')
	.post(actionResultPart);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Chats\Item\Messages\ForwardToChat\ForwardToChatPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\ChatMessage;
use Microsoft\Graph\Beta\Generated\Models\ChatMessageBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ForwardToChatPostRequestBody();
$requestBody->setTargetChatIds(['19:e2ed97baac8e4bffbb91299a38996790@thread.v2', 	]);
$requestBody->setMessageIds(['1728088338580', 	]);
$additionalMessage = new ChatMessage();
$additionalMessageBody = new ChatMessageBody();
$additionalMessageBody->setContent('Hello World');
$additionalMessage->setBody($additionalMessageBody);
$requestBody->setAdditionalMessage($additionalMessage);

$result = $graphServiceClient->chats()->byChatId('chat-id')->messages()->forwardToChat()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	targetChatIds = @(
	"19:e2ed97baac8e4bffbb91299a38996790@thread.v2"
)
messageIds = @(
"1728088338580"
)
additionalMessage = @{
body = @{
	content = "Hello World"
}
}
}

Invoke-MgBetaForwardChatMessageToChat -ChatId $chatId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.chats.item.messages.forward_to_chat.forward_to_chat_post_request_body import ForwardToChatPostRequestBody
from msgraph_beta.generated.models.chat_message import ChatMessage
from msgraph_beta.generated.models.chat_message_body import ChatMessageBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ForwardToChatPostRequestBody(
	target_chat_ids = [
		"19:e2ed97baac8e4bffbb91299a38996790@thread.v2",
	],
	message_ids = [
		"1728088338580",
	],
	additional_message = ChatMessage(
		body = ChatMessageBody(
			content = "Hello World",
		),
	),
)

result = await graph_client.chats.by_chat_id('chat-id').messages.forward_to_chat.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.forwardToChatResult)",
  "value": [
    {
      "@odata.type": "#microsoft.graph.forwardToChatResult",
      "targetChatId": "19:e2ed97baac8e4bffbb91299a38996790@thread.v2",
      "forwardedMessageId": "1730918320559",
      "error": null
    }
  ]
}
```

### Example 2: Forward a message from a channel to a chat

The following example shows how to forward a message from a channel to a chat.

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
POST https://graph.microsoft.com/beta/teams/1e769eab-06a8-4b2e-ac42-1f040a4e52a1/channels/19:b6343216390d46cba965fe36bd877674@thread.tacv2/messages/forwardToChat
Content-Type: application/json

{
  "targetChatIds": [
    "19:e2ed97baac8e4bffbb91299a38996790@thread.v2"
  ],
  "messageIds": [
    "1728088338580"
  ],
  "additionalMessage": {
    "body": {
      "content": "Hello World"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Teams.Item.Channels.Item.Messages.ForwardToChat;
using Microsoft.Graph.Beta.Models;

var requestBody = new ForwardToChatPostRequestBody
{
	TargetChatIds = new List<string>
	{
		"19:e2ed97baac8e4bffbb91299a38996790@thread.v2",
	},
	MessageIds = new List<string>
	{
		"1728088338580",
	},
	AdditionalMessage = new ChatMessage
	{
		Body = new ChatMessageBody
		{
			Content = "Hello World",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages.ForwardToChat.PostAsForwardToChatPostResponseAsync(requestBody);
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
	  graphteams "github.com/microsoftgraph/msgraph-beta-sdk-go/teams"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphteams.NewForwardToChatPostRequestBody()
targetChatIds := []string {
	"19:e2ed97baac8e4bffbb91299a38996790@thread.v2",
}
requestBody.SetTargetChatIds(targetChatIds)
messageIds := []string {
	"1728088338580",
}
requestBody.SetMessageIds(messageIds)
additionalMessage := graphmodels.NewChatMessage()
body := graphmodels.NewChatMessageBody()
content := "Hello World"
body.SetContent(&content) 
additionalMessage.SetBody(body)
requestBody.SetAdditionalMessage(additionalMessage)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
forwardToChat, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().ForwardToChat().PostAsForwardToChatPostResponse(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.teams.item.channels.item.messages.forwardtochat.ForwardToChatPostRequestBody forwardToChatPostRequestBody = new com.microsoft.graph.beta.teams.item.channels.item.messages.forwardtochat.ForwardToChatPostRequestBody();
LinkedList<String> targetChatIds = new LinkedList<String>();
targetChatIds.add("19:e2ed97baac8e4bffbb91299a38996790@thread.v2");
forwardToChatPostRequestBody.setTargetChatIds(targetChatIds);
LinkedList<String> messageIds = new LinkedList<String>();
messageIds.add("1728088338580");
forwardToChatPostRequestBody.setMessageIds(messageIds);
ChatMessage additionalMessage = new ChatMessage();
ChatMessageBody body = new ChatMessageBody();
body.setContent("Hello World");
additionalMessage.setBody(body);
forwardToChatPostRequestBody.setAdditionalMessage(additionalMessage);
var result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().forwardToChat().post(forwardToChatPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const actionResultPart = {
  targetChatIds: [
    '19:e2ed97baac8e4bffbb91299a38996790@thread.v2'
  ],
  messageIds: [
    '1728088338580'
  ],
  additionalMessage: {
    body: {
      content: 'Hello World'
    }
  }
};

await client.api('/teams/1e769eab-06a8-4b2e-ac42-1f040a4e52a1/channels/19:b6343216390d46cba965fe36bd877674@thread.tacv2/messages/forwardToChat')
	.version('beta')
	.post(actionResultPart);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Teams\Item\Channels\Item\Messages\ForwardToChat\ForwardToChatPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\ChatMessage;
use Microsoft\Graph\Beta\Generated\Models\ChatMessageBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ForwardToChatPostRequestBody();
$requestBody->setTargetChatIds(['19:e2ed97baac8e4bffbb91299a38996790@thread.v2', 	]);
$requestBody->setMessageIds(['1728088338580', 	]);
$additionalMessage = new ChatMessage();
$additionalMessageBody = new ChatMessageBody();
$additionalMessageBody->setContent('Hello World');
$additionalMessage->setBody($additionalMessageBody);
$requestBody->setAdditionalMessage($additionalMessage);

$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->forwardToChat()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	targetChatIds = @(
	"19:e2ed97baac8e4bffbb91299a38996790@thread.v2"
)
messageIds = @(
"1728088338580"
)
additionalMessage = @{
body = @{
	content = "Hello World"
}
}
}

Invoke-MgBetaForwardTeamChannelMessageToChat -TeamId $teamId -ChannelId $channelId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.teams.item.channels.item.messages.forward_to_chat.forward_to_chat_post_request_body import ForwardToChatPostRequestBody
from msgraph_beta.generated.models.chat_message import ChatMessage
from msgraph_beta.generated.models.chat_message_body import ChatMessageBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ForwardToChatPostRequestBody(
	target_chat_ids = [
		"19:e2ed97baac8e4bffbb91299a38996790@thread.v2",
	],
	message_ids = [
		"1728088338580",
	],
	additional_message = ChatMessage(
		body = ChatMessageBody(
			content = "Hello World",
		),
	),
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.forward_to_chat.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.forwardToChatResult)",
  "value": [
    {
      "@odata.type": "#microsoft.graph.forwardToChatResult",
      "targetChatId": "19:e2ed97baac8e4bffbb91299a38996790@thread.v2",
      "forwardedMessageId": "1730918320559",
      "error": null
    }
  ]
}
```

### Example 3: Forward a reply message from a channel to a chat

The following example shows how to forward a reply message from a channel to a chat.

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

```http
POST https://graph.microsoft.com/beta/teams/1e769eab-06a8-4b2e-ac42-1f040a4e52a1/channels/19:b6343216390d46cba965fe36bd877674@thread.tacv2/messages/1727810802267/replies/forwardToChat
Content-Type: application/json

{
  "targetChatIds": [
    "19:e2ed97baac8e4bffbb91299a38996790@thread.v2"
  ],
  "messageIds": [
    "1728088338580"
  ],
  "additionalMessage": {
    "body": {
      "content": "Hello World"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Teams.Item.Channels.Item.Messages.Item.Replies.ForwardToChat;
using Microsoft.Graph.Beta.Models;

var requestBody = new ForwardToChatPostRequestBody
{
	TargetChatIds = new List<string>
	{
		"19:e2ed97baac8e4bffbb91299a38996790@thread.v2",
	},
	MessageIds = new List<string>
	{
		"1728088338580",
	},
	AdditionalMessage = new ChatMessage
	{
		Body = new ChatMessageBody
		{
			Content = "Hello World",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels["{channel-id}"].Messages["{chatMessage-id}"].Replies.ForwardToChat.PostAsForwardToChatPostResponseAsync(requestBody);
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
	  graphteams "github.com/microsoftgraph/msgraph-beta-sdk-go/teams"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphteams.NewForwardToChatPostRequestBody()
targetChatIds := []string {
	"19:e2ed97baac8e4bffbb91299a38996790@thread.v2",
}
requestBody.SetTargetChatIds(targetChatIds)
messageIds := []string {
	"1728088338580",
}
requestBody.SetMessageIds(messageIds)
additionalMessage := graphmodels.NewChatMessage()
body := graphmodels.NewChatMessageBody()
content := "Hello World"
body.SetContent(&content) 
additionalMessage.SetBody(body)
requestBody.SetAdditionalMessage(additionalMessage)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
forwardToChat, err := graphClient.Teams().ByTeamId("team-id").Channels().ByChannelId("channel-id").Messages().ByChatMessageId("chatMessage-id").Replies().ForwardToChat().PostAsForwardToChatPostResponse(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.teams.item.channels.item.messages.item.replies.forwardtochat.ForwardToChatPostRequestBody forwardToChatPostRequestBody = new com.microsoft.graph.beta.teams.item.channels.item.messages.item.replies.forwardtochat.ForwardToChatPostRequestBody();
LinkedList<String> targetChatIds = new LinkedList<String>();
targetChatIds.add("19:e2ed97baac8e4bffbb91299a38996790@thread.v2");
forwardToChatPostRequestBody.setTargetChatIds(targetChatIds);
LinkedList<String> messageIds = new LinkedList<String>();
messageIds.add("1728088338580");
forwardToChatPostRequestBody.setMessageIds(messageIds);
ChatMessage additionalMessage = new ChatMessage();
ChatMessageBody body = new ChatMessageBody();
body.setContent("Hello World");
additionalMessage.setBody(body);
forwardToChatPostRequestBody.setAdditionalMessage(additionalMessage);
var result = graphClient.teams().byTeamId("{team-id}").channels().byChannelId("{channel-id}").messages().byChatMessageId("{chatMessage-id}").replies().forwardToChat().post(forwardToChatPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const actionResultPart = {
  targetChatIds: [
    '19:e2ed97baac8e4bffbb91299a38996790@thread.v2'
  ],
  messageIds: [
    '1728088338580'
  ],
  additionalMessage: {
    body: {
      content: 'Hello World'
    }
  }
};

await client.api('/teams/1e769eab-06a8-4b2e-ac42-1f040a4e52a1/channels/19:b6343216390d46cba965fe36bd877674@thread.tacv2/messages/1727810802267/replies/forwardToChat')
	.version('beta')
	.post(actionResultPart);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Teams\Item\Channels\Item\Messages\Item\Replies\ForwardToChat\ForwardToChatPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\ChatMessage;
use Microsoft\Graph\Beta\Generated\Models\ChatMessageBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ForwardToChatPostRequestBody();
$requestBody->setTargetChatIds(['19:e2ed97baac8e4bffbb91299a38996790@thread.v2', 	]);
$requestBody->setMessageIds(['1728088338580', 	]);
$additionalMessage = new ChatMessage();
$additionalMessageBody = new ChatMessageBody();
$additionalMessageBody->setContent('Hello World');
$additionalMessage->setBody($additionalMessageBody);
$requestBody->setAdditionalMessage($additionalMessage);

$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->byChannelId('channel-id')->messages()->byChatMessageId('chatMessage-id')->replies()->forwardToChat()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Teams

$params = @{
	targetChatIds = @(
	"19:e2ed97baac8e4bffbb91299a38996790@thread.v2"
)
messageIds = @(
"1728088338580"
)
additionalMessage = @{
body = @{
	content = "Hello World"
}
}
}

Invoke-MgBetaForwardTeamChannelMessageReplyToChat -TeamId $teamId -ChannelId $channelId -ChatMessageId $chatMessageId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.teams.item.channels.item.messages.item.replies.forward_to_chat.forward_to_chat_post_request_body import ForwardToChatPostRequestBody
from msgraph_beta.generated.models.chat_message import ChatMessage
from msgraph_beta.generated.models.chat_message_body import ChatMessageBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ForwardToChatPostRequestBody(
	target_chat_ids = [
		"19:e2ed97baac8e4bffbb91299a38996790@thread.v2",
	],
	message_ids = [
		"1728088338580",
	],
	additional_message = ChatMessage(
		body = ChatMessageBody(
			content = "Hello World",
		),
	),
)

result = await graph_client.teams.by_team_id('team-id').channels.by_channel_id('channel-id').messages.by_chat_message_id('chatMessage-id').replies.forward_to_chat.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.forwardToChatResult)",
  "value": [
    {
      "@odata.type": "#microsoft.graph.forwardToChatResult",
      "targetChatId": "19:e2ed97baac8e4bffbb91299a38996790@thread.v2",
      "forwardedMessageId": "1730918320559",
      "error": null
    }
  ]
}
```
