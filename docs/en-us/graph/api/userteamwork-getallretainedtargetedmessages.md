<!-- Source: https://learn.microsoft.com/en-us/graph/api/userteamwork-getallretainedtargetedmessages?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# userTeamwork: getAllRetainedTargetedMessages

Namespace: microsoft.graph

Get all retained [targeted messages](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) sent to a specific user in group chats and channels.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamworkTargetedMessage.Read.All | Not available. |

## HTTP request

```http
GET /users/{user-id | userPrincipalName}/teamwork/getAllRetainedTargetedMessages
```

## Optional query parameters

This method supports the following OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

| Name | Description |
| :--- | :--- |
| $filter | The [$filter](https://learn.microsoft.com/en-us/graph/query-parameters#filter-parameter) query parameter supports date and time range queries on the **lastModifiedDateTime** property using [date range parameters](https://learn.microsoft.com/en-us/graph/query-parameters). |
| $top | Use the [$top](https://learn.microsoft.com/en-us/graph/query-parameters#top-parameter) query parameter to control the number of items per response. |

### Supported $filter operators

The following filter expressions are supported:

- `lastModifiedDateTime gt {datetime}` - Returns messages modified after the specified date and time.
- `lastModifiedDateTime lt {datetime}` - Returns messages modified before the specified date and time.
- `from/application/id eq '{id}'` - Returns messages sent by a specific application ID.

You can combine multiple filter expressions using the `and` operator. For example:

```http
GET /users/{user-id | userPrincipalName}/teamwork/getAllRetainedTargetedMessages?$filter=lastModifiedDateTime gt 2024-01-01T00:00:00Z and lastModifiedDateTime lt 2024-12-31T23:59:59Z
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a collection of [targetedChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) objects in the response body.

The response includes the **@odata.nextLink** property for pagination, when applicable.

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
GET https://graph.microsoft.com/v1.0/users/f47b5f54-6968-4706-a522-31e842b12345/teamwork/getAllRetainedTargetedMessages
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.GetAllRetainedTargetedMessages.GetAsGetAllRetainedTargetedMessagesGetResponseAsync();
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
getAllRetainedTargetedMessages, err := graphClient.Users().ByUserId("user-id").Teamwork().GetAllRetainedTargetedMessages().GetAsGetAllRetainedTargetedMessagesGetResponse(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.users().byUserId("{user-id}").teamwork().getAllRetainedTargetedMessages().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getAllRetainedTargetedMessages = await client.api('/users/f47b5f54-6968-4706-a522-31e842b12345/teamwork/getAllRetainedTargetedMessages')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->getAllRetainedTargetedMessages()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

Get-MgUserTeamworkRetainedTargetedMessage -UserId $userId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').teamwork.get_all_retained_targeted_messages.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(targetedChatMessage)",
  "@odata.count": 1,
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/users/f47b5f54-6968-4706-a522-31e842b12345/teamwork/getAllRetainedTargetedMessages?$top=1&$skiptoken=Token",
  "value": [
    {
      "@odata.type": "#microsoft.graph.targetedChatMessage",
      "id": "1684961612345",
      "replyToId": null,
      "etag": "1684962512345",
      "messageType": "message",
      "createdDateTime": "2023-05-24T20:54:49.858Z",
      "lastModifiedDateTime": "2023-05-24T21:13:15Z",
      "lastEditedDateTime": "2023-05-24T21:09:00.224Z",
      "deletedDateTime": null,
      "subject": "",
      "summary": null,
      "chatId": "19:1a546d42d8b54a16903716f49b512345@thread.v2",
      "importance": "normal",
      "locale": "en-us",
      "webUrl": null,
      "channelIdentity": null,
      "onBehalfOf": null,
      "policyViolation": null,
      "eventDetail": null,
      "from": {
        "device": null,
        "user": null,
        "application": {
          "@odata.type": "#microsoft.graph.teamworkApplicationIdentity",
          "id": "6d23e712-527b-406f-8d59-d02927885918",
          "displayName": "Breakthru",
          "applicationIdentityType": "bot"
        }
      },
      "body": {
        "contentType": "html",
        "content": "<p>5/24 group chat</p>"
      },
      "attachments": [],
      "mentions": [],
      "reactions": [],
      "messageHistory": [],
      "recipient": {
        "@odata.type": "#microsoft.graph.identity",
        "id": "1273a016-201d-4f95-8083-1b7f99b3edeb",
        "displayName": "Adele Vance"
      }
    }
  ]
}
```
