<!-- Source: https://learn.microsoft.com/en-us/graph/api/chat-markchatunreadforuser?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# chat: markChatUnreadForUser

Namespace: microsoft.graph

Mark a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) as unread for a user.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Chat.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /chats/{chat-id}/markChatUnreadForUser
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
| lastMessageReadDateTime | DateTimeOffset | Timestamp that indicates the time after which all sent or received messages are to be marked as unread. |
| user | [teamworkUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkuseridentity?view=graph-rest-1.0) | User to unread the chat for. |

> **Note:** **lastMessageReadDateTime** is optional in the request. If not mentioned, the last message would be marked as unread.

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/chats/19:7d898072-792c-4006-bb10-5ca9f2590649_8ea0e38b-efb3-4757-924a-5f94061cf8c2@unq.gbl.spaces/markChatUnreadForUser
Content-Type: application/json
Content-length: 158

{
  "user": {
    "id" : "d864e79f-a516-4d0f-9fee-0eeb4d61fdc2",
    "tenantId": "2a690434-97d9-4eed-83a6-f5f13600199a"
  },
  "lastMessageReadDateTime": "2021-05-27T22:13:01.577Z"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Chats.Item.MarkChatUnreadForUser;
using Microsoft.Graph.Models;

var requestBody = new MarkChatUnreadForUserPostRequestBody
{
	User = new TeamworkUserIdentity
	{
		Id = "d864e79f-a516-4d0f-9fee-0eeb4d61fdc2",
		AdditionalData = new Dictionary<string, object>
		{
			{
				"tenantId" , "2a690434-97d9-4eed-83a6-f5f13600199a"
			},
		},
	},
	LastMessageReadDateTime = DateTimeOffset.Parse("2021-05-27T22:13:01.577Z"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Chats["{chat-id}"].MarkChatUnreadForUser.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphchats "github.com/microsoftgraph/msgraph-sdk-go/chats"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphchats.NewMarkChatUnreadForUserPostRequestBody()
user := graphmodels.NewTeamworkUserIdentity()
id := "d864e79f-a516-4d0f-9fee-0eeb4d61fdc2"
user.SetId(&id) 
additionalData := map[string]interface{}{
	"tenantId" : "2a690434-97d9-4eed-83a6-f5f13600199a", 
}
user.SetAdditionalData(additionalData)
requestBody.SetUser(user)
lastMessageReadDateTime , err := time.Parse(time.RFC3339, "2021-05-27T22:13:01.577Z")
requestBody.SetLastMessageReadDateTime(&lastMessageReadDateTime) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Chats().ByChatId("chat-id").MarkChatUnreadForUser().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.chats.item.markchatunreadforuser.MarkChatUnreadForUserPostRequestBody markChatUnreadForUserPostRequestBody = new com.microsoft.graph.chats.item.markchatunreadforuser.MarkChatUnreadForUserPostRequestBody();
TeamworkUserIdentity user = new TeamworkUserIdentity();
user.setId("d864e79f-a516-4d0f-9fee-0eeb4d61fdc2");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("tenantId", "2a690434-97d9-4eed-83a6-f5f13600199a");
user.setAdditionalData(additionalData);
markChatUnreadForUserPostRequestBody.setUser(user);
OffsetDateTime lastMessageReadDateTime = OffsetDateTime.parse("2021-05-27T22:13:01.577Z");
markChatUnreadForUserPostRequestBody.setLastMessageReadDateTime(lastMessageReadDateTime);
graphClient.chats().byChatId("{chat-id}").markChatUnreadForUser().post(markChatUnreadForUserPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const markChatUnreadForUser = {
  user: {
    id: 'd864e79f-a516-4d0f-9fee-0eeb4d61fdc2',
    tenantId: '2a690434-97d9-4eed-83a6-f5f13600199a'
  },
  lastMessageReadDateTime: '2021-05-27T22:13:01.577Z'
};

await client.api('/chats/19:7d898072-792c-4006-bb10-5ca9f2590649_8ea0e38b-efb3-4757-924a-5f94061cf8c2@unq.gbl.spaces/markChatUnreadForUser')
	.post(markChatUnreadForUser);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Chats\Item\MarkChatUnreadForUser\MarkChatUnreadForUserPostRequestBody;
use Microsoft\Graph\Generated\Models\TeamworkUserIdentity;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MarkChatUnreadForUserPostRequestBody();
$user = new TeamworkUserIdentity();
$user->setId('d864e79f-a516-4d0f-9fee-0eeb4d61fdc2');
$additionalData = [
	'tenantId' => '2a690434-97d9-4eed-83a6-f5f13600199a',
];
$user->setAdditionalData($additionalData);
$requestBody->setUser($user);
$requestBody->setLastMessageReadDateTime(new \DateTime('2021-05-27T22:13:01.577Z'));

$graphServiceClient->chats()->byChatId('chat-id')->markChatUnreadForUser()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	user = @{
		id = "d864e79f-a516-4d0f-9fee-0eeb4d61fdc2"
		tenantId = "2a690434-97d9-4eed-83a6-f5f13600199a"
	}
	lastMessageReadDateTime = [System.DateTime]::Parse("2021-05-27T22:13:01.577Z")
}

Invoke-MgMarkChatUnreadForUser -ChatId $chatId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.chats.item.mark_chat_unread_for_user.mark_chat_unread_for_user_post_request_body import MarkChatUnreadForUserPostRequestBody
from msgraph.generated.models.teamwork_user_identity import TeamworkUserIdentity
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MarkChatUnreadForUserPostRequestBody(
	user = TeamworkUserIdentity(
		id = "d864e79f-a516-4d0f-9fee-0eeb4d61fdc2",
		additional_data = {
				"tenant_id" : "2a690434-97d9-4eed-83a6-f5f13600199a",
		}
	),
	last_message_read_date_time = "2021-05-27T22:13:01.577Z",
)

await graph_client.chats.by_chat_id('chat-id').mark_chat_unread_for_user.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 204 No Content
```
