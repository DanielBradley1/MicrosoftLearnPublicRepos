<!-- Source: https://learn.microsoft.com/en-us/graph/api/chatmessage-replywithquote?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# chatMessage: replyWithQuote

Namespace: microsoft.graph

Reply with quote to a single [chat message](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) or multiple chat messages in a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0).

Note

When replying with a quote to multiple messages, a maximum of 10 messages can be used for the reply.

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

```http
POST /chats/{chatId}/messages/replyWithQuote
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
| messageIds | String collection | List of message IDs in a chat that are replied to with a quote. |
| replyMessage | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | The message body for the reply. |

## Response

If successful, this method returns a `201 Created` response code and a new [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/chats/19:97641583cf154265a237da28ebbde27a@thread.v2/messages/replyWithQuote
Content-Type: application/json

{
  "messageIds": [
    "1728088338580"
  ],
  "replyMessage": {
    "body": {
      "content": "Hello World"
    }
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Chats.Item.Messages.ReplyWithQuote;
using Microsoft.Graph.Models;

var requestBody = new ReplyWithQuotePostRequestBody
{
	MessageIds = new List<string>
	{
		"1728088338580",
	},
	ReplyMessage = new ChatMessage
	{
		Body = new ItemBody
		{
			Content = "Hello World",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Chats["{chat-id}"].Messages.ReplyWithQuote.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphchats "github.com/microsoftgraph/msgraph-sdk-go/chats"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphchats.NewReplyWithQuotePostRequestBody()
messageIds := []string {
	"1728088338580",
}
requestBody.SetMessageIds(messageIds)
replyMessage := graphmodels.NewChatMessage()
body := graphmodels.NewItemBody()
content := "Hello World"
body.SetContent(&content) 
replyMessage.SetBody(body)
requestBody.SetReplyMessage(replyMessage)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
replyWithQuote, err := graphClient.Chats().ByChatId("chat-id").Messages().ReplyWithQuote().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.chats.item.messages.replywithquote.ReplyWithQuotePostRequestBody replyWithQuotePostRequestBody = new com.microsoft.graph.chats.item.messages.replywithquote.ReplyWithQuotePostRequestBody();
LinkedList<String> messageIds = new LinkedList<String>();
messageIds.add("1728088338580");
replyWithQuotePostRequestBody.setMessageIds(messageIds);
ChatMessage replyMessage = new ChatMessage();
ItemBody body = new ItemBody();
body.setContent("Hello World");
replyMessage.setBody(body);
replyWithQuotePostRequestBody.setReplyMessage(replyMessage);
var result = graphClient.chats().byChatId("{chat-id}").messages().replyWithQuote().post(replyWithQuotePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const chatMessage = {
  messageIds: [
    '1728088338580'
  ],
  replyMessage: {
    body: {
      content: 'Hello World'
    }
  }
};

await client.api('/chats/19:97641583cf154265a237da28ebbde27a@thread.v2/messages/replyWithQuote')
	.post(chatMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Chats\Item\Messages\ReplyWithQuote\ReplyWithQuotePostRequestBody;
use Microsoft\Graph\Generated\Models\ChatMessage;
use Microsoft\Graph\Generated\Models\ItemBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ReplyWithQuotePostRequestBody();
$requestBody->setMessageIds(['1728088338580', 	]);
$replyMessage = new ChatMessage();
$replyMessageBody = new ItemBody();
$replyMessageBody->setContent('Hello World');
$replyMessage->setBody($replyMessageBody);
$requestBody->setReplyMessage($replyMessage);

$result = $graphServiceClient->chats()->byChatId('chat-id')->messages()->replyWithQuote()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	messageIds = @(
	"1728088338580"
)
replyMessage = @{
	body = @{
		content = "Hello World"
	}
}
}

Invoke-MgGraphChatMessage -ChatId $chatId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.chats.item.messages.reply_with_quote.reply_with_quote_post_request_body import ReplyWithQuotePostRequestBody
from msgraph.generated.models.chat_message import ChatMessage
from msgraph.generated.models.item_body import ItemBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ReplyWithQuotePostRequestBody(
	message_ids = [
		"1728088338580",
	],
	reply_message = ChatMessage(
		body = ItemBody(
			content = "Hello World",
		),
	),
)

result = await graph_client.chats.by_chat_id('chat-id').messages.reply_with_quote.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#chats('19%3A97641583cf154265a237da28ebbde27a%40thread.v2')/messages/$entity",
  "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET chats('<key>')/messages('<key>')?$select=attachments,body",
  "id": "1729091934196",
  "replyToId": null,
  "etag": "1729091934196",
  "messageType": "message",
  "createdDateTime": "2024-10-16T15:18:54.196Z",
  "lastModifiedDateTime": "2024-10-16T15:18:54.196Z",
  "lastEditedDateTime": null,
  "deletedDateTime": null,
  "subject": null,
  "summary": null,
  "chatId": "19:97641583cf154265a237da28ebbde27a@thread.v2",
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
      "id": "28c10244-4bad-4fda-993c-f332faef94f0",
      "displayName": "Adele Vance",
      "userIdentityType": "aadUser",
      "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34"
    }
  },
  "body": {
    "contentType": "html",
    "content": "<p></p>\n<attachment id=\"1728422677844\"></attachment>\ntest reply\n<p></p>"
  },
  "attachments": [
    {
      "id": "1728422677844",
      "contentType": "messageReference",
      "contentUrl": null,
      "content": "{\"messageId\":\"1728422677844\",\"messagePreview\":\"Hello World Jane Smith\",\"messageSender\":{\"application\":null,\"device\":null,\"user\":{\"userIdentityType\":\"aadUser\",\"tenantId\":\"2432b57b-0abd-43db-aa7b-16eadd115d34\",\"id\":\"28c10244-4bad-4fda-993c-f332faef94f0\",\"displayName\":\"Adele Vance\"}}}",
      "name": null,
      "thumbnailUrl": null,
      "teamsAppId": null
    }
  ],
  "mentions": [],
  "reactions": []
}
```
