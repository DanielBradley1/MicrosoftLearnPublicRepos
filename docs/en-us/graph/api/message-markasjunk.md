<!-- Source: https://learn.microsoft.com/en-us/graph/api/message-markasjunk?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-08-18 -->

# message: markAsJunk \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The **markAsJunk** API is deprecated and will stop returning data on December 30, 2025. Going forward use the [reportMessage](https://learn.microsoft.com/en-us/graph/api/message-reportmessage?view=graph-rest-beta) API.

Mark a [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-beta) as junk. This API adds the sender to the list of blocked senders and moves the message to the **Junk Email** folder, when **moveToJunk** is `true`.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Mail.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Mail.ReadWrite | Not available. |
| Application | Mail.ReadWrite | Not available. |

## HTTP request

```http
POST /me/messages/{id}/markAsJunk
POST /users/{id | userPrincipalName}/messages/{id}/markAsJunk
POST /me/mailFolders/{id}/messages/{id}/markAsJunk
POST /users/{id | userPrincipalName}/mailFolders/{id}/messages/{id}/markAsJunk
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | `Bearer {token}`. Required. |
| Content-Type | `application/json`. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| moveToJunk | Boolean | `True` moves the message to the **Junk Email** folder. |

## Response

If successful, this method returns a `202 Accepted` response code and a [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-beta) object in the response body.

## Example

### Request

The following request moves the specified message to the **Junk Email** folder and adds the sender to the list of blocked senders.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/me/messages/AAMkADhAAATs28OAAA=/markAsJunk
Content-type: application/json

{
  "moveToJunk": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Me.Messages.Item.MarkAsJunk;

var requestBody = new MarkAsJunkPostRequestBody
{
	MoveToJunk = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Messages["{message-id}"].MarkAsJunk.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-beta-sdk-go/users"
	  //other-imports
)

requestBody := graphusers.NewItemMarkAsJunkPostRequestBody()
moveToJunk := true
requestBody.SetMoveToJunk(&moveToJunk) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
markAsJunk, err := graphClient.Me().Messages().ByMessageId("message-id").MarkAsJunk().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.users.item.messages.item.markasjunk.MarkAsJunkPostRequestBody markAsJunkPostRequestBody = new com.microsoft.graph.beta.users.item.messages.item.markasjunk.MarkAsJunkPostRequestBody();
markAsJunkPostRequestBody.setMoveToJunk(true);
var result = graphClient.me().messages().byMessageId("{message-id}").markAsJunk().post(markAsJunkPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const message = {
  moveToJunk: true
};

await client.api('/me/messages/AAMkADhAAATs28OAAA=/markAsJunk')
	.version('beta')
	.post(message);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Users\Item\Messages\Item\MarkAsJunk\MarkAsJunkPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MarkAsJunkPostRequestBody();
$requestBody->setMoveToJunk(true);

$result = $graphServiceClient->me()->messages()->byMessageId('message-id')->markAsJunk()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Beta.Mail

$params = @{
	moveToJunk = $true
}

# A UPN can also be used as -UserId.
Invoke-MgBetaMarkUserMessageAsJunk -UserId $userId -MessageId $messageId -BodyParameter $params
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.users.item.messages.item.mark_as_junk.mark_as_junk_post_request_body import MarkAsJunkPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MarkAsJunkPostRequestBody(
	move_to_junk = True,
)

result = await graph_client.me.messages.by_message_id('message-id').mark_as_junk.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#message",
  "@odata.type": "#microsoft.graph.message",
  "@odata.etag": "W/\"FwAAABYAAAC4ofQHEIqCSbQPot83AFcbAAAW/0tB\"",
  "id": "AAMkADhAAAW-VPeAAA=",
  "createdDateTime": "2018-08-12T08:43:22Z",
  "lastModifiedDateTime": "2018-08-15T19:47:54Z",
  "changeKey": "FwAAABYAAAC4ofQHEIqCSbQPot83AFcbAAAW/0tB",
  "categories": [],
  "receivedDateTime": "2018-08-12T08:43:22Z",
  "sentDateTime": "2018-08-12T08:43:20Z",
  "hasAttachments": false,
  "internetMessageId": "<00535324-5988-4b6a-b9af-d44cf2d0b691@MWHPR2201MB1022.namprd22.prod.outlook.com>",
  "subject": "Undeliverable: Meet for lunch?",
  "bodyPreview": "Delivery has failed to these recipients or groups:\r\n\r\nfannyd@contoso.com (fannyd@contoso.com)\r\nYour message couldn't be delivered. Despite repeated attempts to deliver your message, querying the Domain Name System (DNS) for the rec",
  "importance": "normal",
  "parentFolderId": "AAMkADhAAAAAAEKAAA=",
  "conversationId": "AAQkADhJzfbkARFhe5kKhjihSA=",
  "isDeliveryReceiptRequested": null,
  "isReadReceiptRequested": false,
  "isRead": false,
  "isDraft": false,
  "webLink": "https://outlook.office365.com/owa/?ItemID=AAMkADhAAAW%2FVPeAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "inferenceClassification": "focused",
  "body": {
    "contentType": "html",
    "content": "<html></html>"
  },
  "sender": {
    "emailAddress": {
      "name": "Microsoft Outlook",
      "address": "MicrosoftExchange329e71ec88ae4615bbc36ab6ce41109e@contoso.com"
    }
  },
  "from": {
    "emailAddress": {
      "name": "Microsoft Outlook",
      "address": "MicrosoftExchange329e71ec88ae4615bbc36ab6ce41109e@contoso.com"
    }
  },
  "toRecipients": [
    {
      "emailAddress": {
        "name": "fannyd@contoso.com",
        "address": "fannyd@contoso.com"
      }
    },
    {
      "emailAddress": {
        "name": "danas@contoso.com",
        "address": "danas@contoso.com"
      }
    }
  ],
  "ccRecipients": [],
  "bccRecipients": [],
  "replyTo": [],
  "flag": {
    "flagStatus": "notFlagged"
  }
}
```
