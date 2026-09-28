<!-- Source: https://learn.microsoft.com/en-us/graph/api/subscription-list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-05 -->

# List subscriptions

Namespace: microsoft.graph

Retrieve the properties and relationships of webhook subscriptions, based on the app ID, the user, and the user's role with a tenant.

The content of the response depends on the context in which the app is calling; for details, see the scenarios in the [Permissions](#permissions) section.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

This API supports the following permission scopes; to learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

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
| [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) \(/teams/{id}/channels\) | Channel.ReadBasic.All, ChannelSettings.Read.All, Subscription.Read.All | Not supported | Channel.ReadBasic.All, ChannelSettings.Read.All |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) \(/chats – all chats in an organization\) | Not supported | Not supported | Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) \(/chats/{id}\) | Chat.ReadBasic, Chat.Read, Chat.ReadWrite, Subscription.Read.All | Not supported | ChatSettings.Read.Chat\*, ChatSettings.ReadWrite.Chat\*, Chat.Manage.Chat\*, Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0)  <br>/appCatalogs/teamsApps/{id}/installedToChats  <br>All chats in an organization where a particular Teams app is installed. | Not supported | Not supported | Chat.ReadBasic.WhereInstalled, Chat.Read.WhereInstalled, Chat.ReadWrite.WhereInstalled |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0)  <br>`/users/{id}/chats`  <br>All chats that a particular user is part of. | Chat.ReadBasic, Chat.Read, Chat.ReadWrite | Not supported. | Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) \(/teams/{id}/channels/{id}/messages\) | ChannelMessage.Read.All, Group.Read.All, Group.ReadWrite.All, Subscription.Read.All | Not supported | ChannelMessage.Read.Group\*, ChannelMessage.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) \(/teams/getAllMessages -- all channel messages in organization\) | Not supported | Not supported | ChannelMessage.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) \(/chats/{id}/messages\) | Chat.Read, Chat.ReadWrite, Subscription.Read.All | Not supported | Chat.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) \(/chats/getAllMessages -- all chat messages in organization\) | Not supported | Not supported | Chat.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) \(/users/{id}/chats/getAllMessages -- chat messages for all chats a particular user is part of\) | Chat.Read, Chat.ReadWrite | Not supported | Chat.Read.All, Chat.ReadWrite.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>/appCatalogs/teamsApps/{id}/installedToChats/getAllMessages  <br>Chat messages for all chats in an organization where a particular Teams app is installed. | Not supported. | Not supported. | Chat.Read.WhereInstalled, Chat.ReadWrite.WhereInstalled |
| [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Contacts.Read, Subscription.Read.All | Contacts.Read, Subscription.Read.All | Contacts.Read |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) \(/teams/{id}/channels/getAllMembers\) | Not supported | Not supported | ChannelMember.Read.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) \(/chats/getAllMembers\) | Not supported | Not supported | ChatMember.Read.All, ChatMember.ReadWrite.All, Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) \(/chats/{id}/members\) | ChatMember.Read, ChatMember.ReadWrite, Chat.ReadBasic, Chat.Read, Chat.ReadWrite, Subscription.Read.All | Not supported | ChatMember.Read.Chat\*, Chat.Manage.Chat\*, ChatMember.Read.All, ChatMember.ReadWrite.All, Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0)  <br>/appCatalogs/teamsApps/{id}/installedToChats/getAllMembers  <br>Chat members for all chats in an organization where a particular Teams app is installed. | Not supported | Not supported | ChatMember.Read.WhereInstalled, ChatMember.ReadWrite.WhereInstalled, Chat.ReadBasic.WhereInstalled, Chat.Read.WhereInstalled, Chat.ReadWrite.WhereInstalled |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) \(/teams/{id}/members\) | TeamMember.Read.All, Subscription.Read.All | Not supported | TeamMember.Read.All |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) \(user's personal OneDrive\) | Not supported | Files.ReadWrite, Subscription.Read.All | Not supported |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) \(OneDrive for work or school\) | Files.ReadWrite.All, Subscription.Read.All | Not supported | Files.ReadWrite.All |
| [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Calendars.Read, Subscription.Read.All | Calendars.Read, Subscription.Read.All | Calendars.Read |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Group.Read.All, Subscription.Read.All | Not supported | Group.Read.All |
| [group conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) | Group.Read.All, Subscription.Read.All | Not supported | Not supported |
| [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) | Sites.ReadWrite.All, Subscription.Read.All | Not supported | Sites.ReadWrite.All |
| [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Mail.ReadBasic, Mail.Read, Subscription.Read.All | Mail.ReadBasic, Mail.Read, Subscription.Read.All | Mail.Read |
| [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/offerShiftRequests\)  <br>Changes to any offer shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/openShiftChangeRequests\)  <br>Changes to any open shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence?view=graph-rest-1.0) | Presence.Read.All, Subscription.Read.All | Not supported | Not supported |
| [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) | Not supported | Not supported | Printer.Read.All, Printer.ReadWrite.All |
| [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) | Not supported | Not supported | PrintTaskDefinition.ReadWrite.All |
| [security alert](https://learn.microsoft.com/en-us/graph/api/resources/alert?view=graph-rest-1.0) | SecurityEvents.ReadWrite.All, Subscription.Read.All | Not supported | SecurityEvents.ReadWrite.All |
| [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/shifts\)  <br>Changes to any shift in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/swapShiftsChangeRequests\)  <br>Changes to any swap shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) \(/teams – all teams in an organization\) | Not supported | Not supported | Team.ReadBasic.All, TeamSettings.Read.All |
| [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) \(/teams/{id}\) | Team.ReadBasic.All, TeamSettings.Read.All, Subscription.Read.All | Not supported | Team.ReadBasic.All, TeamSettings.Read.All |
| [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/timeOffRequests\)  <br>Changes to any time off request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) | Tasks.ReadWrite, Subscription.Read.All | Tasks.ReadWrite, Subscription.Read.All | Not supported |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | User.Read.All, Subscription.Read.All | User.Read.All | User.Read.All |

