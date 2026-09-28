<!-- Source: https://learn.microsoft.com/en-us/graph/change-notifications-delivery-webhooks -->
<!-- Sitemap-Last-Modified: 2026-04-22 -->

# Receive change notifications through webhooks

A webhook is an HTTP-based user-defined callback API that you can set up in your infrastructure to receive change notifications and events from a service, such as Microsoft Graph. To use webhooks, you need to define a publicly accessible HTTPS-secured endpoint that receives the notifications.

You can create a subscription to the resource for which you want to be notified of changes. While the subscription is valid, Microsoft Graph sends a notification to your endpoint whenever it detects a change in the resource.

The article guides you through the process of implementing your webhook endpoint, subscribing to and managing Microsoft Graph subscriptions, and how to receive change notifications through webhooks.

For details about how to create change notifications, see [Microsoft Graph API change notifications](https://learn.microsoft.com/en-us/graph/api/resources/change-notifications-api-overview).

## Considerations for a webhook endpoint

Before you can receive a notification via webhooks, you must create a publicly accessible, HTTPS-secured endpoint that is addressable via URL. If your endpoint isn't publicly accessible, Microsoft Graph doesn't send notifications to your endpoint.

Your endpoint must provide correct, consistent, and timely HTTP responses in order to reliably receive notifications. If an endpoint doesn't respond in a timely manner, the change notification service might begin to drop notifications. Dropped notifications can't be recovered.

Your endpoint must also continue to remain authenticated to Microsoft Graph, either by continually renewing your subscription or by responding to lifecycle notifications.

### HTTP codes and retry logic

Once the Microsoft Graph change notifications service receives a 2xx HTTP response from your endpoint within 3 seconds, the notification is considered delivered. If the service receives a non-2xx HTTP response within that 3-second window, or if the request times out because no HTTP response is received within that window, it continues to retry delivery for up to 4 hours. For notifications that are retried, the request timeout is extended to 10 seconds.

- If your endpoint is able to process the notification within the 3-second window, it should return a `200 OK` status code to Microsoft Graph.
- Otherwise, we recommend to validate and persist the notification in a queue on your endpoint and return `202 Accepted` status code within the 3-second window.
- If the notification isn't processed or queued, return a `5xx` class code to indicate an error so that Microsoft Graph can retry the notification.

Notifications that fail to deliver are retried at exponential backoff intervals. Missed notifications might take up to 4 hours to resend once your endpoint comes online.

### Throttling

For security and performance reasons, Microsoft Graph throttles notifications sent to endpoints that become slow or unresponsive. It might include dropping notifications in a way that they can't be recovered.

1. An endpoint is marked "slow" once more than 10% of responses take longer than the 3-second timeout allowance in a 10-minute window.

   - Once an endpoint is marked "slow", any new notifications are sent on after a 10-minute delay.
   - Every 10 minutes the process tries to evaluate with a small number of notifications if the percentage of timeouts is under 10% and if so, it exits the slow state.

2. An endpoint is marked "drop" once more than 15% of responses take longer than the 10-second retry timeout allowance in a 10-minute window.

   - Once an endpoint is marked "drop", notifications are dropped for a 10-minute window.
   - After the 10-minute period ends, the process periodically sends a small number of notifications. The endpoint exits the "drop" state when less than 15% of responses take longer than the 10-second timeout window.

If your endpoint is unable to meet these performance characteristics, consider using [Event Hubs](https://learn.microsoft.com/en-us/graph/change-notifications-delivery-event-hubs) or [Event Grid](https://learn.microsoft.com/en-us/azure/event-grid/subscribe-to-graph-api-events?context=graph/context) as a target for receiving notifications.

### Authentication

When you create your subscription, an access token is sent to your endpoint. This access token is used only to check the validity of your endpoint and has a lifecycle different from your change notification subscription. This access token generally expires within 1 hour.

To ensure uninterrupted notifications, your endpoint must be prepared for regular reauthorization by Microsoft Graph.

If an access token expires, notifications aren't delivered. However, it doesn't trigger endpoint throttling behavior and Microsoft Graph continues to retry sending each notification for up to 4 hours. So if the access token is refreshed within 4 hours of expiration, unsent notifications are delivered.

We recommend that you add [lifecycle notifications](https://learn.microsoft.com/en-us/graph/change-notifications-lifecycle-events) to your subscription to receive a warning about token expiration so you can reauthorize your endpoint in a timely manner.

When you [renew your subscription](#renew-a-subscription), your access token is also refreshed.

### Firewall configuration

You can configure the firewall that protects your endpoint to allow inbound connections only from Microsoft Graph, reducing further exposure to invalid change notifications. For a complete list of IP addresses used by Microsoft Graph to deliver change notifications, see [additional endpoints for Microsoft 365](https://learn.microsoft.com/en-us/office365/enterprise/additional-office365-ip-addresses-and-urls).

## Create a subscription

Important

Multiple steps are required to ensure a secure communication channel is established and maintained between the Microsoft Graph change notifications service and your endpoint.

To start receiving Microsoft Graph change notifications, you must create a subscription using the URL of your endpoint \(notification URL\) to establish the subscription. The pattern of establishing a subscription is as follows:

1. The client app sends a subscription request to subscribe to changes on a specific resource.
2. Microsoft Graph checks the request.

   - If the request is valid, Microsoft Graph sends a validation token to the notification URL for the client app to validate the notification URL.
   - If the request is invalid, Microsoft Graph sends an error response with an error code and details.

3. When the client receives the notification URL validation request, the client responds with the validation token in plain text.
4. Microsoft Graph validates the client's validation token response and if the validation token is valid, responds with a subscription ID.

### Subscription request

The client app sends a **POST** request to the `/subscriptions` endpoint. The following example shows a basic request to subscribe to changes to a specific mail folder on behalf of the signed-in user. For more information about other Microsoft Graph resources that support change notifications, see [supported resources](https://learn.microsoft.com/en-us/graph/change-notifications-overview#supported-resources).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/subscriptions
Content-Type: application/json

{
  "changeType": "created,updated",
  "notificationUrl": "https://webhook.azurewebsites.net/notificationClient",
  "lifecycleNotificationUrl": "https://webhook.azurewebsites.net/api/lifecycleNotifications",
  "resource": "/me/mailfolders('inbox')/messages",
  "expirationDateTime": "2016-03-20T11:00:00.0000000Z",
  "clientState": "SecretClientState"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Subscription
{
	ChangeType = "created,updated",
	NotificationUrl = "https://webhook.azurewebsites.net/notificationClient",
	LifecycleNotificationUrl = "https://webhook.azurewebsites.net/api/lifecycleNotifications",
	Resource = "/me/mailfolders('inbox')/messages",
	ExpirationDateTime = DateTimeOffset.Parse("2016-03-20T11:00:00.0000000Z"),
	ClientState = "SecretClientState",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Subscriptions.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewSubscription()
changeType := "created,updated"
requestBody.SetChangeType(&changeType) 
notificationUrl := "https://webhook.azurewebsites.net/notificationClient"
requestBody.SetNotificationUrl(&notificationUrl) 
lifecycleNotificationUrl := "https://webhook.azurewebsites.net/api/lifecycleNotifications"
requestBody.SetLifecycleNotificationUrl(&lifecycleNotificationUrl) 
resource := "/me/mailfolders('inbox')/messages"
requestBody.SetResource(&resource) 
expirationDateTime , err := time.Parse(time.RFC3339, "2016-03-20T11:00:00.0000000Z")
requestBody.SetExpirationDateTime(&expirationDateTime) 
clientState := "SecretClientState"
requestBody.SetClientState(&clientState) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
subscriptions, err := graphClient.Subscriptions().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Subscription subscription = new Subscription();
subscription.setChangeType("created,updated");
subscription.setNotificationUrl("https://webhook.azurewebsites.net/notificationClient");
subscription.setLifecycleNotificationUrl("https://webhook.azurewebsites.net/api/lifecycleNotifications");
subscription.setResource("/me/mailfolders('inbox')/messages");
OffsetDateTime expirationDateTime = OffsetDateTime.parse("2016-03-20T11:00:00.0000000Z");
subscription.setExpirationDateTime(expirationDateTime);
subscription.setClientState("SecretClientState");
Subscription result = graphClient.subscriptions().post(subscription);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const subscription = {
  changeType: 'created,updated',
  notificationUrl: 'https://webhook.azurewebsites.net/notificationClient',
  lifecycleNotificationUrl: 'https://webhook.azurewebsites.net/api/lifecycleNotifications',
  resource: '/me/mailfolders(\'inbox\')/messages',
  expirationDateTime: '2016-03-20T11:00:00.0000000Z',
  clientState: 'SecretClientState'
};

await client.api('/subscriptions')
	.post(subscription);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Subscription;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Subscription();
$requestBody->setChangeType('created,updated');
$requestBody->setNotificationUrl('https://webhook.azurewebsites.net/notificationClient');
$requestBody->setLifecycleNotificationUrl('https://webhook.azurewebsites.net/api/lifecycleNotifications');
$requestBody->setResource('/me/mailfolders(\'inbox\')/messages');
$requestBody->setExpirationDateTime(new \DateTime('2016-03-20T11:00:00.0000000Z'));
$requestBody->setClientState('SecretClientState');

$result = $graphServiceClient->subscriptions()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.ChangeNotifications

$params = @{
	changeType = "created,updated"
	notificationUrl = "https://webhook.azurewebsites.net/notificationClient"
	lifecycleNotificationUrl = "https://webhook.azurewebsites.net/api/lifecycleNotifications"
	resource = "/me/mailfolders('inbox')/messages"
	expirationDateTime = [System.DateTime]::Parse("2016-03-20T11:00:00.0000000Z")
	clientState = "SecretClientState"
}

New-MgSubscription -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.subscription import Subscription
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Subscription(
	change_type = "created,updated",
	notification_url = "https://webhook.azurewebsites.net/notificationClient",
	lifecycle_notification_url = "https://webhook.azurewebsites.net/api/lifecycleNotifications",
	resource = "/me/mailfolders('inbox')/messages",
	expiration_date_time = "2016-03-20T11:00:00.0000000Z",
	client_state = "SecretClientState",
)

result = await graph_client.subscriptions.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The **clientState** property is required. Setting the property allows your service to confirm that change notifications you receive originate from Microsoft Graph. For this reason, the value of the property should remain secret and known only to your application and the Microsoft Graph service.

If successful, Microsoft Graph returns a `201 Created` code and a [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription) object in the body.

Each subscription has a unique **subscriptionId**, even if you have multiple subscriptions that monitor the same resource and use the same notification URL.

Note

Any query string parameter included in the **notificationUrl** property is included in the HTTP POST request when notifications are being delivered to your service.

Duplicate subscriptions aren't allowed. When a subscription request contains the same values for **changeType** and **resource** as an existing subscription, the request fails with an HTTP error code `409 Conflict`, and the error message `Subscription Id <> already exists for the requested combination`.

#### notificationUrl validation

When you send a request to create a subscription to get change notifications through webhooks, the subscription service checks if the **notificationUrl** property in your subscription request is valid. The validation process works as follows:

Note

If you're subscribing to [lifecycle notifications](https://learn.microsoft.com/en-us/graph/change-notifications-lifecycle-events) as well, the subscription service also validates the **lifecycleNotificationUrl**.

1. When a subscription is requested, Microsoft Graph encodes a validation token and includes it in a POST request to the notification URL as follows.

   ```http
   Content-Type: text/plain; charset=utf-8
   POST https://{notificationUrl}?validationToken={opaqueTokenCreatedByMicrosoftGraph}
   ```

2. The client must properly decode the URL to get the plain text validation token from Microsoft Graph.

   Escaping any HTML or JavaScript is a good practice because malicious actors can use the notification endpoint for cross-site scripting type of attacks. Microsoft Graph never sends any value containing HTML or JavaScript code.

   In general, treat the validation token value as opaque, as the token format can change without notice.
3. The client must respond with the following characteristics within 10 seconds of step 1:

   - A status code of `HTTP 200 OK`.
   - A content type of `text/plain`.
   - A body that includes the *URL decoded* plain text validation token.


   Important


   The validation token must be returned in plain text. If the client returns an encoded validation token, the validation fails.

4. If the endpoint validation fails, Microsoft Graph doesn't create the subscription.

## Receive notifications

While the subscription is valid and there are changes to the resource that you subscribed to, Microsoft Graph sends a `POST` request to the **notificationUrl** with details of the changes. This payload is the **change notification**.

For most subscriptions, Microsoft Graph doesn't delay sending notifications but [delivers all notifications within the SLA unless the service is experiencing an incident](https://learn.microsoft.com/en-us/graph/change-notifications-overview#latency).

A change notification payload sent to your endpoint can contain a collection of change notifications relating to your subscriptions.

### Change notification example

When the user receives an email, Microsoft Graph sends a change notification object to the client app as shown in the following example. See [changeNotificationCollection](https://learn.microsoft.com/en-us/graph/api/resources/changenotificationcollection) and the related [changeNotification](https://learn.microsoft.com/en-us/graph/api/resources/changenotification) for details of the notification payload.

When many changes occur, Microsoft Graph might send multiple notifications that correspond to different subscriptions in the same `POST` request.

```json
{
  "value": [
    {
      "id": "lsgTZMr9KwAAA",
      "subscriptionId":"{subscription_guid}",
      "subscriptionExpirationDateTime":"2016-03-19T22:11:09.952Z",
      "clientState":"secretClientValue",
      "changeType":"created",
      "resource":"users/{user_guid}@{tenant_guid}/messages/{long_id_string}",
      "tenantId": "84bd8158-6d4d-4958-8b9f-9d6445542f95",
      "resourceData":
      {
        "@odata.type":"#Microsoft.Graph.Message",
        "@odata.id":"Users/{user_guid}@{tenant_guid}/Messages/{long_id_string}",
        "@odata.etag":"W/\"CQAAABYAAADkrWGo7bouTKlsgTZMr9KwAAAUWRHf\"",
        "id":"{long_id_string}"
      }
    }
  ]
}
```

### Processing the change notification

When you receive a change notification:

1. Validate the **clientState** property. It must match the value originally submitted with the subscription creation request.

   If there's a mismatch, don't consider the change notification as valid. It's possible that the change notification isn't originated from Microsoft Graph and might have been sent by a rogue actor. You should also investigate where the change notification comes from and take appropriate action.
2. Update your client app based on your business logic.

## Subscription lifecycle

When they're no longer needed, subscriptions might be deleted or expire. When you create your subscription, you set an expiration date using the **expirationDateTime** property. Once this time passes, Microsoft Graph deletes the subscription and doesn't send notifications to your endpoint. You might also explicitly delete your subscription.

The simplest way to continue receiving notifications is to continue renewing your subscription request. Each notification includes a **subscriptionExpirationDateTime** property. You can use it to guide you when to renew your subscription.

Each subscription also includes an access token granted to the endpoint. The expiration time of this access token might occur before the subscription expiration. You can manage access token expiration using lifecycle notifications for your subscription.

### Renew a subscription

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/subscriptions/{id}
Content-Type: application/json

{
  "expirationDateTime": "2016-03-22T11:00:00.0000000Z"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Subscription
{
	ExpirationDateTime = DateTimeOffset.Parse("2016-03-22T11:00:00.0000000Z"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Subscriptions["{subscription-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewSubscription()
expirationDateTime , err := time.Parse(time.RFC3339, "2016-03-22T11:00:00.0000000Z")
requestBody.SetExpirationDateTime(&expirationDateTime) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
subscriptions, err := graphClient.Subscriptions().BySubscriptionId("subscription-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Subscription subscription = new Subscription();
OffsetDateTime expirationDateTime = OffsetDateTime.parse("2016-03-22T11:00:00.0000000Z");
subscription.setExpirationDateTime(expirationDateTime);
Subscription result = graphClient.subscriptions().bySubscriptionId("{subscription-id}").patch(subscription);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const subscription = {
  expirationDateTime: '2016-03-22T11:00:00.0000000Z'
};

await client.api('/subscriptions/{id}')
	.update(subscription);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Subscription;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Subscription();
$requestBody->setExpirationDateTime(new \DateTime('2016-03-22T11:00:00.0000000Z'));

$result = $graphServiceClient->subscriptions()->bySubscriptionId('subscription-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.ChangeNotifications

$params = @{
	expirationDateTime = [System.DateTime]::Parse("2016-03-22T11:00:00.0000000Z")
}

Update-MgSubscription -SubscriptionId $subscriptionId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.subscription import Subscription
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Subscription(
	expiration_date_time = "2016-03-22T11:00:00.0000000Z",
)

result = await graph_client.subscriptions.by_subscription_id('subscription-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

If the subscription renewal request is successful, Microsoft Graph returns a `200 OK` response code and a [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription) object in the response body. The subscription object includes the new **expirationDateTime** value.

### Delete a subscription

If the client app no longer wants change notifications, it can delete the subscription using its **subscriptionId** as follows:

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
DELETE https://graph.microsoft.com/v1.0/subscriptions/{id}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Subscriptions["{subscription-id}"].DeleteAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Subscriptions().BySubscriptionId("subscription-id").Delete(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.subscriptions().bySubscriptionId("{subscription-id}").delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/subscriptions/{id}')
	.delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->subscriptions()->bySubscriptionId('subscription-id')->delete()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.ChangeNotifications

Remove-MgSubscription -SubscriptionId $subscriptionId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.subscriptions.by_subscription_id('subscription-id').delete()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

If successful, Microsoft Graph returns a `204 No Content` code.

### Lifecycle notifications for your subscription

For increased flexibility and reliability, when you create a subscription, you might also subscribe to the lifecycle notifications for that subscription by providing a **lifecycleNotificationUrl** endpoint that receives, processes, and responds to lifecycle notifications.

When you subscribe to lifecycle notifications, Microsoft Graph alerts you:

- When the access token is about to expire.
- When a subscription is about to expire.
- When a tenant administrator revokes your app's permissions to read a resource.

Note

If an access token expires, notifications aren't delivered to the endpoint. But Microsoft Graph continues to retry sending each notification for up to 4 hours. So if the access token is refreshed within 4 hours of expiration, unsent notifications are delivered.

For more information on how to utilize lifecycle notifications for your subscription, see [lifecycle notifications](https://learn.microsoft.com/en-us/graph/change-notifications-lifecycle-events).

## Summary

In this article, you learned how to receive change notifications through webhooks.

1. Create a subscription by sending a POST request to the `/subscriptions` endpoint.
2. Microsoft Graph validates the webhook notification endpoint before it completes the subscription creation process. A unique **subscriptionID** is linked to the subscription.
3. As long as the subscription is still valid and changes occur to the subscribed resource, Microsoft Graph sends change notifications to the **notificationUrl** endpoint.
4. Regularly renew the subscription to maintain its validity and continue receiving updates on the subscribed changes.

## Related content

- [subscription resource type](https://learn.microsoft.com/en-us/graph/api/resources/subscription)
- [changeNotificationCollection](https://learn.microsoft.com/en-us/graph/api/resources/changenotificationcollection) resource type
- [Lifecycle notifications](https://learn.microsoft.com/en-us/graph/change-notifications-lifecycle-events)
