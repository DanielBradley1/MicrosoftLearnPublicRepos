<!-- Source: https://learn.microsoft.com/en-us/graph/api/userteamwork-getalltargetedmessages?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# userTeamwork: getAllTargetedMessages

Namespace: microsoft.graph

Get all [targeted messages](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) sent to a specific user in group chats and channels.

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
GET /users/{user-id | userPrincipalName}/teamwork/getAllTargetedMessages
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
GET /users/{user-id | userPrincipalName}/teamwork/getAllTargetedMessages?$filter=lastModifiedDateTime gt 2024-01-01T00:00:00Z and lastModifiedDateTime lt 2024-12-31T23:59:59Z
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a collection of [targetedChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) objects in the response body.

The response includes the **@odata.nextLink** property for pagination and the **@odata.deltaLink** property for delta tracking, when applicable.

## Examples

### Example 1: Get all targeted messages for a user

The following example shows how to retrieve all targeted messages for a user.

#### Request

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
GET https://graph.microsoft.com/v1.0/users/f47b5f54-6968-4706-a522-31e842b12345/teamwork/getAllTargetedMessages
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.GetAllTargetedMessages.GetAsGetAllTargetedMessagesGetResponseAsync();
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
getAllTargetedMessages, err := graphClient.Users().ByUserId("user-id").Teamwork().GetAllTargetedMessages().GetAsGetAllTargetedMessagesGetResponse(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.users().byUserId("{user-id}").teamwork().getAllTargetedMessages().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getAllTargetedMessages = await client.api('/users/f47b5f54-6968-4706-a522-31e842b12345/teamwork/getAllTargetedMessages')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->getAllTargetedMessages()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

Get-MgUserTeamworkTargetedMessage -UserId $userId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').teamwork.get_all_targeted_messages.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response that includes both chat and channel context–targeted messages.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(targetedChatMessage)",
  "@odata.count": 2,
  "@odata.nextLink": "https://graph.microsoft.com/v1.0/users/f47b5f54-6968-4706-a522-31e842b12345/teamwork/getAllTargetedMessages?$top=2&$skiptoken=U2tpcFZhbHVlPTIjTWFpbGJveEZvbGRlcj1NYWlsRm9sZGVycy9UZWFtc01lc3NhZ2VzRGF0YQ",
  "value": [
    {
      "id": "1580849738240",
      "@odata.type": "#microsoft.graph.targetedChatMessage",
      "replyToId": null,
      "etag": "1580849738240",
      "chatId": "19:eeaa4e946d674c4f8d4dded613780f45@thread.v2",
      "channelIdentity": null,
      "messageType": "message",
      "createdDateTime": "2020-02-04T20:55:38.24Z",
      "lastModifiedDateTime": null,
      "deletedDateTime": null,
      "subject": null,
      "summary": null,
      "importance": "normal",
      "locale": "en-us",
      "webUrl": null,
      "policyViolation": null,
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
        "contentType": "text",
        "content": "hello"
      },
      "attachments": [],
      "mentions": [],
      "reactions": [],
      "recipient": {
        "@odata.type": "#microsoft.graph.identity",
        "id": "1273a016-201d-4f95-8083-1b7f99b3edeb",
        "displayName": "Adele Vance"
      }
    },
    {
      "id": "1580849738241",
      "@odata.type": "#microsoft.graph.targetedChatMessage",
      "replyToId": null,
      "etag": "1580849738241",
      "chatId": null,
      "channelIdentity": {
        "channelId": "19:eeaa4e946d674c4f8d4dded613780f45@thread.v2",
        "teamId": "3Aeeaa4e946d674c4f8d4dded613780f45@thread.v2"
      },
      "messageType": "message",
      "createdDateTime": "2020-02-04T20:55:38.24Z",
      "lastModifiedDateTime": null,
      "deletedDateTime": null,
      "subject": null,
      "summary": null,
      "importance": "normal",
      "locale": "en-us",
      "webUrl": null,
      "policyViolation": null,
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
        "contentType": "text",
        "content": "hello"
      },
      "attachments": [],
      "mentions": [],
      "reactions": [],
      "recipient": {
        "@odata.type": "#microsoft.graph.identity",
        "id": "1273a016-201d-4f95-8083-1b7f99b3edeb",
        "displayName": "Adele Vance"
      }
    }
  ]
}
```

### Example 2: Filter targeted messages by date range

The following example shows how to retrieve targeted messages within a specific date range.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
GET https://graph.microsoft.com/v1.0/users/f47b5f54-6968-4706-a522-31e842b12345/teamwork/getAllTargetedMessages?$filter=lastModifiedDateTime gt 2024-01-01T00:00:00Z and lastModifiedDateTime lt 2024-12-31T23:59:59Z
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.GetAllTargetedMessages.GetAsGetAllTargetedMessagesGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "lastModifiedDateTime gt 2024-01-01T00:00:00Z and lastModifiedDateTime lt 2024-12-31T23:59:59Z";
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


requestFilter := "lastModifiedDateTime gt 2024-01-01T00:00:00Z and lastModifiedDateTime lt 2024-12-31T23:59:59Z"

requestParameters := &graphusers.ItemTeamworkGetAllTargetedMessagesRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphusers.ItemTeamworkGetAllTargetedMessagesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
getAllTargetedMessages, err := graphClient.Users().ByUserId("user-id").Teamwork().GetAllTargetedMessages().GetAsGetAllTargetedMessagesGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.users().byUserId("{user-id}").teamwork().getAllTargetedMessages().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "lastModifiedDateTime gt 2024-01-01T00:00:00Z and lastModifiedDateTime lt 2024-12-31T23:59:59Z";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getAllTargetedMessages = await client.api('/users/f47b5f54-6968-4706-a522-31e842b12345/teamwork/getAllTargetedMessages')
	.filter('lastModifiedDateTime gt 2024-01-01T00:00:00Z and lastModifiedDateTime lt 2024-12-31T23:59:59Z')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Teamwork\GetAllTargetedMessages\GetAllTargetedMessagesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GetAllTargetedMessagesRequestBuilderGetRequestConfiguration();
$queryParameters = GetAllTargetedMessagesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "lastModifiedDateTime gt 2024-01-01T00:00:00Z and lastModifiedDateTime lt 2024-12-31T23:59:59Z";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->getAllTargetedMessages()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

Get-MgUserTeamworkTargetedMessage -UserId $userId -Filter "lastModifiedDateTime gt 2024-01-01T00:00:00Z and lastModifiedDateTime lt 2024-12-31T23:59:59Z" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.teamwork.get_all_targeted_messages.get_all_targeted_messages_request_builder import GetAllTargetedMessagesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GetAllTargetedMessagesRequestBuilder.GetAllTargetedMessagesRequestBuilderGetQueryParameters(
		filter = "lastModifiedDateTime gt 2024-01-01T00:00:00Z and lastModifiedDateTime lt 2024-12-31T23:59:59Z",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.by_user_id('user-id').teamwork.get_all_targeted_messages.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(targetedChatMessage)",
  "@odata.count": 1,
  "value": [
    {
      "id": "1704067200000",
      "@odata.type": "#microsoft.graph.targetedChatMessage",
      "replyToId": null,
      "etag": "1704067200000",
      "chatId": "19:eeaa4e946d674c4f8d4dded613780f45@thread.v2",
      "channelIdentity": null,
      "messageType": "message",
      "createdDateTime": "2024-01-01T00:00:00Z",
      "lastModifiedDateTime": "2024-01-01T00:00:00Z",
      "deletedDateTime": null,
      "subject": null,
      "summary": null,
      "importance": "normal",
      "locale": "en-us",
      "webUrl": null,
      "policyViolation": null,
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
        "contentType": "text",
        "content": "Filtered message content"
      },
      "attachments": [],
      "mentions": [],
      "reactions": [],
      "recipient": {
        "@odata.type": "#microsoft.graph.identity",
        "id": "1273a016-201d-4f95-8083-1b7f99b3edeb",
        "displayName": "Adele Vance"
      }
    }
  ]
}
```

