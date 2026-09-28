<!-- Source: https://learn.microsoft.com/en-us/graph/api/conversationmember-list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-09 -->

# List conversationMembers

Namespace: microsoft.graph

List all [conversation members](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) in a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) or [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0).

Note

The membership IDs returned by the server must be treated as opaque strings. The client should not try to parse or make any assumptions about these resource IDs.

The membership results could map to users from different tenants, as indicated in the response, in the future.The client should not assume that all members are from the current tenant only.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Chat.ReadBasic | ChatMember.ReadWrite, Chat.Read, Chat.ReadWrite, ChatMember.Read |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ChatMember.Read.All | Chat.Manage.Chat, Chat.Read.All, Chat.ReadBasic.All, Chat.ReadWrite.All, ChatMember.Read.Chat, ChatMember.ReadWrite.All |

## HTTP request

```http
GET /chats/{id}/members
```

## Optional query parameters

This operation doesn't support the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to customize the response.

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a list of [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) objects in the response body.

## Example

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

```msgraph
GET https://graph.microsoft.com/v1.0/chats/19:9ef2dcdf14ba44cbae25c2f5d53171ba@thread.v2/members
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Chats["{chat-id}"].Members.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
members, err := graphClient.Chats().ByChatId("chat-id").Members().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ConversationMemberCollectionResponse result = graphClient.chats().byChatId("{chat-id}").members().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let members = await client.api('/chats/19:9ef2dcdf14ba44cbae25c2f5d53171ba@thread.v2/members')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->chats()->byChatId('chat-id')->members()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

Get-MgChatMember -ChatId $chatId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.chats.by_chat_id('chat-id').members.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#chats('19%3A9ef2dcdf14ba44cbae25c2f5d53171ba%40thread.v2')/members",
    "@odata.count": 4,
    "value": [
        {
            "@odata.type": "#microsoft.graph.aadUserConversationMember",
            "id": "MCMjMCMjOGQyMzc2NTAtY2RjMS00MGUxLTg5OWMtNTYwMWUwNTVmM2ZlIyMxOTo5ZWYyZGNkZjE0YmE0NGNiYWUyNWMyZjVkNTMxNzFiYUB0aHJlYWQudjIjIzE3ZTk1MjZjLTIyODYtNDFhMS1hZWViLTRiYWRlZTc2NjA2Mw==",
            "roles": [
                "owner"
            ],
            "displayName": "SA-TeamsAdconnect",
            "visibleHistoryStartDateTime": "2022-04-25T11:52:22.765Z",
            "userId": "17e9526c-2286-41a1-aeeb-4badee766063",
            "email": "SA-TeamsAdconnect@contoso.com",
            "tenantId": "8d237650-cdc1-40e1-899c-5601e055f3fe"
        },
        {
            "@odata.type": "#microsoft.graph.aadUserConversationMember",
            "id": "MCMjMCMjOGQyMzc2NTAtY2RjMS00MGUxLTg5OWMtNTYwMWUwNTVmM2ZlIyMxOTo5ZWYyZGNkZjE0YmE0NGNiYWUyNWMyZjVkNTMxNzFiYUB0aHJlYWQudjIjIzM3MjBiNWE3LTg1NzktNDM0My05NmJmLTQzNDIxNGQ2NTI2ZA==",
            "roles": [
                "owner"
            ],
            "displayName": "Mhamdi Wafa",
            "visibleHistoryStartDateTime": "2022-04-25T11:52:22.765Z",
            "userId": "3720b5a7-8579-4343-96bf-434214d6526d",
            "email": "wmhamdi@rtladconnect.com",
            "tenantId": "8d237650-cdc1-40e1-899c-5601e055f3fe"
        },
        {
            "@odata.type": "#microsoft.graph.aadUserConversationMember",
            "id": "MCMjMCMjZGNkMjE5ZGQtYmM2OC00YjliLWJmMGItNGEzM2E3OTZiZTM1IyMxOTo5ZWYyZGNkZjE0YmE0NGNiYWUyNWMyZjVkNTMxNzFiYUB0aHJlYWQudjIjIzQ4ZDMxODg3LTVmYWQtNGQ3My1hOWY1LTNjMzU2ZTY4YTAzOA==",
            "roles": [
                "owner"
            ],
            "displayName": "Megan Bowen",
            "visibleHistoryStartDateTime": "2022-04-25T11:52:22.765Z",
            "userId": "48d31887-5fad-4d73-a9f5-3c356e68a038",
            "email": "MeganB@contoso.com",
            "tenantId": "dcd219dd-bc68-4b9b-bf0b-4a33a796be35"
        },
        {
            "@odata.type": "#microsoft.graph.aadUserConversationMember",
            "id": "MCMjMCMjOGQyMzc2NTAtY2RjMS00MGUxLTg5OWMtNTYwMWUwNTVmM2ZlIyMxOTo5ZWYyZGNkZjE0YmE0NGNiYWUyNWMyZjVkNTMxNzFiYUB0aHJlYWQudjIjIzcxZjJjYzdmLTQwYWYtNDhkOS05ZDk2LTVhYTMzYjkxYmRkOA==",
            "roles": [
                "owner"
            ],
            "displayName": "Berrahal Mariem [RTL-AdConnect]",
            "visibleHistoryStartDateTime": "2022-04-25T11:59:47.226Z",
            "userId": "71f2cc7f-40af-48d9-9d96-5aa33b91bdd8",
            "email": "mberrahal@rtladconnect.com",
            "tenantId": "8d237650-cdc1-40e1-899c-5601e055f3fe"
        }
    ]
}
```
