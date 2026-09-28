<!-- Source: https://learn.microsoft.com/en-us/graph/api/engagementconversationdiscussionmessage-list-reactions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List reactions

Namespace: microsoft.graph

Get a list of the [engagementConversationMessageReaction](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessagereaction?view=graph-rest-1.0) objects and their properties for an [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0) in an online meeting.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not available. | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | EngagementMeetingConversation.Read.All | Not available. |

## HTTP request

```http
GET /communications/onlineMeetingConversations/{onlineMeetingEngagementConversationId}/messages/{engagementConversationMessageId}/reactions
```

## Optional query parameters

This method doesn't support OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [engagementConversationMessageReaction](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessagereaction?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows how to get a list of reactions for a Teams questions and answers message.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
GET https://graph.microsoft.com/v1.0/communications/onlineMeetingConversations/eyJfdHlwZSI6IlRocmVhZCIsImlkIjoiMzM0NjU1NTExODA0MzEzNiJ9/messages/eyJfdHlwZSI6Ik1lc3NhZ2UiLCJpZCI6IjMzNDY1NTUxMTgwNDMxMzYifQ/reactions
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.OnlineMeetingConversations["{onlineMeetingEngagementConversation-id}"].Messages["{engagementConversationMessage-id}"].Reactions.GetAsync();
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
reactions, err := graphClient.Communications().OnlineMeetingConversations().ByOnlineMeetingEngagementConversationId("onlineMeetingEngagementConversation-id").Messages().ByEngagementConversationMessageId("engagementConversationMessage-id").Reactions().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EngagementConversationMessageReactionCollectionResponse result = graphClient.communications().onlineMeetingConversations().byOnlineMeetingEngagementConversationId("{onlineMeetingEngagementConversation-id}").messages().byEngagementConversationMessageId("{engagementConversationMessage-id}").reactions().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let reactions = await client.api('/communications/onlineMeetingConversations/eyJfdHlwZSI6IlRocmVhZCIsImlkIjoiMzM0NjU1NTExODA0MzEzNiJ9/messages/eyJfdHlwZSI6Ik1lc3NhZ2UiLCJpZCI6IjMzNDY1NTUxMTgwNDMxMzYifQ/reactions')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->communications()->onlineMeetingConversations()->byOnlineMeetingEngagementConversationId('onlineMeetingEngagementConversation-id')->messages()->byEngagementConversationMessageId('engagementConversationMessage-id')->reactions()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

Get-MgCommunicationOnlineMeetingConversationMessageReaction -OnlineMeetingEngagementConversationId $onlineMeetingEngagementConversationId -EngagementConversationMessageId $engagementConversationMessageId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.communications.online_meeting_conversations.by_online_meeting_engagement_conversation_id('onlineMeetingEngagementConversation-id').messages.by_engagement_conversation_message_id('engagementConversationMessage-id').reactions.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#communications/onlineMeetingConversations('eyJfdHlwZSI6IlRocmVhZCIsImlkIjoiMzM0NjU1NTExODA0MzEzNiJ9')/messages('eyJfdHlwZSI6Ik1lc3NhZ2UiLCJpZCI6IjMzNDY1NTUxMTgwNDMxMzYifQ')/reactions",
  "@odata.nextLink": "/communications/onlineMeetingConversations('eyJfdHlwZSI6IlRocmVhZCIsImlkIjoiMzM0NjU1NTExODA0MzEzNiJ9')/messages('eyJfdHlwZSI6Ik1lc3NhZ2UiLCJpZCI6IjMzNDY1NTUxMTgwNDMxMzYifQ')/reactions&skipToken=eyADASSDSA",
  "value": [
    {
      "@odata.type": "#microsoft.graph.engagementConversationMessageReaction",
      "id": "eyJxFkLBYM09IlRocmVhZCIsImlkIjoiMzM0NjU1NT0MzEzNiJ9ExODA",
      "createdDateTime": "2019-02-04T19:58:15.511Z",
      "reactionBy": {
        "user": {
          "displayName": "admin@a830edad9050849lq4lepgz0ubr.onmicrosoft.com",
          "id": "04222c1b-87eb-4cb1-80af-85cae1847a3c"
        }
      },
      "reactionType": "like"
    }
  ]
}
```
