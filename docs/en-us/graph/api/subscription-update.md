<!-- Source: https://learn.microsoft.com/en-us/graph/api/subscription-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-06 -->

# Update subscription

Namespace: microsoft.graph

Renew a subscription by extending its expiry time.

The table in the [Permissions](#permissions) section lists the resources that support subscribing to change notifications.

Subscriptions expire after a length of time that varies by resource type. In order to avoid missing change notifications, an app should renew its subscriptions well in advance of their expiry date. See [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0) for maximum length of a subscription for each resource type.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Depending on the resource and the permission type \(delegated or application\) requested, the permission specified in the following table is the least privileged required to call this API. To learn more, including [taking caution](https://learn.microsoft.com/en-us/graph/auth/auth-concepts#best-practices-for-requesting-permissions) before choosing more privileged permissions, search for the following permissions in [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [aiInteraction](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api/ai-services/interaction-export/resources/aiinteraction)  <br>`copilot/users/{userId}/interactionHistory/getAllEnterpriseInteractions`  <br>Copilot AI interactions that a particular user is part of. | AiEnterpriseInteraction.Read | Not supported. | AiEnterpriseInteraction.Read.All, AiEnterpriseInteraction.Read.User |
| [aiInteraction](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api/ai-services/interaction-export/resources/aiinteraction)  <br>`copilot/interactionHistory/getAllEnterpriseInteractions`  <br>Copilot AI interactions in an organization. | Not supported. | Not supported. | AiEnterpriseInteraction.Read.All |
| [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0) | Not supported | Not supported | CallRecords.Read.All |
| [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0)  <br>`communications/onlineMeetings/getAllRecordings`  <br>All recordings in an organization. | Not supported. | Not supported. | OnlineMeetingRecording.Read.All |
| [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0)  <br>`communications/onlineMeetings/{onlineMeetingId}/recordings`  <br>All recordings for a specific meeting. | OnlineMeetingRecording.Read.All | Not supported. | OnlineMeetingRecording.Read.All |
| [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0)  <br>`users/{userId}/onlineMeetings/getAllRecordings`  <br>A call recording that becomes available in a meeting organized by a specific user. | OnlineMeetingRecording.Read.All | Not supported. | OnlineMeetingRecording.Read.All |
| [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0)  <br>`communications/onlineMeetings/getAllTranscripts`  <br>All transcripts in an organization. | Not supported. | Not supported. | OnlineMeetingTranscript.Read.All |
| [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0)  <br>`communications/onlineMeetings/{onlineMeetingId}/transcripts`  <br>All transcripts for a specific meeting. | OnlineMeetingTranscript.Read.All | Not supported. | OnlineMeetingTranscript.Read.All |
| [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0)  <br>`users/{userId}/onlineMeetings/getAllTranscripts`  <br>A call transcript that becomes available in a meeting organized by a specific user. | OnlineMeetingTranscript.Read.All | Not supported. | OnlineMeetingTranscript.Read.All |
| [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) \(/teams/getAllChannels – all channels in an organization\) | Not supported | Not supported | Channel.ReadBasic.All, ChannelSettings.Read.All |
| [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) \(/teams/{id}/channels\) | Channel.ReadBasic.All, ChannelSettings.Read.All | Not supported | Channel.ReadBasic.All, ChannelSettings.Read.All |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) \(/chats – all chats in an organization\) | Not supported | Not supported | Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) \(/chats/{id}\) | Chat.ReadBasic, Chat.Read, Chat.ReadWrite | Not supported | ChatSettings.Read.Chat\*, ChatSettings.ReadWrite.Chat\*, Chat.Manage.Chat\*, Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0)  <br>/appCatalogs/teamsApps/{id}/installedToChats  <br>All chats in an organization where a particular Teams app is installed. | Not supported | Not supported | Chat.ReadBasic.WhereInstalled, Chat.Read.WhereInstalled, Chat.ReadWrite.WhereInstalled |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0)  <br>`/users/{id}/chats`  <br>All chats that a particular user is part of. | Chat.ReadBasic, Chat.Read, Chat.ReadWrite | Not supported. | Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) \(/teams/{id}/channels/{id}/messages\) | ChannelMessage.Read.All | Not supported | ChannelMessage.Read.Group\*, ChannelMessage.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) \(/teams/getAllMessages -- all channel messages in organization\) | Not supported | Not supported | ChannelMessage.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) \(/chats/{id}/messages\) | Not supported | Not supported | Chat.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) \(/chats/getAllMessages -- all chat messages in organization\) | Not supported | Not supported | Chat.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) \(/users/{id}/chats/getAllMessages -- chat messages for all chats a particular user is part of\) | Chat.Read, Chat.ReadWrite | Not supported | Chat.Read.All, Chat.ReadWrite.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>/appCatalogs/teamsApps/{id}/installedToChats/getAllMessages  <br>Chat messages for all chats in an organization where a particular Teams app is installed. | Not supported | Not supported | Chat.Read.WhereInstalled, Chat.ReadWrite.WhereInstalled |
| [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Contacts.Read | Contacts.Read | Contacts.Read |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) \(/chats/getAllMembers\) | Not supported | Not supported | ChatMember.Read.All, ChatMember.ReadWrite.All, Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) \(/chats/{id}/members\) | ChatMember.Read, ChatMember.ReadWrite, Chat.ReadBasic, Chat.Read, Chat.ReadWrite | Not supported | ChatMember.Read.Chat\*, Chat.Manage.Chat\*, ChatMember.Read.All, ChatMember.ReadWrite.All, Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0)  <br>/appCatalogs/teamsApps/{id}/installedToChats/getAllMembers  <br>Chat members for all chats in an organization where a particular Teams app is installed. | Not supported. | Not supported. | ChatMember.Read.WhereInstalled, ChatMember.ReadWrite.WhereInstalled, Chat.ReadBasic.WhereInstalled, Chat.Read.WhereInstalled, Chat.ReadWrite.WhereInstalled |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) \(/teams/{id}/members\) | TeamMember.Read.All | Not supported | TeamMember.Read.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) \(/teams/{id}/channels/getAllMembers\) | Not supported | Not supported | ChannelMember.Read.All |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) \(user's personal OneDrive\) | Not supported | Files.ReadWrite | Not supported |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) \(OneDrive for Business\) | Files.ReadWrite.All | Not supported | Files.ReadWrite.All |
| [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Calendars.Read | Calendars.Read | Calendars.Read |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Group.Read.All | Not supported | Group.Read.All |
| [group conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) | Group.Read.All | Not supported | Not supported |
| [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) | Sites.ReadWrite.All | Not supported | Sites.ReadWrite.All |
| [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Mail.ReadBasic, Mail.Read | Mail.ReadBasic, Mail.Read | Mail.Read |
| [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/offerShiftRequests\)  <br>Changes to any offer shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/openShiftChangeRequests\)  <br>Changes to any open shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence?view=graph-rest-1.0) | Presence.Read.All | Not supported. | Not supported. |
| [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) | Not supported | Not supported | Printer.Read.All, Printer.ReadWrite.All |
| [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) | Not supported | Not supported | PrintTaskDefinition.ReadWrite.All |
| [security alert](https://learn.microsoft.com/en-us/graph/api/resources/alert?view=graph-rest-1.0) | SecurityEvents.ReadWrite.All | Not supported | SecurityEvents.ReadWrite.All |
| [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/shifts\)  <br>Changes to any shift in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/swapShiftsChangeRequests\)  <br>Changes to any swap shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) \(/teams – all teams in an organization\) | Not supported | Not supported | Team.ReadBasic.All, TeamSettings.Read.All |
| [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) \(/teams/{id}\) | Team.ReadBasic.All, TeamSettings.Read.All | Not supported | Team.ReadBasic.All, TeamSettings.Read.All |
| [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/timeOffRequests\)  <br>Changes to any time off request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) | Tasks.ReadWrite | Tasks.ReadWrite | Not supported |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | User.Read.All | User.Read.All | User.Read.All |
| [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) | VirtualEvent.Read | Not supported. | VirtualEvent.Read.All |

