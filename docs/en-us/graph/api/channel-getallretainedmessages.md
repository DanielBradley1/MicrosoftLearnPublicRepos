<!-- Source: https://learn.microsoft.com/en-us/graph/api/channel-getallretainedmessages?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-05 -->

# channel: getAllRetainedMessages

Namespace: microsoft.graph

Get all retained [messages](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) across all [channels](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) in a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0).

To learn more about how to use the Microsoft Teams export APIs to export content, see [Export content with the Microsoft Teams export APIs](https://learn.microsoft.com/en-us/microsoftteams/export-teams-content).

Note

This API requires [Teams retention policies](https://learn.microsoft.com/en-us/purview/create-retention-policies?tabs=teams-retention) to be configured. For more information, see [Learn about retention for Microsoft Teams](https://learn.microsoft.com/en-us/purview/retention-policies-teams).

Note

Teams migrated private-channel message storage from individual user mailboxes to group mailboxes, where standard channel messages are stored. For private channels, this API supports retained message history for messages edited or deleted after the tenant's storage migration completed, provided an applicable retention policy captured the versions. Edits or deletions that occurred before migration aren't returned because retained-history support wasn't available through this API during the legacy user-mailbox storage period.

A tenant administrator can run [Get-TenantPrivateChannelMigrationStatus](https://learn.microsoft.com/en-us/powershell/module/microsoftteams/get-tenantprivatechannelmigrationstatus?view=teams-ps&preserve-view=true) to verify that `MigrationStatus` is `Completed` and identify the tenant's `MigrationCompletionTimeStamp`. If `MigrationStatus` isn't `Completed`, `MigrationCompletionTimeStamp` isn't available and can't be used as a tenant-wide cutoff. For more information about the storage change, see [Migration of private channel messages in 2025](https://learn.microsoft.com/en-us/purview/retention-policies-teams#migration-of-private-channel-messages-in-2025).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ChannelMessage.Read.All | Not available. |

## HTTP request

```http
GET /teams/{teamsId}/channels/getAllRetainedMessages
```

## Optional query parameters

This method supports the following OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

| Name | Description |
| :--- | :--- |
| $filter | The [$filter](https://learn.microsoft.com/en-us/graph/query-parameters#filter-parameter) query parameter supports date and time range queries on the **lastModifiedDateTime** property. |
| $top | Use the [$top](https://learn.microsoft.com/en-us/graph/query-parameters#top-parameter) query parameter to control the number of items per response. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a collection of [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/teams/8b081ef6-4792-4def-b2c9-c363a1bf41d5/channels/getAllRetainedMessages
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels.GetAllRetainedMessages.GetAsGetAllRetainedMessagesGetResponseAsync();
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
getAllRetainedMessages, err := graphClient.Teams().ByTeamId("team-id").Channels().GetAllRetainedMessages().GetAsGetAllRetainedMessagesGetResponse(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.teams().byTeamId("{team-id}").channels().getAllRetainedMessages().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getAllRetainedMessages = await client.api('/teams/8b081ef6-4792-4def-b2c9-c363a1bf41d5/channels/getAllRetainedMessages')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->getAllRetainedMessages()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

Get-MgTeamChannelRetainedMessage -TeamId $teamId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.teams.by_team_id('team-id').channels.get_all_retained_messages.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(chatMessage)",
  "@odata.count": 2,
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/teams/fbe2bf47-16c8-47cf-b4a5-4b9b187c508b/channels/getAllRetainedMessages?$skip=2",
  "value": [
    {
      "@odata.type": "#microsoft.graph.chatMessage",
      "id": "1616990417393",
      "replyToId": null,
      "etag": "1616990417393",
      "messageType": "message",
      "createdDateTime": "2021-03-29T04:00:17.393Z",
      "lastModifiedDateTime": "2021-03-29T04:00:17.393Z",
      "lastEditedDateTime": null,
      "deletedDateTime": null,
      "subject": null,
      "summary": null,
      "chatId": null,
      "importance": "normal",
      "locale": "en-us",
      "webUrl": "https://teams.microsoft.com/l/message/19%3Ad5d2708d408c41d98424c1c354c19db3%40thread.tacv2/1616990417393?groupId=fbe2bf47-16c8-47cf-b4a5-4b9b187c508b&tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34&createdTime=1616990417393&parentMessageId=1616990417393",
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
        "contentType": "text",
        "content": "Test message"
      },
      "channelIdentity": {
        "teamId": "fbe2bf47-16c8-47cf-b4a5-4b9b187c508b",
        "channelId": "19:d5d2708d408c41d98424c1c354c19db3@thread.tacv2"
      },
      "attachments": [],
      "mentions": [],
      "reactions": []
    },
    {
      "@odata.type": "#microsoft.graph.chatMessage",
      "id": "1616990171266",
      "replyToId": "1616990032035",
      "etag": "1616990171266",
      "messageType": "message",
      "createdDateTime": "2021-03-29T03:56:11.266Z",
      "lastModifiedDateTime": "2021-03-29T03:56:11.266Z",
      "lastEditedDateTime": null,
      "deletedDateTime": null,
      "subject": null,
      "summary": null,
      "chatId": null,
      "importance": "normal",
      "locale": "en-us",
      "webUrl": "https://teams.microsoft.com/l/message/19%3A4a95f7d8db4c4e7fae857bcebe0623e6%40thread.tacv2/1616990171266?groupId=fbe2bf47-16c8-47cf-b4a5-4b9b187c508b&tenantId=2432b57b-0abd-43db-aa7b-16eadd115d34&createdTime=1616990171266&parentMessageId=1616990032035",
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
        "contentType": "text",
        "content": "Hello World"
      },
      "channelIdentity": {
        "teamId": "fbe2bf47-16c8-47cf-b4a5-4b9b187c508b",
        "channelId": "19:4a95f7d8db4c4e7fae857bcebe0623e6@thread.tacv2"
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
