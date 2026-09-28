<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# subscription resource type

Namespace: microsoft.graph

Represents a subscription that allows a client app to receive [change notifications](https://learn.microsoft.com/en-us/graph/api/resources/changenotificationcollection?view=graph-rest-1.0) about changes to data in Microsoft Graph.

For more information about subscriptions and change notifications, including resources that support change notifications, see [Set up notifications for changes in resource data](https://learn.microsoft.com/en-us/graph/api/resources/change-notifications-api-overview?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/subscription-list?view=graph-rest-1.0) | [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0) | Lists active subscriptions. |
| [Create](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions?view=graph-rest-1.0) | [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0) | Subscribes a listener application to receive change notifications when Microsoft Graph data changes. When a susbcription is created and valdiated sucessfully, Microsoft Graph sends the app at least one [changeNotificationCollection](https://learn.microsoft.com/en-us/graph/api/resources/changenotificationcollection?view=graph-rest-1.0) object every time there's a change in the subscribed resource. |
| [Get](https://learn.microsoft.com/en-us/graph/api/subscription-get?view=graph-rest-1.0) | [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0) | Reads properties and relationships of subscription object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/subscription-update?view=graph-rest-1.0) | [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0) | Updates a subscription expiration time for renewal and/or updates the notificationUrl for delivery. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/subscription-delete?view=graph-rest-1.0) | None | Deletes a subscription object. |
| [Reauthorize](https://learn.microsoft.com/en-us/graph/api/subscription-reauthorize?view=graph-rest-1.0) | None | Reauthorize a subscription when you receive a **reauthorizationRequired** challenge. |
| [Get VAPID](https://learn.microsoft.com/en-us/graph/api/subscription-getvapidpublickey?view=graph-rest-1.0) | String | Get the Voluntary Application Server Identification \(VAPID\) public key to create a subscription in accordance with [RFC 8292](https://www.rfc-editor.org/rfc/rfc8292.html). |

## Properties

| Property | Type | Description |
| --- | --- | --- |
| applicationId | String | Optional. Identifier of the application used to create the subscription. Read-only. |
| changeType | String | Required. Indicates the type of change in the subscribed resource that raises a change notification. The supported values are: `created`, `updated`, `deleted`. Multiple values can be combined using a comma-separated list.  <br>  <br>**Note:**<br><br><li> Drive root item and list change notifications support only the <code>updated</code> changeType. </li><br><br><li><a href="https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0" data-linktype="relative-path">User</a> and <a href="https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0" data-linktype="relative-path">group</a> change notifications support <code>updated</code> and <code>deleted</code> changeType. Use <code>updated</code> to receive notifications when user or group is created, updated, or soft deleted. Use <code>deleted</code> to receive notifications when user or group is permanently deleted.</li> |
| clientState | String | Optional. Specifies the value of the `clientState` property sent by the service in each change notification. The maximum length is 128 characters. The client can check that the change notification came from the service by comparing the value of the `clientState` property sent with the subscription with the value of the `clientState` property received with each change notification. |
| creatorId | String | Optional. Identifier of the user or service principal that created the subscription. If the app used delegated permissions to create the subscription, this field contains the ID of the signed-in user the app called on behalf of. If the app used application permissions, this field contains the ID of the service principal corresponding to the app. Read-only. |
| encryptionCertificate | String | Optional. A base64-encoded representation of a certificate with a public key used to encrypt resource data in change notifications. Optional but required when **includeResourceData** is `true`. |
| encryptionCertificateId | String | Optional. A custom app-provided identifier to help identify the certificate needed to decrypt resource data. |
| expirationDateTime | DateTimeOffset | Required. Specifies the date and time when the webhook subscription expires. The time is in UTC, and can be an amount of time from subscription creation that varies for the resource subscribed to. Any value under 45 minutes after the time of the request is automatically set to 45 minutes after the request time. For the maximum supported subscription length of time, see [Subscription lifetime](#subscription-lifetime). |
| id | String | Optional. Unique identifier for the subscription. Read-only. |
| includeResourceData | Boolean | Optional. When set to `true`, change notifications [include resource data](https://learn.microsoft.com/en-us/graph/change-notifications-with-resource-data) \(such as content of a chat message\). |
| latestSupportedTlsVersion | String | Optional. Specifies the latest version of Transport Layer Security \(TLS\) that the notification endpoint, specified by **notificationUrl**, supports. The possible values are: `v1_0`, `v1_1`, `v1_2`, `v1_3`.  <br>  <br>For subscribers whose notification endpoint supports a version lower than the currently recommended version \(TLS 1.2\), specifying this property by a set [timeline](https://developer.microsoft.com/graph/blogs/microsoft-graph-subscriptions-deprecating-tls-1-0-and-1-1/) allows them to temporarily use their deprecated version of TLS before completing their upgrade to TLS 1.2. For these subscribers, not setting this property per the timeline would result in subscription operations failing.  <br>  <br>For subscribers whose notification endpoint already supports TLS 1.2, setting this property is optional. In such cases, Microsoft Graph defaults the property to `v1_2`. |
| lifecycleNotificationUrl | String | Required for Teams resources if the `expirationDateTime` value is more than 1 hour from now; optional otherwise. The URL of the endpoint that receives lifecycle notifications, including `subscriptionRemoved`, `reauthorizationRequired`, and `missed` notifications. This URL must make use of the HTTPS protocol. For more information, see [Reduce missing subscriptions and change notifications](https://learn.microsoft.com/en-us/graph/change-notifications-lifecycle-events). |
| notificationQueryOptions | String | Optional. OData query options for specifying value for the targeting resource. Clients receive notifications when resource reaches the state matching the query options provided here. With this new property in the subscription creation payload along with all existing properties, Webhooks deliver notifications whenever a resource reaches the desired state mentioned in the notificationQueryOptions property. For example, when the print job is completed or when a print job resource `isFetchable` property value becomes `true` etc.  <br>  <br>Supported only for Universal Print Service. For more information, see [Subscribe to change notifications from cloud printing APIs using Microsoft Graph](https://learn.microsoft.com/en-us/graph/universal-print-webhook-notifications). |
| notificationUrl | String | Required. The URL of the endpoint that receives the change notifications. This URL must make use of the HTTPS protocol. Any query string parameter included in the notificationUrl property is included in the HTTP POST request when Microsoft Graph sends the change notifications. |
| notificationUrlAppId | String | Optional. The app ID that the subscription service can use to generate the validation token. The value allows the client to validate the authenticity of the notification received. |
| resource | String | Required. Specifies the resource that is monitored for changes. Don't include the base URL \(`https://graph.microsoft.com/v1.0/`\). See the possible resource path [values](https://learn.microsoft.com/en-us/graph/api/resources/change-notifications-api-overview?view=graph-rest-1.0) for each supported resource. |
| vapidPublicKey | String | Optional. The application server's VAPID public key, base64url-encoded \(P-256 uncompressed point, 65 bytes pre-encoding\). Obtained by calling the [getVapidPublicKey](https://learn.microsoft.com/en-us/graph/api/subscription-getvapidpublickey?view=graph-rest-1.0) function on the subscription collection. The browser passes this value to `PushManager.subscribe({ applicationServerKey: vapidPublicKey })` to bind the push subscription to this server identity. Required when **notificationUrl** targets a known Web Push service origin \(for example, `*.push.apple.com`, `fcm.googleapis.com`, `updates.push.services.mozilla.com`\); rejected with `400 Bad Request` if supplied on a standard webhook subscription. For more information, see [RFC 8292](https://www.rfc-editor.org/rfc/rfc8292.html). |
| webPushEncryptionP256dhPublicKey | String | Optional. The subscriber's ECDH public key, base64url-encoded \(P-256 uncompressed point, 65 bytes pre-encoding\). Obtained from the browser via `PushSubscription.getKey('p256dh')`. Used as the peer public key during ECDH key agreement to derive the per-message content encryption key for RFC 8291 payload encryption. Required when **notificationUrl** targets a known Web Push service origin; rejected with `400 Bad Request` if supplied on a standard webhook subscription. For more information, see [RFC 8291 Section 3](https://www.rfc-editor.org/rfc/rfc8291.html#section-3). |
| webPushEncryptionSecret | String | Optional. The subscriber's auth secret, base64url-encoded \(16 bytes pre-encoding\). Obtained from the browser via `PushSubscription.getKey('auth')`. Used as the HMAC-SHA-256 salt for the HKDF combine step that derives key material for RFC 8291 payload encryption. Write-only: this value is never returned in GET responses \(returned as `null`\). Treat as a secret. Required when **notificationUrl** targets a known Web Push service origin; rejected with `400 Bad Request` if supplied on a standard webhook subscription. For more information, see [RFC 8291 Section 3](https://www.rfc-editor.org/rfc/rfc8291.html#section-3). |

### Subscription lifetime

Subscriptions have a limited lifetime. Apps need to renew their subscriptions before the expiration time; otherwise, they need to create a new subscription. Apps can also unsubscribe at any time to stop getting change notifications.

Additionally, any request with expirationDateTime set to under 45 minutes after the time of the request is automatically set to 45 minutes after the request time.

The following table shows the maximum expiration times for subscriptions per resource in Microsoft Graph.

| Resource | Maximum expiration time |
| :--- | :--- |
| Copilot [aiInteraction](https://learn.microsoft.com/en-us/graph/api/resources/aiinteraction) | 4,320 minutes \(three days\) |
| Security [alert](https://learn.microsoft.com/en-us/graph/api/resources/alert) | 43,200 minutes \(under 30 days\) |
| Teams [approvals](https://learn.microsoft.com/en-us/graph/api/resources/approvalItem) | 43,200 minutes \(under 30 days\) |
| Teams [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord) | 4,230 minutes \(under three days\) |
| Teams [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording) | 4,320 minutes \(three days\) |
| Teams [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript) | 4,320 minutes \(three days\) |
| Teams [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel) | 4,320 minutes \(three days\) |
| Teams [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat) | 4,320 minutes \(three days\) |
| Teams [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage) | 4,320 minutes \(three days\) |
| Teams [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember) | 4,320 minutes \(three days\) |
| Teams [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting) | 4,320 minutes \(three days\) |
| Teams [team](https://learn.microsoft.com/en-us/graph/api/resources/team) | 4,320 minutes \(three days\) |
| Teams [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation) | 4,320 minutes \(3 days\) |
| Teams Shifts [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest) | 360 minutes \(6 hours\) |
| Teams Shifts [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest) | 360 minutes \(6 hours\) |
| Teams Shifts [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift) | 360 minutes \(6 hours\) |
| Teams Shifts [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest) | 360 minutes \(6 hours\) |
| Teams Shifts [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest) | 360 minutes \(6 hours\) |
| Group [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation) | 4,230 minutes \(under three days\) |
| OneDrive [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem) | 42,300 minutes \(under 30 days\) |
| SharePoint [list](https://learn.microsoft.com/en-us/graph/api/resources/list) | 42,300 minutes \(under 30 days\) |
| Outlook [message](https://learn.microsoft.com/en-us/graph/api/resources/message), [event](https://learn.microsoft.com/en-us/graph/api/resources/event), [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact) | 10,080 minutes \(under seven days\)  <br>  <br>For subscriptions with resource data \(rich notification subscriptions\), subscription lifetime is 1440 minutes \(under one day\). |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user), [group](https://learn.microsoft.com/en-us/graph/api/resources/group), other directory resources | 41,760 minutes \(under 29 days\) |
| [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting) | 4,230 minutes \(under three days\) |
| [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence) | 60 minutes \(1 hour\) |
| Print [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer) | 4,230 minutes \(under three days\) |
| Print [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition) | 4,230 minutes \(under three days\) |
| [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask) | 4,230 minutes \(under three days\)  <br>  <br>Webhooks for this resource are only available in the global endpoint and not in the national clouds. |
| Microsoft Entra Health Monitoring [alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert) | 42,300 minutes \(under 30 days\) |
| **baseTask** \(deprecated\) | 4,230 minutes \(under three days\) |

> **Note:** Existing applications and new applications should not exceed the supported value. In the future, any requests to create or renew a subscription beyond the maximum value will fail.

### Latency

The following table lists the latency to expect between an event happening in the service and the delivery of the change notification.

| Resource | Average latency | Maximum latency |
| :--- | :--- | :--- |
| [aiInteraction](https://learn.microsoft.com/en-us/graph/api/resources/aiinteraction) | Less than 10 seconds | 60 minutes |
| [alert](https://learn.microsoft.com/en-us/graph/api/resources/alert) <sup>1</sup> | Less than 3 minutes | 5 minutes |
| [approvals](https://learn.microsoft.com/en-us/graph/api/resources/approvalItem) | Less than 10 seconds | 40 seconds |
| [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar) | Less than 1 minute | 3 minutes |
| [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord) <sup>2</sup> | Less than 30 minutes | 150 minutes |
| [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording) | Less than 10 seconds | 60 minutes |
| [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript) | Less than 10 seconds | 60 minutes |
| [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel) | Less than 10 seconds | 60 minutes |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat) | Less than 10 seconds | 60 minutes |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage) | Less than 10 seconds | 1 minute |
| [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact) | Less than 1 minute | 3 minutes |
| [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation) | Unknown | Unknown |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember) | Less than 10 seconds | 60 minutes |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem) | Less than 1 minute | 6 hours |
| [event](https://learn.microsoft.com/en-us/graph/api/resources/event) | Unknown | Unknown |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group) | Unknown | Unknown |
| [health monitoring alert](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-alert) | Unknown | Unknown |
| [list](https://learn.microsoft.com/en-us/graph/api/resources/list) | Less than 1 minute | 6 hours |
| [message](https://learn.microsoft.com/en-us/graph/api/resources/message) | Less than 1 minute | 3 minutes |
| [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest) | Less than 1 minute | 60 minutes |
| [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting) | Less than 10 seconds | 1 minute |
| [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest) | Less than 1 minute | 60 minutes |
| [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence) | Less than 10 seconds | 1 minute |
| [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer) | Less than 1 minute | 5 minutes |
| [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition) | Less than 1 minute | 5 minutes |
| [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift) | Less than 1 minute | 60 minutes |
| [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest) | Less than 1 minute | 60 minutes |
| [team](https://learn.microsoft.com/en-us/graph/api/resources/team) | Less than 10 seconds | 60 minutes |
| [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation) | Less than 10 seconds | 60 minutes |
| [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest) | Less than 1 minute | 60 minutes |
| [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask) | Less than 2 minutes | 15 minutes |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user) | Unknown | Unknown |

<sup>1</sup> The latency provided for the **alert** resource is only applicable after the alert is created. It doesn't include the time it takes for a rule to create an alert from the data. <sup>2</sup> The latency provided for the **callRecord** resource is only applicable to the first version of a call record. Subsequent versions of a call record might be updated beyond the stated latencies.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.subscription",
  "applicationId": "String",
  "changeType": "String",
  "clientState": "String",
  "creatorId": "String",
  "encryptionCertificate": "String",
  "encryptionCertificateId": "String",
  "expirationDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "includeResourceData": "Boolean",
  "latestSupportedTlsVersion": "String",
  "lifecycleNotificationUrl": "String",
  "notificationQueryOptions": "String",
  "notificationUrl": "String",
  "notificationUrlAppId": "String",
  "resource": "String",
  "vapidPublicKey": "String",
  "webPushEncryptionP256dhPublicKey": "String",
  "webPushEncryptionSecret": "String"
}
```
