<!-- Source: https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-05 -->

# Create subscription

Namespace: microsoft.graph

Subscribes a listener application to receive change notifications when the requested type of changes occur to the specified resource in Microsoft Graph.

To identify the resources for which you can create subscriptions and the limitations on subscriptions, see [Set up notifications for changes in resource data: Supported resources](https://learn.microsoft.com/en-us/graph/change-notifications-overview#supported-resources).

Some resources support rich notifications, that is, notifications that include resource data. For more information about these resources, see [Set up change notifications that include resource data: Supported resources](https://learn.microsoft.com/en-us/graph/change-notifications-with-resource-data#supported-resources).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

To create a subscription, your app must have read permissions for the resource. For example, to get change notifications for messages, your app needs the `Mail.Read` permission.

Depending on the resource and the permission type \(delegated or application\) requested, the permission specified in the following table is the least privileged required to call this API. To learn more, including [taking caution](https://learn.microsoft.com/en-us/graph/auth/auth-concepts#best-practices-for-requesting-permissions) before choosing the permissions, search for the following permissions in [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [aiInteraction](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api/ai-services/interaction-export/resources/aiinteraction)  <br>`copilot/users/{userId}/interactionHistory/getAllEnterpriseInteractions`  <br>Copilot AI interactions that a particular user is part of. | AiEnterpriseInteraction.Read | Not supported. | AiEnterpriseInteraction.Read.All, AiEnterpriseInteraction.Read.User |
| [aiInteraction](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api/ai-services/interaction-export/resources/aiinteraction)  <br>`copilot/interactionHistory/getAllEnterpriseInteractions`  <br>Copilot AI interactions in an organization. | Not supported. | Not supported. | AiEnterpriseInteraction.Read.All |
| [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0) \(/communications/callRecords\) | Not supported | Not supported | CallRecords.Read.All |
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
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) \(/chats/{id}/messages\) | Chat.Read, Chat.ReadWrite | Not supported | Chat.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) \(/chats/getAllMessages -- all chat messages in organization\) | Not supported | Not supported | Chat.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) \(/users/{id}/chats/getAllMessages -- chat messages for all chats a particular user is part of\) | Chat.Read, Chat.ReadWrite | Not supported | Chat.Read.All, Chat.ReadWrite.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>/appCatalogs/teamsApps/{id}/installedToChats/getAllMessages  <br>Chat messages for all chats in an organization where a particular Teams app is installed. | Not supported | Not supported | Chat.Read.WhereInstalled, Chat.ReadWrite.WhereInstalled |
| [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Contacts.Read | Contacts.Read | Contacts.Read |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) \(/chats/getAllMembers\) | Not supported | Not supported | ChatMember.Read.All, ChatMember.ReadWrite.All, Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) \(/chats/{id}/members\) | ChatMember.Read, ChatMember.ReadWrite, Chat.ReadBasic, Chat.Read, Chat.ReadWrite | Not supported | ChatMember.Read.Chat\*, Chat.Manage.Chat\*, ChatMember.Read.All, ChatMember.ReadWrite.All, Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0)  <br>/appCatalogs/teamsApps/{id}/installedToChats/getAllMembers  <br>Chat members for all chats in an organization where a particular Teams app is installed. | Not supported. | Not supported. | ChatMember.Read.WhereInstalled, ChatMember.ReadWrite.WhereInstalled, Chat.ReadBasic.WhereInstalled, Chat.Read.WhereInstalled, Chat.ReadWrite.WhereInstalled |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) \(/teams/{id}/members\) | TeamMember.Read.All | Not supported | TeamMember.Read.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) \(/teams/{id}/channels/getAllMembers\) | Not supported | Not supported | ChannelMember.Read.All |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) \(user's personal OneDrive\) | Not supported | Files.Read | Not supported |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) \(OneDrive for Business\) | Files.Read.All | Not supported | Files.Read.All |
| [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Calendars.Read | Calendars.Read | Calendars.Read |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Group.Read.All | Not supported | Group.Read.All |
| [group conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) | Group.Read.All | Not supported | Not supported |
| [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) | Sites.Read.All | Not supported | Sites.Read.All |
| [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Mail.ReadBasic, Mail.Read | Mail.ReadBasic, Mail.Read | Mail.Read |
| [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/offerShiftRequests\)  <br>Changes to any offer shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/openShiftChangeRequests\)  <br>Changes to any open shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence?view=graph-rest-1.0) | Presence.Read.All | Not supported | Not supported |
| [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) | Not supported | Not supported | Printer.Read.All, Printer.ReadWrite.All |
| [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) | Not supported | Not supported | PrintTaskDefinition.ReadWrite.All |
| [security alert](https://learn.microsoft.com/en-us/graph/api/resources/alert?view=graph-rest-1.0) | SecurityEvents.ReadWrite.All | Not supported | SecurityEvents.ReadWrite.All |
| [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/shifts\)  <br>Changes to any shift in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/swapShiftsChangeRequests\)  <br>Changes to any swap shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) \(/teams – all teams in an organization\) | Not supported | Not supported | Team.ReadBasic.All, TeamSettings.Read.All |
| [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) \(/teams/{id}\) | Team.ReadBasic.All, TeamSettings.Read.All | Not supported | Team.ReadBasic.All, TeamSettings.Read.All |
| [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/timeOffRequests\)  <br>Changes to any time off request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) | Tasks.ReadWrite | Tasks.ReadWrite | Tasks.ReadWrite.All |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | User.Read.All | User.Read.All | User.Read.All |
| [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) | VirtualEvent.Read | Not supported. | VirtualEvent.Read.All |
| [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) | VirtualEvent.Read | Not supported. | VirtualEvent.Read.All |