### Example 3: Get targeted messages by application sender

The following example retrieves targeted messages sent by a specific application.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
GET https://graph.microsoft.com/v1.0/users/f47b5f54-6968-4706-a522-31e842b12345/teamwork/getAllTargetedMessages?$filter=from/application/id eq '6d23e712-527b-406f-8d59-d02927885918'
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Teamwork.GetAllTargetedMessages.GetAsGetAllTargetedMessagesGetResponseAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Filter = "from/application/id eq '6d23e712-527b-406f-8d59-d02927885918'";
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


requestFilter := "from/application/id eq '6d23e712-527b-406f-8d59-d02927885918'"

requestParameters := &graphusers.ItemTeamworkGetAllTargetedMessagesRequestBuilderGetQueryParameters{
	Filter: &requestFilter,
}
configuration := &graphusers.ItemTeamworkGetAllTargetedMessagesRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
getAllTargetedMessages, err := graphClient.Users().ByUserId("user-id").Teamwork().GetAllTargetedMessages().GetAsGetAllTargetedMessagesGetResponse(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

var result = graphClient.users().byUserId("{user-id}").teamwork().getAllTargetedMessages().get(requestConfiguration -> {
	requestConfiguration.queryParameters.filter = "from/application/id eq '6d23e712-527b-406f-8d59-d02927885918'";
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let getAllTargetedMessages = await client.api('/users/f47b5f54-6968-4706-a522-31e842b12345/teamwork/getAllTargetedMessages')
	.filter('from/application/id eq \'6d23e712-527b-406f-8d59-d02927885918\'')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Teamwork\GetAllTargetedMessages\GetAllTargetedMessagesRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new GetAllTargetedMessagesRequestBuilderGetRequestConfiguration();
$queryParameters = GetAllTargetedMessagesRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->filter = "from/application/id eq '6d23e712-527b-406f-8d59-d02927885918'";
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->users()->byUserId('user-id')->teamwork()->getAllTargetedMessages()->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

Get-MgUserTeamworkTargetedMessage -UserId $userId -Filter "from/application/id eq '6d23e712-527b-406f-8d59-d02927885918'" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.teamwork.get_all_targeted_messages.get_all_targeted_messages_request_builder import GetAllTargetedMessagesRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = GetAllTargetedMessagesRequestBuilder.GetAllTargetedMessagesRequestBuilderGetQueryParameters(
		filter = "from/application/id eq '6d23e712-527b-406f-8d59-d02927885918'",
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.users.by_user_id('user-id').teamwork.get_all_targeted_messages.get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(targetedChatMessage)",
  "@odata.count": 1,
  "value": [
    {
      "@odata.type": "#microsoft.graph.targetedChatMessage",
      "id": "1580849738240",
      "replyToId": null,
      "etag": "1580849738240",
      "chatId": "19:eeaa4e946d674c4f8d4dded613780f45@thread.v2",
      "channelIdentity": null,
      "messageType": "message",
      "createdDateTime": "2020-02-04T20:55:38.24Z",
      "lastModifiedDateTime": "2020-02-04T20:55:38.24Z",
      "deletedDateTime": null,
      "subject": null,
      "summary": null,
      "importance": "normal",
      "locale": "en-us",
      "webUrl": null,
      "policyViolation": null,
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
        "contentType": "text",
        "content": "hello"
      },
      "attachments": [],
      "mentions": [],
      "reactions": [],
      "recipient": {
        "@odata.type": "#microsoft.graph.identity",
        "id": "1273a016-201d-4f95-8083-1b7f99b3edeb",
        "displayName": "Adele Vance"
      }
    }
  ]
}
```
