<!-- Source: https://learn.microsoft.com/en-us/graph/api/call-addlargegalleryview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# call: addLargeGalleryView

Namespace: microsoft.graph

Add the large gallery view to a call.

For details about how to identify a large gallery view participant in a roster so that you can retrieve the relevant data to subscribe to the video feed, see [Identify large gallery view participants in a roster](https://learn.microsoft.com/en-us/graph/cloud-communications-identifylargegalleryview).

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
| Application | Calls.JoinGroupCallAsGuest.All | Calls.InitiateGroupCall.All, Calls.JoinGroupCall.All |

## HTTP request

```http
POST /app/calls/{id}/addLargeGalleryView
POST /communications/calls/{id}/addLargeGalleryView
```

> **Note:** The `/app` path is deprecated. Going forward, use the `/communications` path.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameter.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| clientContext | String | Unique client context string that can have a maximum of 256 characters. |

## Response

If successful, this method returns a `202 Accepted` response code and an [addLargeGalleryViewOperation](https://learn.microsoft.com/en-us/graph/api/resources/addlargegalleryviewoperation?view=graph-rest-1.0) object in the response body.

## Example

### Request

The following example shows how to add the large gallery view to a call.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896/addLargeGalleryView
Content-Type: application/json
Content-Length: 46

{
  "clientContext": "785f4929-92ca-497b-863f-c778c77c9758"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Communications.Calls.Item.AddLargeGalleryView;

var requestBody = new AddLargeGalleryViewPostRequestBody
{
	ClientContext = "785f4929-92ca-497b-863f-c778c77c9758",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.Calls["{call-id}"].AddLargeGalleryView.PostAsync(requestBody);
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

requestBody := graphcommunications.NewAddLargeGalleryViewPostRequestBody()
clientContext := "785f4929-92ca-497b-863f-c778c77c9758"
requestBody.SetClientContext(&clientContext) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
addLargeGalleryView, err := graphClient.Communications().Calls().ByCallId("call-id").AddLargeGalleryView().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.communications.calls.item.addlargegalleryview.AddLargeGalleryViewPostRequestBody addLargeGalleryViewPostRequestBody = new com.microsoft.graph.communications.calls.item.addlargegalleryview.AddLargeGalleryViewPostRequestBody();
addLargeGalleryViewPostRequestBody.setClientContext("785f4929-92ca-497b-863f-c778c77c9758");
var result = graphClient.communications().calls().byCallId("{call-id}").addLargeGalleryView().post(addLargeGalleryViewPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const addLargeGalleryViewOperation = {
  clientContext: '785f4929-92ca-497b-863f-c778c77c9758'
};

await client.api('/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896/addLargeGalleryView')
	.post(addLargeGalleryViewOperation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Communications\Calls\Item\AddLargeGalleryView\AddLargeGalleryViewPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new AddLargeGalleryViewPostRequestBody();
$requestBody->setClientContext('785f4929-92ca-497b-863f-c778c77c9758');

$result = $graphServiceClient->communications()->calls()->byCallId('call-id')->addLargeGalleryView()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	clientContext = "785f4929-92ca-497b-863f-c778c77c9758"
}

Add-MgCommunicationCallLargeGalleryView -CallId $callId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.communications.calls.item.add_large_gallery_view.add_large_gallery_view_post_request_body import AddLargeGalleryViewPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = AddLargeGalleryViewPostRequestBody(
	client_context = "785f4929-92ca-497b-863f-c778c77c9758",
)

result = await graph_client.communications.calls.by_call_id('call-id').add_large_gallery_view.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 ACCEPTED
Location: https://graph.microsoft.com/v1.0/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896/operations/e33176d4-836a-4fd7-b95a-d11bda52811d

{
  "@odata.type": "#microsoft.graph.addLargeGalleryViewOperation",
  "clientContext": "785f4929-92ca-497b-863f-c778c77c9758",
  "id": "e33176d4-836a-4fd7-b95a-d11bda52811d",
  "resultInfo": null,
  "status": "running"
}
```

### Notification - operation completed

```http
POST https://bot.contoso.com/api/calls
Content-Type: application/json
```

```json
{
  "@odata.type": "#microsoft.graph.commsNotifications",
  "value": [
    {
      "@odata.type": "#microsoft.graph.commsNotification",
      "changeType": "deleted",
      "resourceUrl": "/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896/operations/e33176d4-836a-4fd7-b95a-d11bda52811d",
      "resourceData": {
        "@odata.type": "#microsoft.graph.addLargeGalleryViewOperation",
        "@odata.id": "/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896/operations/e33176d4-836a-4fd7-b95a-d11bda52811d",
        "clientContext": "785f4929-92ca-497b-863f-c778c77c9758",
        "status": "completed"
      }
    }
  ]
}
```

## Related content

- [Identify large gallery view participants in a roster](https://learn.microsoft.com/en-us/graph/cloud-communications-identifylargegalleryview)