We recommend that you use the permissions as documented in the previous table. Due to security restrictions, Microsoft Graph subscriptions don't support write access permissions when only read access permissions are needed.

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

On a personal OneDrive, you can subscribe to the root folder or any subfolder in that drive. On OneDrive for Business, you can subscribe to only the root folder. Change notifications are sent for the requested types of changes on the subscribed folder, or any file, folder, or other **driveItem** instances in its hierarchy. You can't subscribe to **drive** or **driveItem** instances that aren't folders, such as individual files.

OneDrive for Business and SharePoint support sending your application notifications of security events that occur on a **driveItem**. To subscribe to these events, add the `prefer:includesecuritywebhooks` header to your request to create a subscription. After the subscription is created, you will receive notifications when the permissions on an item change. This header is applicable to SharePoint and OneDrive for Business but not consumer OneDrive accounts.

### contact, event, and message

You can subscribe to changes in Outlook **contact**, **event**, or **message** resources.

Creating and managing \(getting, updating, and deleting\) a subscription requires a read scope to the resource. For example, to get change notifications on messages, your app needs the Mail.Read permission. Outlook change notifications support delegated and application permission scopes. Note the following limitations:

- Delegated permission supports subscribing to items in folders in only the signed-in user's mailbox. For example, you can't use the delegated permission Calendars.Read to subscribe to events in another user’s mailbox.
- To subscribe to change notifications of Outlook contacts, events, or messages in *shared or delegated* folders:

  - Use the corresponding application permission to subscribe to changes of items in a folder or mailbox of *any* user in the tenant.
  - Don't use the Outlook sharing permissions \(Contacts.Read.Shared, Calendars.Read.Shared, Mail.Read.Shared, and their read/write counterparts\), as they do **not** support subscribing to change notifications on items in shared or delegated folders.

### presence

