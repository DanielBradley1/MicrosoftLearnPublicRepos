<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudcommunications-getallonlinemeetingmessages?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# cloudCommunications: getAllOnlineMeetingMessages

Namespace: microsoft.graph

Get all Teams question and answer \(Q&A\) conversation messages in a tenant. This function returns a snapshot of all Q&A activity in JSON format.

The export includes:

- The original question or discussion text
- The user who posted the message
- All replies and responders
- Vote counts
- Moderation status \(pending or dismissed\)
- Private replies
- The meeting ID and organizer ID that are used for mapping to meeting metadata.

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
| Application | EngagementMeetingConversation.Read.All | Not available. |

## HTTP request

```http
GET /communications/getAllOnlineMeetingMessages
```

## Optional query parameters

This method supports the `$expand` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a collection of [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0) objects in the response body.

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
GET https://graph.microsoft.com/v1.0/communications/getAllOnlineMeetingMessages?$expand=conversation
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.GetAllOnlineMeetingMessages.GetAsGetAllOnlineMeetingMessagesGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "conversation" };
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphcommunications "github.com/microsoftgraph/msgraph-sdk-go/communications"
	  //other-imports
)

requestParameters := &graphcommunications.CommunicationsGetAllOnlineMeetingMessagesRequestBuilderGetQueryParameters{
	Expand: [] string {"conversation"},
}
configuration := &graphcommunications.CommunicationsGetAllOnlineMeetingMessagesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
getAllOnlineMeetingMessages, err := graphClient.Communications().GetAllOnlineMeetingMessages().GetAsGetAllOnlineMeetingMessagesGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.communications().getAllOnlineMeetingMessages().get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"conversation"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getAllOnlineMeetingMessages = await client.api('/communications/getAllOnlineMeetingMessages')
	.expand('conversation')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Communications\GetAllOnlineMeetingMessages\GetAllOnlineMeetingMessagesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GetAllOnlineMeetingMessagesRequestBuilderGetRequestConfiguration();
$queryParameters = GetAllOnlineMeetingMessagesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["conversation"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->communications()->getAllOnlineMeetingMessages()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

Get-MgCommunicationOnlineMeetingMessage -ExpandProperty "conversation" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.communications.get_all_online_meeting_messages.get_all_online_meeting_messages_request_builder import GetAllOnlineMeetingMessagesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GetAllOnlineMeetingMessagesRequestBuilder.GetAllOnlineMeetingMessagesRequestBuilderGetQueryParameters(
		expand = ["conversation"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.communications.get_all_online_meeting_messages.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#communications/getAllOnlineMeetingMessages",
  "@odata.nextLink": "/communications/getAllOnlineMeetingMessages?$expand=conversation&skipToken=eyADASSDSA",
  "value": [
    {
      "@odata.type": "#microsoft.graph.engagementConversationDiscussionMessage",
      "id": "eyJfdHlwZSI6IlRocmVhZCIsImlkIjoiMzM0OTcwNzMxNTEyNjI3MiJ9",
      "createdDateTime": "2025-05-20T06:35:58.936313Z",
      "lastModifiedDateTime": "2025-05-20T06:35:58.936313Z",
      "replyToId": "eyJjh1wwZSI6IlRocmVhZCIsImlkIjxyzqzM0OTcwNzMxNTEyNjI2q1fw",
      "from": {
        "user": {
          "displayName": "John Doe",
          "id": "611b1c2b-8935-4068-8445-2f73aec6cc3f"
        }
      },
      "body": {
        "content": "This is a sample message body.",
        "contentType": "html"
      },
      "mentions": [],
      "attachments": [],
      "conversation": {
        "@odata.type": "#microsoft.graph.onlineMeetingEngagementConversation",
        "id": "eyJjh1wwZSI6IlRocmVhZCIsImlkIjxyzqzM0OTcwNzMxNTEyNjI2q1fw7",
        "starterId": "eyJjh1wwZSI6IlRocmVhZCIsImlkIjxyzqzM0OTcwNzMxNTEyNjI2q1fw",
        "moderationState": "published",
        "upvoteCount": 5,
        "onlineMeetingId": "MSoxMjczYTAxNi0yMDFkRLTmOTUtODA5My0xYjdmOTliM2VkZWIqMCoqMTk6bWVldGluZ19aR1F3WTJZNE9XTXROekppWlMwME1XWTRMVGc0TWpBdE1BBXdOV1kzWlRsak9UTXlAdGhyZWFkLnYy",
        "organizer": {
          "user": {
            "displayName": "Meeting Organizer",
            "id": "3fe108bf-1d01-43d6-a7f4-b2b697f02c90"
          }
        }
      }
    }
  ]
}
```
