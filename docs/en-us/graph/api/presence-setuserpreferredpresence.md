<!-- Source: https://learn.microsoft.com/en-us/graph/api/presence-setuserpreferredpresence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# presence: setUserPreferredPresence

Namespace: microsoft.graph

Set the preferred availability and activity status for a user. If the preferred presence of a user is set, the user's presence shows as the preferred status.

Preferred presence takes effect only when at least one [presence session](https://learn.microsoft.com/en-us/graph/cloud-communications-manage-presence-state#presence-sessions) exists for the user. Otherwise, the user's presence shows as `Offline`.

A presence session is created as a result of a successful [setPresence](https://learn.microsoft.com/en-us/graph/api/presence-setpresence?view=graph-rest-1.0) operation, or if the user is signed in on a Microsoft Teams client.

For more details, see [presence sessions](https://learn.microsoft.com/en-us/graph/cloud-communications-manage-presence-state#presence-sessions) and [time-out and expiration](https://learn.microsoft.com/en-us/graph/cloud-communications-manage-presence-state#timeout-expiration-and-keep-alive).

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

## HTTP request

```http
POST /users/{id}/presence/setUserPreferredPresence
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
| activity | String | The supplemental information to availability. |
| availability | String | The base presence information. |
| expirationDuration | Duration | The expiration of the app presence session represented in ISO 8601 format for durations.  <br>If not provided, a default expiration will be applied:  <br>- `DoNotDisturb` or `Busy`: Expiration in 1 day  <br>- All others: Expiration in 7 days |

The following table lists supported combinations of **availability** and **activity**.

| availability | activity | Description |
| :--- | :--- | :--- |
| Available | Available | Set the user preferred presence as `Available`. |
| Busy | Busy | Set the user preferred presence as `Busy`. |
| DoNotDisturb | DoNotDisturb | Set the user preferred presence as `DoNotDisturb`. |
| BeRightBack | BeRightBack | Set the user preferred presence as `BeRightBack`. |
| Away | Away | Set the user preferred presence as `Away`. |
| Offline | OffWork | Set the user preferred presence as `Offline`. |

## Response

If successful, this method returns a `200 OK` response code.

## Examples

### Request

The following example shows a request that sets the preferred presence as `DoNotDisturb` for a user, with an expiration of 8 hours.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
POST https://graph.microsoft.com/v1.0/users/fa8bf3dc-eca7-46b7-bad1-db199b62afc3/presence/setUserPreferredPresence
Content-Type: application/json

{
  "availability": "DoNotDisturb",
  "activity": "DoNotDisturb",
  "expirationDuration": "PT8H"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Users.Item.Presence.SetUserPreferredPresence;

var requestBody = new SetUserPreferredPresencePostRequestBody
{
	Availability = "DoNotDisturb",
	Activity = "DoNotDisturb",
	ExpirationDuration = TimeSpan.Parse("PT8H"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users["{user-id}"].Presence.SetUserPreferredPresence.PostAsync(requestBody);
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

requestBody := graphusers.NewSetUserPreferredPresencePostRequestBody()
availability := "DoNotDisturb"
requestBody.SetAvailability(&availability) 
activity := "DoNotDisturb"
requestBody.SetActivity(&activity) 
expirationDuration , err := abstractions.ParseISODuration("PT8H")
requestBody.SetExpirationDuration(&expirationDuration) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Users().ByUserId("user-id").Presence().SetUserPreferredPresence().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.presence.setuserpreferredpresence.SetUserPreferredPresencePostRequestBody setUserPreferredPresencePostRequestBody = new com.microsoft.graph.users.item.presence.setuserpreferredpresence.SetUserPreferredPresencePostRequestBody();
setUserPreferredPresencePostRequestBody.setAvailability("DoNotDisturb");
setUserPreferredPresencePostRequestBody.setActivity("DoNotDisturb");
PeriodAndDuration expirationDuration = PeriodAndDuration.ofDuration(Duration.parse("PT8H"));
setUserPreferredPresencePostRequestBody.setExpirationDuration(expirationDuration);
graphClient.users().byUserId("{user-id}").presence().setUserPreferredPresence().post(setUserPreferredPresencePostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const setUserPreferredPresence = {
  availability: 'DoNotDisturb',
  activity: 'DoNotDisturb',
  expirationDuration: 'PT8H'
};

await client.api('/users/fa8bf3dc-eca7-46b7-bad1-db199b62afc3/presence/setUserPreferredPresence')
	.post(setUserPreferredPresence);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Presence\SetUserPreferredPresence\SetUserPreferredPresencePostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SetUserPreferredPresencePostRequestBody();
$requestBody->setAvailability('DoNotDisturb');
$requestBody->setActivity('DoNotDisturb');
$requestBody->setExpirationDuration(new \DateInterval('PT8H'));

$graphServiceClient->users()->byUserId('user-id')->presence()->setUserPreferredPresence()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.CloudCommunications

$params = @{
	availability = "DoNotDisturb"
	activity = "DoNotDisturb"
	expirationDuration = "PT8H"
}

Set-MgUserPresenceUserPreferredPresence -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.presence.set_user_preferred_presence.set_user_preferred_presence_post_request_body import SetUserPreferredPresencePostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SetUserPreferredPresencePostRequestBody(
	availability = "DoNotDisturb",
	activity = "DoNotDisturb",
	expiration_duration = "PT8H",
)

await graph_client.users.by_user_id('user-id').presence.set_user_preferred_presence.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```
