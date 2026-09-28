<!-- Source: https://learn.microsoft.com/en-us/graph/change-notifications-lifecycle-events -->
<!-- Sitemap-Last-Modified: 2026-03-24 -->

# Reduce missing subscriptions and change notifications

In the lifetime of a subscription, Microsoft Graph sends special kinds of notifications to your specified **lifecycleNotificationUrl** to signal action required. These notifications are called **lifecycle notifications** and they help you to minimize the risk of missing subscriptions and change notifications.

There are three types of lifecycle notifications:

- **reauthorizationRequired** notifications
- Subscription **removed** notifications
- **missed** notifications

If you ignore these events, it might break the change notification flow; you can handle the events by implementing logic in your app to resume a continuous change notification flow.

This article introduces lifecycle notifications in Microsoft Graph change notifications and provides guidance for handling the notifications.

## Supported resources

While you can provide a **lifecycleNotificationUrl** when creating a subscription on any resource type, lifecycle notifications are currently supported only for the following resource types.

- **reauthorizationRequired** notifications - All resources
- **subscriptionRemoved** notifications - Outlook [message](https://learn.microsoft.com/en-us/graph/api/resources/message), Outlook [event](https://learn.microsoft.com/en-us/graph/api/resources/event), Outlook personal [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact), Teams [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage)
- **missed** notifications - Outlook [message](https://learn.microsoft.com/en-us/graph/api/resources/message), Outlook [event](https://learn.microsoft.com/en-us/graph/api/resources/event), Outlook personal [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact)

## Configure your subscription to receive lifecycle notifications

To receive lifecycle notifications, you must provide a valid **lifecycleNotificationUrl** endpoint when creating the subscription. The following subscription creation request defines both the **notificationUrl** and **lifecycleNotificationUrl** endpoints.

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
  "notificationUrl": "https://webhook.azurewebsites.net/api/resourceNotifications",
  "lifecycleNotificationUrl": "https://webhook.azurewebsites.net/api/lifecycleNotifications",
  "resource": "/users/{id}/messages",
  "expirationDateTime": "2020-03-20T11:00:00.0000000Z",
  "clientState": "<secretClientState>"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Subscription
{
	ChangeType = "created,updated",
	NotificationUrl = "https://webhook.azurewebsites.net/api/resourceNotifications",
	LifecycleNotificationUrl = "https://webhook.azurewebsites.net/api/lifecycleNotifications",
	Resource = "/users/{id}/messages",
	ExpirationDateTime = DateTimeOffset.Parse("2020-03-20T11:00:00.0000000Z"),
	ClientState = "<secretClientState>",
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
notificationUrl := "https://webhook.azurewebsites.net/api/resourceNotifications"
requestBody.SetNotificationUrl(&notificationUrl) 
lifecycleNotificationUrl := "https://webhook.azurewebsites.net/api/lifecycleNotifications"
requestBody.SetLifecycleNotificationUrl(&lifecycleNotificationUrl) 
resource := "/users/{id}/messages"
requestBody.SetResource(&resource) 
expirationDateTime , err := time.Parse(time.RFC3339, "2020-03-20T11:00:00.0000000Z")
requestBody.SetExpirationDateTime(&expirationDateTime) 
clientState := "<secretClientState>"
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
subscription.setNotificationUrl("https://webhook.azurewebsites.net/api/resourceNotifications");
subscription.setLifecycleNotificationUrl("https://webhook.azurewebsites.net/api/lifecycleNotifications");
subscription.setResource("/users/{id}/messages");
OffsetDateTime expirationDateTime = OffsetDateTime.parse("2020-03-20T11:00:00.0000000Z");
subscription.setExpirationDateTime(expirationDateTime);
subscription.setClientState("<secretClientState>");
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
  notificationUrl: 'https://webhook.azurewebsites.net/api/resourceNotifications',
  lifecycleNotificationUrl: 'https://webhook.azurewebsites.net/api/lifecycleNotifications',
  resource: '/users/{id}/messages',
  expirationDateTime: '2020-03-20T11:00:00.0000000Z',
  clientState: '<secretClientState>'
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
$requestBody->setNotificationUrl('https://webhook.azurewebsites.net/api/resourceNotifications');
$requestBody->setLifecycleNotificationUrl('https://webhook.azurewebsites.net/api/lifecycleNotifications');
$requestBody->setResource('/users/{id}/messages');
$requestBody->setExpirationDateTime(new \DateTime('2020-03-20T11:00:00.0000000Z'));
$requestBody->setClientState('<secretClientState>');

$result = $graphServiceClient->subscriptions()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.ChangeNotifications

$params = @{
	changeType = "created,updated"
	notificationUrl = "https://webhook.azurewebsites.net/api/resourceNotifications"
	lifecycleNotificationUrl = "https://webhook.azurewebsites.net/api/lifecycleNotifications"
	resource = "/users/{id}/messages"
	expirationDateTime = [System.DateTime]::Parse("2020-03-20T11:00:00.0000000Z")
	clientState = "<secretClientState>"
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
	notification_url = "https://webhook.azurewebsites.net/api/resourceNotifications",
	lifecycle_notification_url = "https://webhook.azurewebsites.net/api/lifecycleNotifications",
	resource = "/users/{id}/messages",
	expiration_date_time = "2020-03-20T11:00:00.0000000Z",
	client_state = "<secretClientState>",
)

result = await graph_client.subscriptions.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

The **lifecycleNotificationUrl** endpoint can be the same as the **notificationUrl**.

Existing subscriptions without a **lifecycleNotificationUrl** property don't receive the lifecycle notifications. You also can't add the **lifecycleNotificationUrl** property to an existing subscription by updating the subscription. To add the **lifecycleNotificationUrl** property, you must delete the existing subscription and create a new subscription while specifying the property during subscription creation.

When using the webhooks delivery channel, you must [validate both **lifecycleNotificationUrl** and **notificationUrl** endpoints](https://learn.microsoft.com/en-us/graph/change-notifications-delivery-webhooks#notificationurl-validation).

## Structure of a lifecycle notification

A lifecycle notification payload follows the structure of the [changeNotificationCollection](https://learn.microsoft.com/en-us/graph/api/resources/changenotificationcollection) object and the related [changeNotification](https://learn.microsoft.com/en-us/graph/api/resources/changenotification) object as follows:

```json
{
  "value": [
    {
      "subscriptionId":"<subscription_guid>",
      "subscriptionExpirationDateTime":"2019-03-20T11:00:00.0000000Z",
      "tenantId": "<tenant_guid>",
      "clientState":"<secretClientState>",
      "lifecycleEvent": "subscriptionRemoved or missed or reauthorizationRequired"
    }
  ]
}
```

Where the **lifecycleEvent** can be `subscriptionRemoved`, `missed`, or `reauthorizationRequired`, representing the lifecycle notification types.

A lifecycle notification doesn't contain any information about a specific resource, because it isn't related to a resource change, but to the subscription state change. Similar to change notifications, lifecycle notifications can be batched together and received as a collection, each with a possibly different **lifecycleEvent** value. Process each lifecycle notification in the batch accordingly.

When you process the lifecycle notification and resume the flow of change notifications, the change notifications start flowing to the **notificationUrl**.

## reauthorizationRequired notifications

`reauthorizationRequired` lifecycle events alert you when Microsoft Graph requires the app to reauthorize the subscription, for example in the following cases:

- When the access token is about to expire.
- When a [subscription is about to expire](https://learn.microsoft.com/en-us/graph/change-notifications-overview#subscription-lifetime).
- When an administrator has revoked your app's permissions to read a resource.

Before any of these conditions become true, Microsoft Graph sends an authorization challenge to the **lifecycleNotificationUrl**.

The following code sample illustrates how the Microsoft Graph change notifications service can calculate the interval of these notifications.

```csharp
    //The following code is for illustrative purposes only
    var TokenTimeToExpirationInMinutes=(TokenExpirationTime-CurrentTime)/4;

    if((TokenTimeToExpirationInMinutes)<=180 && TokenTimeToExpirationInMinutes>60){
        //Microsoft Graph will send reauthorizationRequired notification
        TokenTimeToExpirationInMinutes=TokenTimeToExpirationInMinutes/2;
    }
    elseif(TokenTimeToExpirationInMinutes<60 && TokenTimeToExpirationInMinutes>=0){
            //Microsoft Graph will send reauthorizationRequired notification every 15 mins
            TokenTimeToExpirationInMinutes=TokenTimeToExpirationInMinutes-15;
    } else {
      //Microsoft Graph will stop sending reauthorizationRequired notifications
    }
```

The following steps represent the flow of an authorization challenge for an active subscription:

1. Microsoft Graph requires a subscription to be reauthorized.

   The reasons might vary from resource to resource and might change over time. To maintain the subscription, you must respond to a reauthorization event no matter what caused it.
2. Microsoft Graph sends an authorization challenge notification to the **lifecycleNotificationUrl**.

   The flow of change notifications might continue for a while, giving you extra time to respond. However, eventually change notification delivery pauses, until you take the required action. Any notifications about resource changes that happen when the change notification delivery pauses and the time when the app successfully creates the subscription again are lost. In such cases, the app should separately fetch those changes, for example using the [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview).

### Responding to reauthorizationRequired notifications

1. Acknowledge receipt of the lifecycle notification by responding to the POST call with `202 - Accepted` response code.
2. Validate the authenticity of the lifecycle notification.
3. Ensure that the app has a valid access token to take the next step.
4. Call *either* of the following two APIs. If the API call succeeds, the change notification flow resumes.

   Important

   Don't issue a reauthorize request \(`POST /subscriptions/{id}/reauthorize`\) and an update request \(`PATCH /subscriptions/{id}`\) for the same subscription within a 10-minute window. Sending these requests concurrently or in rapid succession can result in subscription state inconsistencies. To reauthorize and renew a subscription in the same request, use a single `PATCH /subscriptions/{id}` request with an updated **expirationDateTime**, which performs both actions in one operation.

   - Call the `/reauthorize` action to reauthorize the subscription without extending its expiration date.

     ```http
     POST  https://graph.microsoft.com/v1.0/subscriptions/{id}/reauthorize
     ```

   - Perform the update operation to reauthorize *and* renew the subscription at the same time.

     ```http
     PATCH https://graph.microsoft.com/v1.0/subscriptions/{id}
     Content-Type: application/json

     {
        "expirationDateTime": "2019-09-21T11:00:00.0000000Z"
     }
     ```


     Renewing might fail if the app is no longer authorized to access to the resource. It might then be necessary for the app to obtain a new access token to successfully reauthorize a subscription.


     You might retry these actions later, at any time, and succeed if the conditions of access change.

### Additional information

- Authorization challenges don't replace the need to renew a subscription before it expires. The lifecycles of access tokens and subscription expiration aren't the same. Your access token might expire before your subscription. It's important to be prepared to regularly reauthorize your endpoint to refresh your access token. Reauthorizing your endpoint doesn't renew your subscription. However, [renewing your subscription](https://learn.microsoft.com/en-us/graph/api/subscription-update) also reauthorizes your endpoint.
- The frequency of authorization challenges is subject to change.

  Don't assume the frequency of authorization challenges. These lifecycle notifications tell you when to take action, saving you from having to track which subscriptions require reauthorization. Be ready to handle authorization challenges from once every few minutes for every subscription to rarely for some of your subscriptions.

## subscriptionRemoved notifications

`subscriptionRemoved` lifecycle events alert you when Microsoft Graph has removed a subscription. In such cases, if you want to continue receiving change notifications for the related resource, you need to recreate the subscription.

Even if you have a long-lived subscription, the conditions of access to the resource data might change over time. For example, an event in the service might occur that requires the app to reauthenticate the user. In such a case, Microsoft Graph sends you a **subscriptionRemoved** notification.

The following flow shows the flow of a **subscriptionRemoved** event:

1. The service detects that a subscription needs to be removed from Microsoft Graph.

   There's no set cadence for these events. They might occur frequently for some resources, and almost never for others.
2. Microsoft Graph sends a `subscriptionRemoved` lifecycle notification to the **lifecycleNotificationUrl** \(if specified\).

   No lifecycle notifications are available from the period when the `subscriptionRemoved` lifecycle notification was sent to when the app recreates the subscription successfully. The app needs to fetch those changes on its own.

### Responding to subscriptionRemoved notifications

1. Acknowledge receipt of the lifecycle notification by responding to the POST call with `202 - Accepted` response code.
2. Validate the authenticity of the lifecycle notification.
3. Ensure that the app has a valid access token to take the next step.
4. Create a new subscription.

   This action might fail, because the authorization checks performed by the system might deny the app access to the resource. It might be necessary for the app to obtain a new access token to successfully reauthorize a subscription. You can retry these actions later, at any time; for example, when the conditions of access change.
5. After creating the new subscription, you can sync the resource data to identify any missed change notifications; for example using the [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview).

## missed notifications

`missed` lifecycle events alert you that some change notifications weren't delivered. For example, because of [throttling](https://learn.microsoft.com/en-us/graph/change-notifications-delivery-webhooks#throttling).

### Responding to missed notifications

1. Acknowledge receipt of the lifecycle notification by responding to the POST call with `202 - Accepted` response code.
2. Validate the authenticity of the lifecycle notification.
3. Perform a full data resync of the resource to identify the changes that weren't delivered as notifications; for example, using the [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview).

## Related content

- [Subscription resource type](https://learn.microsoft.com/en-us/graph/api/resources/subscription)
