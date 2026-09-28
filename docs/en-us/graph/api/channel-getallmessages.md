<!-- Source: https://learn.microsoft.com/en-us/graph/api/channel-getallmessages?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-03 -->

# channel: getAllMessages

Namespace: microsoft.graph

Retrieve [messages](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) across all [channels](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) in a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0), including text, audio, and video conversations.

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
| Application | ChannelMessage.Read.All | Not available. |

## HTTP request

```http
GET /teams/{team-id}/channels/getAllMessages
```

## Optional query parameters

You can use the [$top](https://learn.microsoft.com/en-us/graph/query-parameters#top-parameter) query parameter to control the number of items per response. Additionally, [$filter](https://learn.microsoft.com/en-us/graph/query-parameters#filter-parameter) is supported with **dateTime** range query on **lastModifiedDateTime**. The other [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) aren't currently supported.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {code}. Required. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and also returns all the messages in all the public and private channels.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/teams/01fe12e0-e720-44fd-8854-28c66d1bee40/channels/getAllMessages?$filter=lastModifiedDateTime+gt+2019-11-01T00:00:00Z+and lastModifiedDateTime+lt+2021-11-01T00:00:00Z
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Channels.GetAllMessages.GetAsGetAllMessagesGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "lastModifiedDateTime gt 2019-11-01T00:00:00Z and lastModifiedDateTime lt 2021-11-01T00:00:00Z";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphteams "github.com/microsoftgraph/msgraph-sdk-go/teams"
	  //other-imports
)


requestFilter := "lastModifiedDateTime gt 2019-11-01T00:00:00Z and lastModifiedDateTime lt 2021-11-01T00:00:00Z"

requestParameters := &graphteams.ItemChannelsGetAllMessagesRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphteams.ItemChannelsGetAllMessagesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
getAllMessages, err := graphClient.Teams().ByTeamId("team-id").Channels().GetAllMessages().GetAsGetAllMessagesGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.teams().byTeamId("{team-id}").channels().getAllMessages().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "lastModifiedDateTime gt 2019-11-01T00:00:00Z and lastModifiedDateTime lt 2021-11-01T00:00:00Z";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getAllMessages = await client.api('/teams/01fe12e0-e720-44fd-8854-28c66d1bee40/channels/getAllMessages')
	.filter('lastModifiedDateTime gt 2019-11-01T00:00:00Z and lastModifiedDateTime lt 2021-11-01T00:00:00Z')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\Channels\GetAllMessages\GetAllMessagesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GetAllMessagesRequestBuilderGetRequestConfiguration();
$queryParameters = GetAllMessagesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "lastModifiedDateTime gt 2019-11-01T00:00:00Z and lastModifiedDateTime lt 2021-11-01T00:00:00Z";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->teams()->byTeamId('team-id')->channels()->getAllMessages()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.channels.get_all_messages.get_all_messages_request_builder import GetAllMessagesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GetAllMessagesRequestBuilder.GetAllMessagesRequestBuilderGetQueryParameters(
		filter = "lastModifiedDateTime gt 2019-11-01T00:00:00Z and lastModifiedDateTime lt 2021-11-01T00:00:00Z",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.teams.by_team_id('team-id').channels.get_all_messages.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(chatMessage)",
    "@odata.count": 2,
    "@odata.nextLink": "https://graph.microsoft.com/v1.0/teams('01fe12e0-e720-44fd-8854-28c66d1bee40')/channels/getallMessages?$skiptoken=U2tpcFZhbHVlPTAjUHJpdmF0ZUNoYW5uZWxJZD0xOTpmYWU5YTJmZjk1ZGE0ZTEwOWE1YTg3ZTM5Y2FkOGYyYkB0aHJlYWQudGFjdjIjVXNlcklkPTBkN2M2M2QzLTEzMDYtNGVlYy04ZjIxLTU4OGE3MGZiNmVmMSNNYWlsYm94Rm9sZGVyPU1haWxGb2xkZXJzL1RlYW1DaGF0&$filter=lastModifiedDateTime+gt+2019-11-01T00%3a00%3a00Z+and+lastModifiedDateTime+lt+2021-11-01T00%3a00%3a00Z",
    "value": [
        {
            "@odata.type": "#microsoft.graph.chatMessage",
            "id": "1622071758431",
            "replyToId": "1622071642456",
            "etag": "1622071758431",
            "messageType": "message",
            "createdDateTime": "2021-05-26T23:29:18.431Z",
            "lastModifiedDateTime": "2021-05-26T23:29:18.431Z",
            "lastEditedDateTime": null,
            "deletedDateTime": null,
            "subject": null,
            "summary": null,
            "chatId": null,
            "importance": "normal",
            "locale": "en-us",
            "webUrl": "https://teams.microsoft.com/l/message/19%3Afae9a2ff95da4e109a5a87e39cad8f2b%40thread.tacv2/1622071758431?groupId=01fe12e0-e720-44fd-8854-28c66d1bee40&tenantId=9854dc85-3fb3-4f8e-a055-9cdc5523024d&createdTime=1622071758431&parentMessageId=1622071642456",
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
                "contentType": "html",
                "content": "<div>\n<div itemprop=\"copy-paste-block\">reply 9&nbsp;to new conv</div>\n</div>"
            },
            "channelIdentity": {
                "teamId": "01fe12e0-e720-44fd-8854-28c66d1bee40",
                "channelId": "19:fae9a2ff95da4e109a5a87e39cad8f2b@thread.tacv2"
            },
            "attachments": [],
            "mentions": [],
            "reactions": []
        },
        {
            "@odata.type": "#microsoft.graph.chatMessage",
            "id": "1622071764529",
            "replyToId": "1622071642456",
            "etag": "1622071764529",
            "messageType": "message",
            "createdDateTime": "2021-05-26T23:29:24.529Z",
            "lastModifiedDateTime": "2021-05-26T23:29:24.529Z",
            "lastEditedDateTime": null,
            "deletedDateTime": null,
            "subject": null,
            "summary": null,
            "chatId": null,
            "importance": "normal",
            "locale": "en-us",
            "webUrl": "https://teams.microsoft.com/l/message/19%3Afae9a2ff95da4e109a5a87e39cad8f2b%40thread.tacv2/1622071764529?groupId=01fe12e0-e720-44fd-8854-28c66d1bee40&tenantId=9854dc85-3fb3-4f8e-a055-9cdc5523024d&createdTime=1622071764529&parentMessageId=1622071642456",
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
                "contentType": "html",
                "content": "<div>\n<div itemprop=\"copy-paste-block\">reply 10 to new conv</div>\n</div>"
            },
            "channelIdentity": {
                "teamId": "01fe12e0-e720-44fd-8854-28c66d1bee40",
                "channelId": "19:fae9a2ff95da4e109a5a87e39cad8f2b@thread.tacv2"
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
