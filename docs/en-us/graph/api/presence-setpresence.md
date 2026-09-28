<!-- Source: https://learn.microsoft.com/en-us/graph/api/presence-setpresence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# presence: setPresence

Namespace: microsoft.graph

Set the state of a user's presence session as an application.

For more information about presence sessions, states permutations, and timeouts, see [Manage presence state using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/cloud-communications-manage-presence-state).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Presence.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Presence.ReadWrite.All | Not available. |

## HTTP Request

```http
POST /users/{id}/presence/setPresence
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| sessionId | string | The ID of the application's presence session. |
| availability | string | The base presence information. |
| activity | string | The supplemental information to availability. |
| expirationDuration | duration | The expiration of the app presence session. The value is represented in [ISO 8601 format for durations](http://en.wikipedia.org/wiki/ISO_8601#Durations).<br><br>If not provided, a default expiration of 5 minutes is applied. The valid duration range is from 5 to 240 minutes \(PT5M to PT4H\). |

Important

Provide the ID of the application as `sessionId` in the request.

Supported combinations of `availability` and `activity` are:

| availability | activity | Description |
| :--- | :--- | :--- |
| Available | Available | Updates the presence session as Available. |
| Busy | InACall | Updates the presence session as Busy, InACall. |
| Busy | InAConferenceCall | Updates the presence session as Busy, InAConferenceCall. |
| Away | Away | Updates the presence session as Away. |
| DoNotDisturb | Presenting | Updates the presence session as DoNotDisturb, Presenting. |

## Response

If successful, this method returns a `200 OK` response code.

## Examples

The following request shows the application with ID `22553876-f5ab-4529-bffb-cfe50aa89f87` that sets its presence session for user `fa8bf3dc-eca7-46b7-bad1-db199b62afc3`.

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
POST https://graph.microsoft.com/v1.0/users/fa8bf3dc-eca7-46b7-bad1-db199b62afc3/presence/setPresence
Content-Type: application/json

{
  "sessionId": "22553876-f5ab-4529-bffb-cfe50aa89f87",
  "availability": "Available",
  "activity": "Available",
  "expirationDuration": "PT1H"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Users.Item.Presence.SetPresence;

var requestBody = new SetPresencePostRequestBody
{
	SessionId = "22553876-f5ab-4529-bffb-cfe50aa89f87",
	Availability = "Available",
	Activity = "Available",
	ExpirationDuration = TimeSpan.Parse("PT1H"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users["{user-id}"].Presence.SetPresence.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

requestBody := graphusers.NewSetPresencePostRequestBody()
sessionId := "22553876-f5ab-4529-bffb-cfe50aa89f87"
requestBody.SetSessionId(&sessionId) 
availability := "Available"
requestBody.SetAvailability(&availability) 
activity := "Available"
requestBody.SetActivity(&activity) 
expirationDuration , err := abstractions.ParseISODuration("PT1H")
requestBody.SetExpirationDuration(&expirationDuration) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Users().ByUserId("user-id").Presence().SetPresence().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.presence.setpresence.SetPresencePostRequestBody setPresencePostRequestBody = new com.microsoft.graph.users.item.presence.setpresence.SetPresencePostRequestBody();
setPresencePostRequestBody.setSessionId("22553876-f5ab-4529-bffb-cfe50aa89f87");
setPresencePostRequestBody.setAvailability("Available");
setPresencePostRequestBody.setActivity("Available");
PeriodAndDuration expirationDuration = PeriodAndDuration.ofDuration(Duration.parse("PT1H"));
setPresencePostRequestBody.setExpirationDuration(expirationDuration);
graphClient.users().byUserId("{user-id}").presence().setPresence().post(setPresencePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const setPresence = {
  sessionId: '22553876-f5ab-4529-bffb-cfe50aa89f87',
  availability: 'Available',
  activity: 'Available',
  expirationDuration: 'PT1H'
};

await client.api('/users/fa8bf3dc-eca7-46b7-bad1-db199b62afc3/presence/setPresence')
	.post(setPresence);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Presence\SetPresence\SetPresencePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SetPresencePostRequestBody();
$requestBody->setSessionId('22553876-f5ab-4529-bffb-cfe50aa89f87');
$requestBody->setAvailability('Available');
$requestBody->setActivity('Available');
$requestBody->setExpirationDuration(new \DateInterval('PT1H'));

$graphServiceClient->users()->byUserId('user-id')->presence()->setPresence()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	sessionId = "22553876-f5ab-4529-bffb-cfe50aa89f87"
	availability = "Available"
	activity = "Available"
	expirationDuration = "PT1H"
}

Set-MgUserPresence -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.presence.set_presence.set_presence_post_request_body import SetPresencePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SetPresencePostRequestBody(
	session_id = "22553876-f5ab-4529-bffb-cfe50aa89f87",
	availability = "Available",
	activity = "Available",
	expiration_duration = "PT1H",
)

await graph_client.users.by_user_id('user-id').presence.set_presence.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

```http
HTTP/1.1 200 OK
```