Subscriptions on **presence** require any resource data included in a change notification to be encrypted. Always specify the **encryptionCertificate** parameter when [creating a subscription](https://learn.microsoft.com/en-us/graph/change-notifications-with-resource-data#creating-a-subscription) to avoid failure. See more information about [setting up change notifications to include resource data](https://learn.microsoft.com/en-us/graph/change-notifications-with-resource-data).

### virtualEventWebinar and virtualEventTownhall

Subscriptions on virtual events support only basic notifications and are limited to a few entities of a virtual event. For more information about the supported subscription types, see [Get change notifications for Microsoft Teams virtual event updates](https://learn.microsoft.com/en-us/graph/changenotifications-for-virtualevent).

## HTTP request

```http
POST /subscriptions
```

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0) object.

## Response

If successful, this method returns `201 Created` response code and a [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0) object in the response body. For details about how errors are returned, see [Error responses](https://learn.microsoft.com/en-us/graph/errors).

## Example

### Request

The following example shows a request to send a change notification when the user receives a new mail.

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
Content-type: application/json

{
   "changeType": "created",
   "notificationUrl": "https://webhook.azurewebsites.net/api/send/myNotifyClient",
   "resource": "me/mailFolders('Inbox')/messages",
   "expirationDateTime":"2016-11-20T18:23:45.9356913Z",
   "clientState": "secretClientValue",
   "latestSupportedTlsVersion": "v1_2"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Subscription
{
	ChangeType = "created",
	NotificationUrl = "https://webhook.azurewebsites.net/api/send/myNotifyClient",
	Resource = "me/mailFolders('Inbox')/messages",
	ExpirationDateTime = DateTimeOffset.Parse("2016-11-20T18:23:45.9356913Z"),
	ClientState = "secretClientValue",
	LatestSupportedTlsVersion = "v1_2",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Subscriptions.PostAsync(requestBody);
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
changeType := "created"
requestBody.SetChangeType(&changeType) 
notificationUrl := "https://webhook.azurewebsites.net/api/send/myNotifyClient"
requestBody.SetNotificationUrl(&notificationUrl) 
resource := "me/mailFolders('Inbox')/messages"
requestBody.SetResource(&resource) 
expirationDateTime , err := time.Parse(time.RFC3339, "2016-11-20T18:23:45.9356913Z")
requestBody.SetExpirationDateTime(&expirationDateTime) 
clientState := "secretClientValue"
requestBody.SetClientState(&clientState) 
latestSupportedTlsVersion := "v1_2"
requestBody.SetLatestSupportedTlsVersion(&latestSupportedTlsVersion) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
subscriptions, err := graphClient.Subscriptions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Subscription subscription = new Subscription();
subscription.setChangeType("created");
subscription.setNotificationUrl("https://webhook.azurewebsites.net/api/send/myNotifyClient");
subscription.setResource("me/mailFolders('Inbox')/messages");
OffsetDateTime expirationDateTime = OffsetDateTime.parse("2016-11-20T18:23:45.9356913Z");
subscription.setExpirationDateTime(expirationDateTime);
subscription.setClientState("secretClientValue");
subscription.setLatestSupportedTlsVersion("v1_2");
Subscription result = graphClient.subscriptions().post(subscription);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const subscription = {
   changeType: 'created',
   notificationUrl: 'https://webhook.azurewebsites.net/api/send/myNotifyClient',
   resource: 'me/mailFolders(\'Inbox\')/messages',
   expirationDateTime: '2016-11-20T18:23:45.9356913Z',
   clientState: 'secretClientValue',
   latestSupportedTlsVersion: 'v1_2'
};

await client.api('/subscriptions')
	.post(subscription);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Subscription;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Subscription();
$requestBody->setChangeType('created');
$requestBody->setNotificationUrl('https://webhook.azurewebsites.net/api/send/myNotifyClient');
$requestBody->setResource('me/mailFolders(\'Inbox\')/messages');
$requestBody->setExpirationDateTime(new \DateTime('2016-11-20T18:23:45.9356913Z'));
$requestBody->setClientState('secretClientValue');
$requestBody->setLatestSupportedTlsVersion('v1_2');

$result = $graphServiceClient->subscriptions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.ChangeNotifications

$params = @{
	changeType = "created"
	notificationUrl = "https://webhook.azurewebsites.net/api/send/myNotifyClient"
	resource = "me/mailFolders('Inbox')/messages"
	expirationDateTime = [System.DateTime]::Parse("2016-11-20T18:23:45.9356913Z")
	clientState = "secretClientValue"
	latestSupportedTlsVersion = "v1_2"
}

New-MgSubscription -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.subscription import Subscription
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Subscription(
	change_type = "created",
	notification_url = "https://webhook.azurewebsites.net/api/send/myNotifyClient",
	resource = "me/mailFolders('Inbox')/messages",
	expiration_date_time = "2016-11-20T18:23:45.9356913Z",
	client_state = "secretClientValue",
	latest_supported_tls_version = "v1_2",
)

result = await graph_client.subscriptions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

In the request body, supply a JSON representation of the [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0) object. The `clientState` and `latestSupportedTlsVersion` fields are optional.

#### Duplicate subscription behavior

Duplicate subscriptions aren't allowed. When a subscription request contains the same values for **changeType** and **resource** that an existing subscription contains, the request fails with an HTTP error code `409 Conflict`, and the error message `Subscription Id <> already exists for the requested combination`.

#### Resources examples

The following are valid values for the resource property of the subscription:

| Resource type | Examples |
| :--- | :--- |
| [Call records](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0) | `communications/callRecords` |
| [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) | `communications/onlineMeetings/getAllRecordings`, `communications/onlineMeetings/{onlineMeetingId}/recordings`, `users/{userId}/onlineMeetings/getAllRecordings` |
| [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0) | `communications/onlineMeetings/getAllTranscripts`, `communications/onlineMeetings/{onlineMeetingId}/transcripts`, `users/{userId}/onlineMeetings/getAllTranscripts` |
| [Chat message](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | `chats/{id}/messages`, `chats/getAllMessages`, `teams/{id}/channels/{id}/messages`, `teams/getAllMessages` |
| [Contacts](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | `me/contacts` |
| [Conversations](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) | `groups('{id}')/conversations` |
| [Drives](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | `me/drive/root` |
| [Events](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | `me/events` |
| [Groups](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | `groups` |
| [List](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) | `sites/{site-id}/lists/{list-id}` |
| [Mail](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | `me/mailfolders('inbox')/messages`, `me/messages` |
| [Presence](https://learn.microsoft.com/en-us/graph/api/resources/presence?view=graph-rest-1.0) | `/communications/presences/{id}` \(single user\), `/communications/presences?$filter=id in ('{id}','{id}',…)` \(multiple users\) |
| [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) | `print/printers/{id}/jobs` |
| [PrintTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) | `print/taskDefinitions/{id}/tasks` |
| [Security alert](https://learn.microsoft.com/en-us/graph/api/resources/alert?view=graph-rest-1.0) | `security/alerts?$filter=status eq 'New'` |
| [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) | `/me/todo/lists/{todoTaskListId}/tasks` |
| [Users](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | `users` |

> **Note:** Any path starting with `me` can also be used with `users/{id}` instead of `me` to target a specific user instead of the current user.

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#subscriptions/$entity",
  "id": "7f105c7d-2dc5-4530-97cd-4e7ae6534c07",
  "resource": "me/mailFolders('Inbox')/messages",
  "applicationId": "24d3b144-21ae-4080-943f-7067b395b913",
  "changeType": "created",
  "clientState": "secretClientValue",
  "notificationUrl": "https://webhook.azurewebsites.net/api/send/myNotifyClient",
  "expirationDateTime": "2016-11-20T18:23:45.9356913Z",
  "creatorId": "8ee44408-0679-472c-bc2a-692812af3437",
  "latestSupportedTlsVersion": "v1_2",
  "notificationContentType": "application/json"
}
```

#### Notification endpoint validation

The subscription notification endpoint \(specified in the `notificationUrl` property\) must be capable of responding to a validation request as described in [Set up notifications for changes in user data](https://learn.microsoft.com/en-us/graph/change-notifications-overview#notification-endpoint-validation). If validation fails, the request to create the subscription returns a 400 Bad Request error.
