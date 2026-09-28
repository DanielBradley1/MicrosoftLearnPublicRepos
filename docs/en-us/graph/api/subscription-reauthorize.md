<!-- Source: https://learn.microsoft.com/en-us/graph/api/subscription-reauthorize?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-05 -->

# subscription: reauthorize

Namespace: microsoft.graph

Reauthorize a subscription when you receive a **reauthorizationRequired** challenge.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Depending on the resource and the permission type \(delegated or application\) requested, the permission specified in the following table is the least privileged required to call this API. To learn more, including [taking caution](https://learn.microsoft.com/en-us/graph/auth/auth-concepts#best-practices-for-requesting-permissions) before choosing more privileged permissions, search for the following permissions in [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

> **Note**:
> 
> Some resources support change notifications in multiple scenarios, each of which may require different permissions. In those cases, use the resource path to differentiate the scenarios.
> 
> Permissions marked with \* use [resource-specific consent](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent).

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [aiInteraction](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api/ai-services/interaction-export/resources/aiinteraction)  <br>`copilot/users/{userId}/interactionHistory/getAllEnterpriseInteractions`  <br>Copilot AI interactions that a particular user is part of. | AiEnterpriseInteraction.Read | Not supported. | AiEnterpriseInteraction.Read.All, AiEnterpriseInteraction.Read.User |
| [aiInteraction](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api/ai-services/interaction-export/resources/aiinteraction)  <br>`copilot/interactionHistory/getAllEnterpriseInteractions`  <br>Copilot AI interactions in an organization. | Not supported. | Not supported. | AiEnterpriseInteraction.Read.All |
| [baseTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) \(deprecated\) | Tasks.ReadWrite | Tasks.ReadWrite | Not supported. |
| [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0) | Not supported. | Not supported. | CallRecords.Read.All |
| [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0)  <br>`communications/onlineMeetings/getAllRecordings`  <br>All recordings in an organization. | Not supported. | Not supported. | OnlineMeetingRecording.Read.All |
| [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0)  <br>`communications/onlineMeetings/{onlineMeetingId}/recordings`  <br>All recordings for a specific meeting. | OnlineMeetingRecording.Read.All | Not supported. | OnlineMeetingRecording.Read.All |
| [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0)  <br>`users/{userId}/onlineMeetings/getAllRecordings`  <br>A call recording that becomes available in a meeting organized by a specific user. | OnlineMeetingRecording.Read.All | Not supported. | OnlineMeetingRecording.Read.All |
| [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0)  <br>`communications/onlineMeetings/getAllTranscripts`  <br>All transcripts in an organization. | Not supported. | Not supported. | OnlineMeetingTranscript.Read.All |
| [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0)  <br>`communications/onlineMeetings/{onlineMeetingId}/transcripts`  <br>All transcripts for a specific meeting. | OnlineMeetingTranscript.Read.All | Not supported. | OnlineMeetingTranscript.Read.All |
| [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0)  <br>`users/{userId}/onlineMeetings/getAllTranscripts`  <br>A call transcript that becomes available in a meeting organized by a specific user. | OnlineMeetingTranscript.Read.All | Not supported. | OnlineMeetingTranscript.Read.All |
| [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0)  <br>/teams/getAllChannels  <br>All channels in an organization. | Not supported. | Not supported. | Channel.ReadBasic.All, ChannelSettings.Read.All |
| [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0)  <br>/teams/{id}/channels  <br>All channels in a particular team in an organization. | Channel.ReadBasic.All, ChannelSettings.Read.All | Not supported. | Channel.ReadBasic.All, ChannelSettings.Read.All |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0)  <br>/chats  <br>All chats in an organization. | Not supported. | Not supported. | Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0)  <br>/chats/{id}  <br>A particular chat. | Chat.ReadBasic, Chat.Read, Chat.ReadWrite | Not supported. | ChatSettings.Read.Chat\*, ChatSettings.ReadWrite.Chat\*, Chat.Manage.Chat\*, Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0)  <br>/appCatalogs/teamsApps/{id}/installedToChats  <br>All chats in an organization where a particular Teams app is installed. | Not supported | Not supported | Chat.ReadBasic.WhereInstalled, Chat.Read.WhereInstalled, Chat.ReadWrite.WhereInstalled |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0)  <br>`/users/{id}/chats`  <br>All chats that a particular user is part of. | Chat.ReadBasic, Chat.Read, Chat.ReadWrite | Not supported. | Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>/teams/{id}/channels/{id}/messages  <br>All messages and replies in a particular channel. | ChannelMessage.Read.All, Group.Read.All, Group.ReadWrite.All | Not supported. | ChannelMessage.Read.Group\*, ChannelMessage.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>/teams/getAllMessages  <br>All channel messages in organization. | Not supported. | Not supported. | ChannelMessage.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>/chats/{id}/messages  <br>All messages in a chat. | Chat.Read, Chat.ReadWrite | Not supported. | Chat.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>/chats/getAllMessages.  <br>All chat messages in an organization. | Not supported. | Not supported. | Chat.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>/users/{id}/chats/getAllMessages  <br>Chat messages for all chats a particular user is part of. | Chat.Read, Chat.ReadWrite | Not supported. | Chat.Read.All, Chat.ReadWrite.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>/appCatalogs/teamsApps/{id}/installedToChats/getAllMessages  <br>Chat messages for all chats in an organization where a particular Teams app is installed. | Not supported | Not supported | Chat.Read.WhereInstalled, Chat.ReadWrite.WhereInstalled |
| [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Contacts.Read | Contacts.Read | Contacts.Read |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0)  <br>/chats/getAllMembers  <br>Members of all chats in an organization. | Not supported. | Not supported. | ChatMember.Read.All, ChatMember.ReadWrite.All, Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0)  <br>/chats/{id}/members  <br>Members of a particular chat. | ChatMember.Read, ChatMember.ReadWrite, Chat.ReadBasic, Chat.Read, Chat.ReadWrite | Not supported. | ChatMember.Read.Chat\*, Chat.Manage.Chat\*, ChatMember.Read.All, ChatMember.ReadWrite.All, Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0)  <br>/appCatalogs/teamsApps/{id}/installedToChats/getAllMembers  <br>Chat members for all chats in an organization where a particular Teams app is installed. | Not supported. | Not supported. | ChatMember.Read.WhereInstalled, ChatMember.ReadWrite.WhereInstalled, Chat.ReadBasic.WhereInstalled, Chat.Read.WhereInstalled, Chat.ReadWrite.WhereInstalled |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0)  <br>/teams/getAllMembers  <br>Members in all teams in an organization. | Not supported. | Not supported. | TeamMember.Read.All, TeamMember.ReadWrite.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0)  <br>/teams/{id}/members  <br>Members in a particular team. | TeamMember.Read.All | Not supported. | TeamMember.Read.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0)  <br>/teams/{id}/channels/getAllMembers  <br>Members in all private channels of a particular team. | Not supported. | Not supported. | ChannelMember.Read.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) \(/teams/getAllChannels/getAllMembers\) | Not supported. | Not supported. | ChannelMember.Read.All |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) \(user's personal OneDrive\) | Not supported. | Files.ReadWrite | Not supported. |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) \(OneDrive for Business\) | Files.ReadWrite.All | Not supported. | Files.ReadWrite.All |
| [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Calendars.Read | Calendars.Read | Calendars.Read |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Group.Read.All | Not supported. | Group.Read.All |
| [group conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) | Group.Read.All | Not supported. | Not supported. |
| [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) | Sites.ReadWrite.All | Not supported. | Sites.ReadWrite.All |
| [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Mail.ReadBasic, Mail.Read | Mail.ReadBasic, Mail.Read | Mail.Read |
| [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/offerShiftRequests\)  <br>Changes to any offer shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/openShiftChangeRequests\)  <br>Changes to any open shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [online meeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) | Not supported | Not supported | OnlineMeetings.Read.All, OnlineMeetings.ReadWrite.All |
| [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence?view=graph-rest-1.0) | Presence.Read.All | Not supported. | Not supported. |
| [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) | Not supported. | Not supported. | Printer.Read.All, Printer.ReadWrite.All |
| [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) | Not supported. | Not supported. | PrintTaskDefinition.ReadWrite.All |
| [security alert](https://learn.microsoft.com/en-us/graph/api/resources/alert?view=graph-rest-1.0) | SecurityEvents.ReadWrite.All | Not supported. | SecurityEvents.ReadWrite.All |
| [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/shifts\)  <br>Changes to any shift in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/swapShiftsChangeRequests\)  <br>Changes to any swap shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0)  <br>/teams  <br>All teams in an organization. | Not supported. | Not supported. | Team.ReadBasic.All, TeamSettings.Read.All |
| [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0)  <br>/teams/{id}  <br>A particular team. | Team.ReadBasic.All, TeamSettings.Read.All | Not supported. | Team.ReadBasic.All, TeamSettings.Read.All |
| [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-1.0)  <br>\(/teams/{id}/schedule/timeOffRequests\)  <br>Changes to any time off request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) | Tasks.ReadWrite | Tasks.ReadWrite | Not supported. |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | User.Read.All | User.Read.All | User.Read.All |

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

## HTTP request

```http
POST /subscriptions/{subscriptionsId}/reauthorize
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `204 No Content` response code.

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
POST https://graph.microsoft.com/v1.0/subscriptions/{subscriptionsId}/reauthorize
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Subscriptions["{subscription-id}"].Reauthorize.PostAsync();
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
graphClient.Subscriptions().BySubscriptionId("subscription-id").Reauthorize().Post(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.subscriptions().bySubscriptionId("{subscription-id}").reauthorize().post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/subscriptions/{subscriptionsId}/reauthorize')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->subscriptions()->bySubscriptionId('subscription-id')->reauthorize()->post()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.ChangeNotifications

Invoke-MgReauthorizeSubscription -SubscriptionId $subscriptionId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.subscriptions.by_subscription_id('subscription-id').reauthorize.post()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
