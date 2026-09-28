<!-- Source: https://learn.microsoft.com/en-us/graph/api/userteamwork-deletetargetedmessage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# userTeamwork: deleteTargetedMessage

Namespace: microsoft.graph

Delete a specific [targeted message](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) from a channel context. Teams administrators can use this API to remove targeted messages by providing the message ID, team ID, and channel ID.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamworkTargetedMessage.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /users/{user-id | userPrincipalName}/teamwork/deleteTargetedMessage
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table lists the parameters that are required when you call this action.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| channelId | String | The unique identifier of the channel where the targeted message was sent. Required. |
| messageId | String | The unique identifier of the targeted message to delete. This ID is unique within the context of the specified channel and user. Required. |
| teamId | String | The unique identifier of the team that contains the channel where the targeted message was sent. Required. |

## Response

If successful, this action returns a `204 No Content` response code.

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
POST https://graph.microsoft.com/v1.0/users/f47b5f54-6968-4706-a522-31e842b12345/teamwork/deleteTargetedMessage
Content-Type: application/json

{
  "teamId": "9dda0ae1-e007-4a1d-81ec-2cf4b1274610",
  "channelId": "19:eeaa4e946d674c4f8d4dded613780f45@thread.v2",
  "messageId": "1580849738240"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Users.Item.Teamwork.DeleteTargetedMessage;

var requestBody = new DeleteTargetedMessagePostRequestBody
{
	TeamId = "9dda0ae1-e007-4a1d-81ec-2cf4b1274610",
	ChannelId = "19:eeaa4e946d674c4f8d4dded613780f45@thread.v2",
	MessageId = "1580849738240",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users["{user-id}"].Teamwork.DeleteTargetedMessage.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

requestBody := graphusers.NewDeleteTargetedMessagePostRequestBody()
teamId := "9dda0ae1-e007-4a1d-81ec-2cf4b1274610"
requestBody.SetTeamId(&teamId) 
channelId := "19:eeaa4e946d674c4f8d4dded613780f45@thread.v2"
requestBody.SetChannelId(&channelId) 
messageId := "1580849738240"
requestBody.SetMessageId(&messageId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Users().ByUserId("user-id").Teamwork().DeleteTargetedMessage().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.teamwork.deletetargetedmessage.DeleteTargetedMessagePostRequestBody deleteTargetedMessagePostRequestBody = new com.microsoft.graph.users.item.teamwork.deletetargetedmessage.DeleteTargetedMessagePostRequestBody();
deleteTargetedMessagePostRequestBody.setTeamId("9dda0ae1-e007-4a1d-81ec-2cf4b1274610");
deleteTargetedMessagePostRequestBody.setChannelId("19:eeaa4e946d674c4f8d4dded613780f45@thread.v2");
deleteTargetedMessagePostRequestBody.setMessageId("1580849738240");
graphClient.users().byUserId("{user-id}").teamwork().deleteTargetedMessage().post(deleteTargetedMessagePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const deleteTargetedMessage = {
  teamId: '9dda0ae1-e007-4a1d-81ec-2cf4b1274610',
  channelId: '19:eeaa4e946d674c4f8d4dded613780f45@thread.v2',
  messageId: '1580849738240'
};

await client.api('/users/f47b5f54-6968-4706-a522-31e842b12345/teamwork/deleteTargetedMessage')
	.post(deleteTargetedMessage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Teamwork\DeleteTargetedMessage\DeleteTargetedMessagePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new DeleteTargetedMessagePostRequestBody();
$requestBody->setTeamId('9dda0ae1-e007-4a1d-81ec-2cf4b1274610');
$requestBody->setChannelId('19:eeaa4e946d674c4f8d4dded613780f45@thread.v2');
$requestBody->setMessageId('1580849738240');

$graphServiceClient->users()->byUserId('user-id')->teamwork()->deleteTargetedMessage()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	teamId = "9dda0ae1-e007-4a1d-81ec-2cf4b1274610"
	channelId = "19:eeaa4e946d674c4f8d4dded613780f45@thread.v2"
	messageId = "1580849738240"
}

Remove-MgUserTeamworkTargetedMessage -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.teamwork.delete_targeted_message.delete_targeted_message_post_request_body import DeleteTargetedMessagePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = DeleteTargetedMessagePostRequestBody(
	team_id = "9dda0ae1-e007-4a1d-81ec-2cf4b1274610",
	channel_id = "19:eeaa4e946d674c4f8d4dded613780f45@thread.v2",
	message_id = "1580849738240",
)

await graph_client.users.by_user_id('user-id').teamwork.delete_targeted_message.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
