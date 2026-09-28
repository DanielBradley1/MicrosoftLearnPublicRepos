<!-- Source: https://learn.microsoft.com/en-us/graph/api/chats-getallmessages?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# chats: getAllMessages

Namespace: microsoft.graph

Get all [messages](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) from all [chats](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) in which a user is a participant, including one-on-one chats, group chats, and meeting chats.

To learn more about how to use the Microsoft Teams export APIs to export content, see [Export content with the Microsoft Teams export APIs](https://learn.microsoft.com/en-us/microsoftteams/export-teams-content).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Chat.Read.All | Chat.ReadWrite.All |

## HTTP request

```http
GET /users/{id | user-principal-name}/chats/getAllMessages
```

## Optional query parameters

This method also supports [date range parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to customize the response, as shown in the following example.

```http
GET /users/{id}/chats/getAllMessages?$top=50&$filter=lastModifiedDateTime gt 2020-06-04T18:03:11.591Z and lastModifiedDateTime lt 2020-06-05T21:00:09.413Z
```

This method supports the `$filter` query parameter. The following table lists examples.

| Scenario | `$filter` parameter | Possible values |
| :--- | :--- | :--- |
| Get messages sent by user identity type | $filter=from/user/userIdentityType eq '{teamworkUserIdentityType}' | aadUser, onPremiseAadUser, anonymousGuest, federatedUser, personalMicrosoftAccountUser, skypeUser, phoneUser |
| Get messages sent by application type | $filter=from/application/applicationIdentityType eq '{teamworkApplicationIdentity}' | aadApplication, bot, tenantBot, office365Connector, outgoingWebhook |
| Get messages sent by user ID | $filter=from/user/id eq '{oid}' |  |
| Get control\(system event\) messages | $filter=messageType eq 'systemEventMessage' |  |
| Exclude control \(system event\) messages | $filter=messageType ne 'systemEventMessage' |  |

> **Note:** These filter clauses can be joined by using the `or` operator. A filter clause can appear more than once in a query, and it can filter on a different value each time it appears within the query..

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Response

If successful, this method returns a `200 OK` response code and a list of [chatMessages](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) in the response body.

## Example

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/users/0b4f1cf6-54c8-4820-bbb7-2a1f4257ade5/chats/getAllMessages?$top=2
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Chats.GetAllMessages.GetAsGetAllMessagesGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Top = 2;
});
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


requestTop := int32(2)

requestParameters := &graphusers.ItemChatsGetAllMessagesRequestBuilderGetQueryParameters{
	Top: &requestTop,
}
configuration := &graphusers.ItemChatsGetAllMessagesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
getAllMessages, err := graphClient.Users().ByUserId("user-id").Chats().GetAllMessages().GetAsGetAllMessagesGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.users().byUserId("{user-id}").chats().getAllMessages().get(requestConfiguration -> {
	requestConfiguration.queryParameters.top = 2;
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getAllMessages = await client.api('/users/0b4f1cf6-54c8-4820-bbb7-2a1f4257ade5/chats/getAllMessages')
	.top(2)
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Chats\GetAllMessages\GetAllMessagesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GetAllMessagesRequestBuilderGetRequestConfiguration();
$queryParameters = GetAllMessagesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->top = 2;
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->byUserId('user-id')->chats()->getAllMessages()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.chats.get_all_messages.get_all_messages_request_builder import GetAllMessagesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GetAllMessagesRequestBuilder.GetAllMessagesRequestBuilderGetQueryParameters(
		top = 2,
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.by_user_id('user-id').chats.get_all_messages.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(chatMessage)",
    "@odata.count": 2,
    "@odata.nextLink": "https://graph.microsoft.com/v1.0/users('0b4f1cf6-54c8-4820-bbb7-2a1f4257ade5')/chats/getallMessages?$top=2&$skiptoken=U2tpcFZhbHVlPTIjTWFpbGJveEZvbGRlcj1NYWlsRm9sZGVycy9UZWFtc01lc3NhZ2VzRGF0YQ%3d%3d",
    "value": [
        {
            "@odata.type": "#microsoft.graph.chatMessage",
            "id": "1621973534864",
            "replyToId": null,
            "etag": "1621973534864",
            "messageType": "message",
            "createdDateTime": "2021-05-25T20:12:14.864Z",
            "lastModifiedDateTime": "2021-05-25T20:12:14.864Z",
            "lastEditedDateTime": null,
            "deletedDateTime": null,
            "subject": null,
            "summary": null,
            "chatId": "19:3c9e92a344704332bbf5bda58f4d37b1@thread.v2",
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
                    "id": "0b4f1cf6-54c8-4820-bbb7-2a1f4257ade5",
                    "displayName": "user1 a",
                    "userIdentityType": "aadUser"
                }
            },
            "body": {
                "contentType": "text",
                "content": "Hello user2, user 3"
            },
            "attachments": [],
            "mentions": [],
            "reactions": []
        },
        {
            "@odata.type": "#microsoft.graph.chatMessage",
            "id": "1622762567488",
            "replyToId": null,
            "etag": "1622762567488",
            "messageType": "message",
            "createdDateTime": "2021-06-03T23:22:47.488Z",
            "lastModifiedDateTime": "2021-06-03T23:22:47.488Z",
            "lastEditedDateTime": null,
            "deletedDateTime": null,
            "subject": null,
            "summary": null,
            "chatId": "19:0b4f1cf6-54c8-4820-bbb7-2a1f4257ade5_0d7c63d3-1306-4eec-8f21-588a70fb6ef1@unq.gbl.spaces",
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
                    "id": "0b4f1cf6-54c8-4820-bbb7-2a1f4257ade5",
                    "displayName": "user1 a",
                    "userIdentityType": "aadUser"
                }
            },
            "body": {
                "contentType": "text",
                "content": "hi user2"
            },
            "attachments": [],
            "mentions": [],
            "reactions": []
        }
    ]
}
```

## Related content

[Microsoft Graph service-specific throttling limits](https://learn.microsoft.com/en-us/graph/throttling-limits#microsoft-teams-service-limits)
