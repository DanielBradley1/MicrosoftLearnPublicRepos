<!-- Source: https://learn.microsoft.com/en-us/graph/api/subscription-getvapidpublickey?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# subscription: getVapidPublicKey

Namespace: microsoft.graph

Get the public key information required to validate push notifications according to [RFC 8292](https://www.rfc-editor.org/rfc/rfc8292.html) specifications.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Depending on the resource and the permission type \(delegated or application\) requested, the permission specified in the following table is the least privileged required to call this API. To learn more, including [taking caution](https://learn.microsoft.com/en-us/graph/auth/auth-concepts#best-practices-for-requesting-permissions) before choosing more privileged permissions, search for the following permissions in [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

Note

Some resources support change notifications in multiple scenarios, each of which may require different permissions. In those cases, use the resource path to differentiate the scenarios.

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [aiInteraction](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api/ai-services/interaction-export/resources/aiinteraction)  <br>`copilot/users/{userId}/interactionHistory/getAllEnterpriseInteractions`  <br>Copilot AI interactions that a particular user is part of. | AiEnterpriseInteraction.Read | Not supported. | AiEnterpriseInteraction.Read.All, AiEnterpriseInteraction.Read.User |
| [aiInteraction](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api/ai-services/interaction-export/resources/aiinteraction)  <br>`copilot/interactionHistory/getAllEnterpriseInteractions`  <br>Copilot AI interactions in an organization. | Not supported. | Not supported. | AiEnterpriseInteraction.Read.All |
| [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0) | Not supported. | Not supported. | CallRecords.Read.All |
| [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0)  <br>`communications/onlineMeetings/getAllRecordings`  <br>Any recording becomes available in the tenant. | Not supported. | Not supported. | OnlineMeetingRecording.Read.All |
| [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0)  <br>`communications/onlineMeetings/{onlineMeetingId}/recordings`  <br>Any recording becomes available for a specific meeting. | OnlineMeetingRecording.Read.All | Not supported. | OnlineMeetingRecording.Read.All |
| [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0)  <br>`users/{userId}/onlineMeetings/getAllRecordings`  <br>A call recording that becomes available in a meeting organized by a specific user. | OnlineMeetingRecording.Read.All | Not supported. | OnlineMeetingRecording.Read.All |
| [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0)  <br>`communications/onlineMeetings/getAllTranscripts`  <br>Any transcript becomes available in the tenant. | Not supported. | Not supported. | OnlineMeetingTranscript.Read.All |
| [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0)  <br>`communications/onlineMeetings/{onlineMeetingId}/transcripts`  <br>Any transcript becomes available for a specific meeting. | OnlineMeetingTranscript.Read.All | Not supported. | OnlineMeetingTranscript.Read.All |
| [callTranscript](https://learn.microsoft.com/en-us/graph/api/resources/calltranscript?view=graph-rest-1.0)  <br>`users/{userId}/onlineMeetings/getAllTranscripts`  <br>A call transcript that becomes available in a meeting organized by a specific user. | OnlineMeetingTranscript.Read.All | Not supported. | OnlineMeetingTranscript.Read.All |
| [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0)  <br>`/teams/getAllChannels`  <br>All channels in an organization. | Not supported. | Not supported. | Channel.ReadBasic.All, ChannelSettings.Read.All |
| [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0)  <br>`/teams/{id}/channels`  <br>All channels in a particular team in an organization. | Channel.ReadBasic.All, ChannelSettings.Read.All | Not supported. | Channel.ReadBasic.All, ChannelSettings.Read.All |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0)  <br>`/chats`  <br>All chats in an organization. | Not supported. | Not supported. | Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0)  <br>`/chats/{id}`  <br>A particular chat. | Chat.ReadBasic, Chat.Read, Chat.ReadWrite | Not supported. | ChatSettings.Read.Chat, ChatSettings.ReadWrite.Chat, Chat.Manage.Chat, Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0)  <br>`/appCatalogs/teamsApps/{id}/installedToChats`  <br>All chats in an organization where a particular Teams app is installed. | Not supported. | Not supported. | Chat.ReadBasic.WhereInstalled, Chat.Read.WhereInstalled, Chat.ReadWrite.WhereInstalled |
| [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0)  <br>`/users/{id}/chats`  <br>All chats that a particular user is part of. | Chat.ReadBasic, Chat.Read, Chat.ReadWrite | Not supported. | Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>`/teams/{id}/channels/{id}/messages`  <br>All messages and replies in a particular channel. | ChannelMessage.Read.All, Group.Read.All, Group.ReadWrite.All | Not supported. | ChannelMessage.Read.Group, ChannelMessage.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>`/teams/getAllMessages`  <br>All channel messages in organization. | Not supported. | Not supported. | ChannelMessage.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>`/chats/{id}/messages`  <br>All messages in a chat. | Chat.Read, Chat.ReadWrite | Not supported. | Chat.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>`/chats/getAllMessages`  <br>All chat messages in an organization. | Not supported. | Not supported. | Chat.Read.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>`/users/{id}/chats/getAllMessages`  <br>Chat messages for all chats a particular user is part of. | Chat.Read, Chat.ReadWrite | Not supported. | Chat.Read.All, Chat.ReadWrite.All |
| [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)  <br>`/appCatalogs/teamsApps/{id}/installedToChats/getAllMessages`  <br>Chat messages for all chats in an organization where a particular Teams app is installed. | Not supported. | Not supported. | Chat.Read.WhereInstalled, Chat.ReadWrite.WhereInstalled |
| [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Contacts.Read | Contacts.Read | Contacts.Read |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0)  <br>`/chats/getAllMembers`  <br>Members of all chats in an organization. | Not supported. | Not supported. | ChatMember.Read.All, ChatMember.ReadWrite.All, Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0)  <br>`/chats/{id}/members`  <br>Members of a particular chat. | ChatMember.Read, ChatMember.ReadWrite, Chat.ReadBasic, Chat.Read, Chat.ReadWrite | Not supported. | ChatMember.Read.Chat, Chat.Manage.Chat, ChatMember.Read.All, ChatMember.ReadWrite.All, Chat.ReadBasic.All, Chat.Read.All, Chat.ReadWrite.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0)  <br>`/appCatalogs/teamsApps/{id}/installedToChats/getAllMembers`  <br>Chat members for all chats in an organization where a particular Teams app is installed. | Not supported. | Not supported. | ChatMember.Read.WhereInstalled, ChatMember.ReadWrite.WhereInstalled, Chat.ReadBasic.WhereInstalled, Chat.Read.WhereInstalled, Chat.ReadWrite.WhereInstalled |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0)  <br>`/teams/{id}/members`  <br>Members in a particular team. | TeamMember.Read.All | Not supported. | TeamMember.Read.All |
| [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0)  <br>`/teams/{id}/channels/getAllMembers`  <br>Members in all private channels of a particular team. | Not supported. | Not supported. | ChannelMember.Read.All |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) \(user's personal OneDrive\) | Not supported. | Files.ReadWrite | Not supported. |
| [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) \(OneDrive for work or school\) | Files.ReadWrite.All | Not supported. | Files.ReadWrite.All |
| [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Calendars.Read | Calendars.Read | Calendars.Read |
| [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) | Group.Read.All | Not supported. | Group.Read.All |
| [group conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) | Group.Read.All | Not supported. | Not supported. |
| [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) | Sites.Read.All | Not supported. | Sites.Read.All |
| [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Mail.ReadBasic, Mail.Read | Mail.ReadBasic, Mail.Read | Mail.Read |
| [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-1.0)  <br>`/teams/{id}/schedule/offerShiftRequests`  <br>Changes to any offer shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest?view=graph-rest-1.0)  <br>`/teams/{id}/schedule/openShiftChangeRequests`  <br>Changes to any open shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence?view=graph-rest-1.0) | Presence.Read.All | Not supported. | Not supported. |
| [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) | Not supported. | Not supported. | Printer.Read.All, Printer.ReadWrite.All |
| [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) | Not supported. | Not supported. | PrintTaskDefinition.ReadWrite.All |
| [security alert](https://learn.microsoft.com/en-us/graph/api/resources/alert?view=graph-rest-1.0) | SecurityEvents.ReadWrite.All | Not supported. | SecurityEvents.ReadWrite.All |
| [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0)  <br>`/teams/{id}/schedule/shifts`  <br>Changes to any shift in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-1.0)  <br>`/teams/{id}/schedule/swapShiftsChangeRequests`  <br>Changes to any swap shift request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0)  <br>`/teams`  <br>All teams in an organization. | Not supported. | Not supported. | Team.ReadBasic.All, TeamSettings.Read.All |
| [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0)  <br>`/teams/{id}`  <br>A particular team. | Team.ReadBasic.All, TeamSettings.Read.All | Not supported. | Team.ReadBasic.All, TeamSettings.Read.All |
| [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-1.0)  <br>`/teams/{id}/schedule/timeOffRequests`  <br>Changes to any time off request in a team. | Schedule.Read.All, Schedule.ReadWrite.All | Not supported. | Schedule.Read.All, Schedule.ReadWrite.All |
| [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0) | Tasks.ReadWrite | Tasks.ReadWrite | Tasks.ReadWrite.All |
| [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | User.Read.All | User.Read.All | User.Read.All |
| [virtualEventWebinar](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0) | VirtualEvent.Read | Not supported. | VirtualEvent.Read.All |
| [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) | VirtualEvent.Read | Not supported. | VirtualEvent.Read.All |

Note

The following permissions use [resource-specific consent](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/rsc/resource-specific-consent):

- OnlineMeetingRecording.Read.Chat
- OnlineMeetingTranscript.Read.Chat
- ChatSettings.Read.Chat
- ChatSettings.ReadWrite.Chat
- Chat.Manage.Chat
- ChannelMessage.Read.Group
- ChatMember.Read.Chat
- AiEnterpriseInteraction.Read.User

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

More limitations apply to subscriptions on OneDrive items. The limitations apply to creating as well as managing \(getting, updating, and deleting\) subscriptions.

On a personal OneDrive, you can subscribe to the root folder or any subfolder in that drive. On OneDrive for work or school, you can subscribe to only the root folder. Change notifications are sent for the requested types of changes on the subscribed folder or any file, folder, or other **driveItem** instances in its hierarchy. You can't subscribe to **drive** or **driveItem** instances that aren't folders, such as individual files.

### contact, event, and message

You can subscribe to changes in Outlook **contact**, **event**, or **message** resources and optionally specify in the POST request payload whether to include encrypted resource data in notifications.

Creating and managing \(getting, updating, and deleting\) a subscription requires a read scope to the resource. For example, to get change notifications on messages, your app needs the Mail.Read permission. Outlook change notifications support delegated and application permission scopes. Note the following limitations:

- Delegated permission supports subscribing to items in folders in only the signed-in user's mailbox. For example, you can't use the delegated permission Calendars.Read to subscribe to events in another user’s mailbox.
- To subscribe to change notifications of Outlook contacts, events, or messages in *shared or delegated* folders:

  - Use the corresponding application permission to subscribe to changes of items in a folder or mailbox of *any* user in the tenant.
  - Don't use the Outlook sharing permissions \(Contacts.Read.Shared, Calendars.Read.Shared, Mail.Read.Shared, and their read/write counterparts\), as they do **not** support subscribing to change notifications on items in shared or delegated folders.

### onlineMeetings, presence

**onlineMeetings** and **presence** subscriptions require encryption for notifications with resource data. Subscription creation fails if **encryptionCertificate** and **encryptionCertificateId** aren't specified if resource data is desired in notifications. For more information, see:

- [Set up Microsoft Graph change notifications with resource data \(rich notifications\)](https://learn.microsoft.com/en-us/graph/change-notifications-with-resource-data).
- [Get change notifications for online meetings](https://learn.microsoft.com/en-us/graph/changenotifications-for-onlinemeeting).

### virtualEventWebinar

Subscriptions on virtual events support only basic notifications and are limited to a few entities of a virtual event. For more information about the supported subscription types, see [Get change notifications for Microsoft Teams virtual event updates](https://learn.microsoft.com/en-us/graph/changenotifications-for-virtualevent).

## HTTP request

```http
GET /subscriptions/getVapidPublicKey
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a String in the response body.

## Examples

### Request

The following example shows a request.

```msgraph
GET https://graph.microsoft.com/v1.0/subscriptions/getVapidPublicKey
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
   "value": "BNWw_dXp4bP5aw7K0mw2Fg4JjqyNJxnJKVWZ7MXuAVDK8VKlqq7h8JfEKWgJOLHFXlmVQK1vUk1n4JmGzNqeZrQ"
}
```
