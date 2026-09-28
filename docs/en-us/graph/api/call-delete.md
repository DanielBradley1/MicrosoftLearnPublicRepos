<!-- Source: https://learn.microsoft.com/en-us/graph/api/call-delete?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Delete call

Namespace: microsoft.graph

Delete or hang up an active call. For group calls, this will only delete your call leg and the underlying group call will still continue.

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
| Application | Calls.Initiate.All | Calls.AccessMedia.All |

> **Note:** Permissions are checked when the call is created; no additional permission check is made when calling this API. Calls.AccessMedia.All is only necessary for calls that use app-hosted media.

## HTTP request

```http
DELETE /communications/calls/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns `204 No Content` response code. It doesn't return anything in the response body.

## Example

### Request

The following example shows the request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
DELETE https://graph.microsoft.com/v1.0/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Communications.Calls["{call-id}"].DeleteAsync();
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
graphClient.Communications().Calls().ByCallId("call-id").Delete(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.communications().calls().byCallId("{call-id}").delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896')
	.delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->communications()->calls()->byCallId('call-id')->delete()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

Remove-MgCommunicationCall -CallId $callId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.communications.calls.by_call_id('call-id').delete()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
```

### Notification - terminating

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
      "changeType": "updated",
      "resourceUrl": "/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896",
      "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "state": "terminating"
      }
    }
  ]
}
  
```

### Notification - terminated

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
      "resourceUrl": "/communications/calls/57dab8b1-894c-409a-b240-bd8beae78896",
      "resourceData": {
        "@odata.type": "#microsoft.graph.call",
        "state": "terminated",
        "resultInfo": {
          "@odata.type": "#microsoft.graph.resultInfo",
          "code": "200",
          "subcode": "5001",
          "message": "The conversation has ended."
        }
      }
    }
  ]
}
```

#### Call end reason codes

These are some of the common error codes received via notification when call is terminated.

| Code | Sub-code | Termination reason |
| :--- | :--- | :--- |
| 200 | 4097 | Call ended by the other participant in the call. |
| 200 | 4521 | Call ended by the other participant in peer-to-peer call. |
| 200 | 5000 | Removed from the conversation by another participant. |
| 200 | 5001 | The conversation has ended. |
| 200 | 5002 | The conversation has ended as all other participants have left the call. |
| 200 | 5003 | The conversation has ended. |
| 200 | 5007 | The conversation has ended as the initiator of the group call left the conversation. |
| 200 | 5010 | The conversation has ended as only one participant remained in the conversation. |
| 200 | 5012 | The conversation has ended as there are no participants in the incoming roster. |
| 200 | 5013 | The conversation has ended as no one else has joined the group call. |
| 200 | 5014 | The conversation has ended because we were unable to determine a potential host for the group call. |
| 200 | 5020 | The conversation has ended as there are no non-hidden participants in the incoming roster. |
| 200 | 5030 | The conversation has ended as the breakout room duration has elapsed. |
| 200 | 5300 | Participant was removed from the conversation by another participant. |
| 200 | 5855 | Participant waiting in lobby was removed from the conversation after lobby inactivity timeout. |
| 200 | 7000 | The conversation has ended by bot. |
| 200 | 7015 | Call ended as the transfer completed successfully. |
| 200 | 10550 | The conversation has ended by bot. |
| 200 | 18503 | The other participant in the peer-to-peer call left the conversation. |
| 200 | 540000/560000 | Call ended by the PSTN User. |
| 408 | 8537 | Keep Alive timeout, cleaned up inactive call. |
| 408 | 1106 | An acknowledgment wasn't received for the call acceptance in the allotted time. |
| 408 | 10057 | Call timed out due to no signaling from callee endpoints. |
| 410 | 301005 | Media connectivity failure. |
| 480 | 10037 | No callee endpoints were found. |
| 480 | 10076 | Callee couldn't be reached. |
| 480 | 10134 | Call rejected due to inability to route the call. |
| 480 | 10199 | Call rejected as private calling is disabled for the user. |
| 500 | 1005 | Server encountered connectivity error with Bot's media. Check media connectivity between Bot and Microsoft. |