> **Note**: Permissions marked with \* use [resource-specific consent](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

### chatMessage

**chatMessage** subscriptions can be specified to include resource data \(**includeResourceData** set to `true`\). In that case, encryption is required and the subscription creation fails if an **encryptionCertificate** isn't specified for such subscriptions.

Use the `Prefer: include-unknown-enum-members` request header to get the following values in **chatMessage** **messageType** [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `systemEventMessage` for `/teams/{id}/channels/{id}/messages` and `/chats/{id}/messages` resource.

### conversationMember

**conversationMember** subscriptions can be specified to include resource data \(**includeResourceData** set to `true`\). In that case, encryption is required and the subscription creation fails if an **encryptionCertificate** isn't specified for such subscriptions.

### team, channel, and chat

**team**, **channel**, and **chat** subscriptions can be specified to include resource data \(**includeResourceData** set to `true`\). In that case, encryption is required and the subscription creation fails if an **encryptionCertificate** isn't specified for such subscriptions.

You can use the **notifyOnUserSpecificProperties** query string parameter when you subscribe to changes in a particular chat or at user level. When you set the query string parameter **notifyOnUserSpecificProperties** to `true` during subscription creation, two types of payloads are sent to the subscriber. One type contains user-specific properties, and the other is sent without them. For more information, see [Get change notifications for chats using Microsoft Graph](https://learn.microsoft.com/en-us/graph/teams-changenotifications-chat).

### aiInteraction

Subscriptions on Copilot AI interactions require a valid Copilot license that includes the following Copilot service plan:

- **Microsoft 365 Copilot Chat**: 3f30311c-6b1e-48a4-ab79-725b469da960

For subscriptions that target Copilot AI interactions that a particular user is part of, the user in the resource path must have the previous service plans assigned to them in a valid state.

For subscriptions that target Copilot AI interactions for the entire tenant, the tenant must have valid licenses provisioned that include all previous Copilot service plans.

### driveItem

Additional limitations apply for subscriptions on OneDrive items. The limitations apply to creating as well as managing \(getting, updating, and deleting\) subscriptions.

On personal OneDrive, you can subscribe to the root folder or any subfolder in that drive. On OneDrive for Business, you can subscribe to only the root folder. Change notifications are sent for the requested types of changes on the subscribed folder, or any file, folder, or other **driveItem** instances in its hierarchy. You can't subscribe to **drive** or **driveItem** instances that aren't folders, such as individual files.

### contact, event, and message

You can subscribe to changes in Outlook **contact**, **event**, or **message** resources.

Creating and managing \(getting, updating, and deleting\) a subscription requires a read scope to the resource. For example, to get change notifications on messages, your app needs the Mail.Read permission. Outlook change notifications support delegated and application permission scopes. Note the following limitations:

- Delegated permission supports subscribing to items in folders in only the signed-in user's mailbox. For example, you can't use the delegated permission Calendars.Read to subscribe to events in another user’s mailbox.
- To subscribe to change notifications of Outlook contacts, events, or messages in *shared or delegated* folders:

  - Use the corresponding application permission to subscribe to changes of items in a folder or mailbox of *any* user in the tenant.
  - Don't use the Outlook sharing permissions \(Contacts.Read.Shared, Calendars.Read.Shared, Mail.Read.Shared, and their read/write counterparts\), as they do **not** support subscribing to change notifications on items in shared or delegated folders.

### presence

**presence** Subscriptions on **presence** **chatMessage** subscriptions can be specified to include resource data \(**includeResourceData** set to `true`\). In that case, encryption is required and the subscription creation fails if an **encryptionCertificate** and **encryptionCertificateId** aren't specified. For details about presence subscriptions, see [Get change notifications for presence updates in Microsoft Teams](https://learn.microsoft.com/en-us/graph/changenotifications-for-presence).

### virtualEventWebinar

Subscriptions on virtual events support only basic notifications and are limited to a few entities of a virtual event. For more information about the supported subscription types, see [Get change notifications for Microsoft Teams virtual event updates](https://learn.microsoft.com/en-us/graph/changenotifications-for-virtualevent).

## HTTP request

```http
PATCH /subscriptions/{id}
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

The request body must contain either the `expirationDateTime` or `notificationUrl` property and its value.

| Name | Type | Description |
| :--- | :--- | :--- |
| expirationDateTime | DateTimeOffset | Specifies the date and time in UTC when the subscription expires. For the maximum supported subscription, the length of time varies depending on the resource. For more information, see [Subscription lifetime](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0#subscription-lifetime). |
| notificationUrl | String | This URL must make use of the HTTPS protocol. Any query string parameter included in the notificationUrl property is included in the HTTP POST request when Microsoft Graph sends the change notifications. |

## Response

If successful, this method returns a `200 OK` response code and [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0) object in the response body.

Note

A `404 Not Found` response indicates that the subscription no longer exists. For example, it already expired and was removed by the service, or it was deleted. The subscription can't be renewed in this state, so retrying the update keeps failing. To avoid missing change notifications, [create a new subscription](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions?view=graph-rest-1.0) instead of retrying the update. To reduce how often this happens, renew subscriptions well before they expire and use [lifecycle notifications](https://learn.microsoft.com/en-us/graph/change-notifications-lifecycle-events) to renew subscriptions proactively.

For details about how errors are returned, see [Error responses](https://learn.microsoft.com/en-us/graph/errors).

## Example

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
PATCH https://graph.microsoft.com/v1.0/subscriptions/{id}
Content-type: application/json

{
   "expirationDateTime":"2016-11-22T18:23:45.9356913Z"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Subscription
{
	ExpirationDateTime = DateTimeOffset.Parse("2016-11-22T18:23:45.9356913Z"),
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Subscriptions["{subscription-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

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
expirationDateTime , err := time.Parse(time.RFC3339, "2016-11-22T18:23:45.9356913Z")
requestBody.SetExpirationDateTime(&expirationDateTime) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
subscriptions, err := graphClient.Subscriptions().BySubscriptionId("subscription-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Subscription subscription = new Subscription();
OffsetDateTime expirationDateTime = OffsetDateTime.parse("2016-11-22T18:23:45.9356913Z");
subscription.setExpirationDateTime(expirationDateTime);
Subscription result = graphClient.subscriptions().bySubscriptionId("{subscription-id}").patch(subscription);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const subscription = {
   expirationDateTime: '2016-11-22T18:23:45.9356913Z'
};

await client.api('/subscriptions/{id}')
	.update(subscription);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Subscription;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Subscription();
$requestBody->setExpirationDateTime(new \DateTime('2016-11-22T18:23:45.9356913Z'));

$result = $graphServiceClient->subscriptions()->bySubscriptionId('subscription-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.ChangeNotifications

$params = @{
	expirationDateTime = [System.DateTime]::Parse("2016-11-22T18:23:45.9356913Z")
}

Update-MgSubscription -SubscriptionId $subscriptionId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.subscription import Subscription
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Subscription(
	expiration_date_time = "2016-11-22T18:23:45.9356913Z",
)

result = await graph_client.subscriptions.by_subscription_id('subscription-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "id":"7f105c7d-2dc5-4530-97cd-4e7ae6534c07",
  "resource":"me/messages",
  "applicationId": "24d3b144-21ae-4080-943f-7067b395b913",
  "changeType":"created,updated",
  "clientState":"subscription-identifier",
  "notificationUrl":"https://webhook.azurewebsites.net/api/send/myNotifyClient",
  "lifecycleNotificationUrl":"https://webhook.azurewebsites.net/api/send/lifecycleNotifications",
  "expirationDateTime":"2016-11-22T18:23:45.9356913Z",
  "creatorId": "8ee44408-0679-472c-bc2a-692812af3437",
  "latestSupportedTlsVersion": "v1_2",
  "encryptionCertificate": "",
  "encryptionCertificateId": "",
  "includeResourceData": false,
  "notificationContentType": "application/json"
}
```
