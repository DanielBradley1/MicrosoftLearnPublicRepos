<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudcommunications-getpresencesbyuserid?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# cloudCommunications: getPresencesByUserId

Namespace: microsoft.graph

Get the [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence?view=graph-rest-1.0) information for multiple users.

> **Note:** This API allows users to subscribe only to another user's presence. If an application wants to subscribe to presence information for all users, it uses fictitious users to create the subscription to collect the required data.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Presence.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Presence.Read.All | Presence.ReadWrite.All |

> **Note:**
> 
> - Maximum of 650 user IDs are supported per API request.
> - The maximum request rate of this API is 1500 API requests in a 30 second period, per application per tenant.

## HTTP Request

```http
POST /communications/getPresencesByUserId
```

## Request Headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameter.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| ids | String collection | The user object IDs. |

## Response

If successful, this method returns a `200 OK` response code and a collection of [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence?view=graph-rest-1.0) objects in the response body.

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
POST https://graph.microsoft.com/v1.0/communications/getPresencesByUserId
Content-Type: application/json

{
	"ids": ["fa8bf3dc-eca7-46b7-bad1-db199b62afc3", "66825e03-7ef5-42da-9069-724602c31f6b"]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Communications.GetPresencesByUserId;

var requestBody = new GetPresencesByUserIdPostRequestBody
{
	Ids = new List<string>
	{
		"fa8bf3dc-eca7-46b7-bad1-db199b62afc3",
		"66825e03-7ef5-42da-9069-724602c31f6b",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Communications.GetPresencesByUserId.PostAsGetPresencesByUserIdPostResponseAsync(requestBody);
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

requestBody := graphcommunications.NewGetPresencesByUserIdPostRequestBody()
ids := []string {
	"fa8bf3dc-eca7-46b7-bad1-db199b62afc3",
	"66825e03-7ef5-42da-9069-724602c31f6b",
}
requestBody.SetIds(ids)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
getPresencesByUserId, err := graphClient.Communications().GetPresencesByUserId().PostAsGetPresencesByUserIdPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.communications.getpresencesbyuserid.GetPresencesByUserIdPostRequestBody getPresencesByUserIdPostRequestBody = new com.microsoft.graph.communications.getpresencesbyuserid.GetPresencesByUserIdPostRequestBody();
LinkedList<String> ids = new LinkedList<String>();
ids.add("fa8bf3dc-eca7-46b7-bad1-db199b62afc3");
ids.add("66825e03-7ef5-42da-9069-724602c31f6b");
getPresencesByUserIdPostRequestBody.setIds(ids);
var result = graphClient.communications().getPresencesByUserId().post(getPresencesByUserIdPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const presence = {
	ids: ['fa8bf3dc-eca7-46b7-bad1-db199b62afc3', '66825e03-7ef5-42da-9069-724602c31f6b']
};

await client.api('/communications/getPresencesByUserId')
	.post(presence);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Communications\GetPresencesByUserId\GetPresencesByUserIdPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetPresencesByUserIdPostRequestBody();
$requestBody->setIds(['fa8bf3dc-eca7-46b7-bad1-db199b62afc3', '66825e03-7ef5-42da-9069-724602c31f6b', 	]);

$result = $graphServiceClient->communications()->getPresencesByUserId()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	ids = @(
	"fa8bf3dc-eca7-46b7-bad1-db199b62afc3"
"66825e03-7ef5-42da-9069-724602c31f6b"
)
}

Get-MgCommunicationPresenceByUserId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.communications.get_presences_by_user_id.get_presences_by_user_id_post_request_body import GetPresencesByUserIdPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetPresencesByUserIdPostRequestBody(
	ids = [
		"fa8bf3dc-eca7-46b7-bad1-db199b62afc3",
		"66825e03-7ef5-42da-9069-724602c31f6b",
	],
)

result = await graph_client.communications.get_presences_by_user_id.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response objects might be shortened for readability. All the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1574

{
  "value": [
    {
      "id": "fa8bf3dc-eca7-46b7-bad1-db199b62afc3",
      "availability": "Busy",
      "activity": "InAMeeting",
      "outOfOfficeSettings": {
        "message": null,
        "isOutOfOffice": false
      }
    },
    {
      "id": "66825e03-7ef5-42da-9069-724602c31f6b",
      "availability": "Away",
      "activity": "Away",
      "outOfOfficeSettings": {
        "message": null,
        "isOutOfOffice": false
      }
    }
  ]
}
```

## Related content

[Get change notifications for presence updates in Microsoft Teams](https://learn.microsoft.com/en-us/graph/changenotifications-for-presence).