> **Note**: Permissions marked with \* use [resource-specific consent](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

Response results are based on the context of the calling app. The following sections describe the common scenarios.

### Basic scenarios

Most commonly, an application wants to retrieve subscriptions that it originally created for the currently signed-in user, or for all users in the directory \(work/school accounts\). These scenarios don't require any special permissions beyond the ones the app used originally to create its subscriptions.

| Context of the calling app | Response contains |
| :--- | :--- |
| App is calling on behalf of the signed-in user \(delegated permission\).  <br>-and-  <br>App has the original permission required to [create the subscription](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions?view=graph-rest-1.0).  <br>  <br>Note: This applies to both personal Microsoft accounts and work/school accounts. | Subscriptions created by **this app** for the signed-in user only. |
| App is calling on behalf of itself \(application permission\).  <br>-and-  <br>App has the original permission required to [create the subscription](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions?view=graph-rest-1.0).  <br>  <br>**Note:** This applies to work/school accounts only. | Subscriptions created by **this app** for itself or for any user in the directory. |

### Advanced scenarios

In some cases, an app wants to retrieve subscriptions created by other apps. For example, a user wants to see all subscriptions created by any app on their behalf. Or, a Global Administrator might want to see all subscriptions from all apps in their directory. For such scenarios, a delegated permission Subscription.Read.All is required.

| Context of the calling app | Response contains |
| :--- | :--- |
| App is calling on behalf of the signed-in user \(delegated permission\). *The user is a non-admin*.  <br>-and-  <br>App has the permission Subscription.Read.All  <br>  <br>Note: This applies to both personal Microsoft accounts and work/school accounts. | Subscriptions created by **any app** for the signed-in user only. |
| App is calling on behalf of the signed-in user \(delegated permission\). *The user is a Global Administrator*.  <br>-and-  <br>App has the permission Subscription.Read.All  <br>  <br>Note: This applies to work/school accounts only. | Subscriptions created by **any app** for **any user** in the directory. |

## HTTP request

```http
GET /subscriptions
```

## Optional query parameters

This method doesn't support the [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a list of [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0) objects in the response body.

## Example

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
GET https://graph.microsoft.com/v1.0/subscriptions
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Subscriptions.GetAsync();
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
subscriptions, err := graphClient.Subscriptions().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SubscriptionCollectionResponse result = graphClient.subscriptions().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let subscriptions = await client.api('/subscriptions')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->subscriptions()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.ChangeNotifications

Get-MgSubscription
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.subscriptions.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#subscriptions",
  "value": [
    {
      "id": "0fc0d6db-0073-42e5-a186-853da75fb308",
      "resource": "Users",
      "applicationId": "24d3b144-21ae-4080-943f-7067b395b913",
      "changeType": "updated,deleted",
      "clientState": null,
      "notificationUrl": "https://webhookappexample.azurewebsites.net/api/notifications",
      "lifecycleNotificationUrl":"https://webhook.azurewebsites.net/api/send/lifecycleNotifications",
      "expirationDateTime": "2018-03-12T05:00:00Z",
      "creatorId": "8ee44408-0679-472c-bc2a-692812af3437",
      "latestSupportedTlsVersion": "v1_2",
      "encryptionCertificate": "",
      "encryptionCertificateId": "",
      "includeResourceData": false,
      "notificationContentType": "application/json"
    }
  ]
}
```

> **Note:** the `clientState` property value is not returned for security purposes.

When a request returns multiple pages of data, the response includes an `@odata.nextLink` property to help you manage the results. To learn more, see [Paging Microsoft Graph data in your app](https://learn.microsoft.com/en-us/graph/paging).
