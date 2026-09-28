<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-16 -->

# chat resource type

Namespace: microsoft.graph

A chat is a collection of [chatMessages](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) between one or more participants. Participants can be users or apps.

> **Note**: If the chat is associated with an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) instance, then some of the listed methods will transitively impact the meeting.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| **Chat management** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/chat-list?view=graph-rest-1.0) | [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) collection | Get the list of chats a user is part of. |
| [Create](https://learn.microsoft.com/en-us/graph/api/chat-post?view=graph-rest-1.0) | [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) | Create a new chat. |
| [Get](https://learn.microsoft.com/en-us/graph/api/chat-get?view=graph-rest-1.0) | [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) | Read properties and relationships of the chat. |
| [Update](https://learn.microsoft.com/en-us/graph/api/chat-patch?view=graph-rest-1.0) | [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) | Update properties of the chat. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/chat-delete?view=graph-rest-1.0) | None | Delete a chat. |
| [List members](https://learn.microsoft.com/en-us/graph/api/chat-list-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | Get the list of all users in the chat. |
| [Add member](https://learn.microsoft.com/en-us/graph/api/chat-post-members?view=graph-rest-1.0) | Location header | Add a user to the chat. |
| [Get member](https://learn.microsoft.com/en-us/graph/api/chat-get-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) | Get a single user in the chat. |
| [Remove member](https://learn.microsoft.com/en-us/graph/api/chat-delete-members?view=graph-rest-1.0) | None | Remove a user from the chat. |
| [Get chat between user and app](https://learn.microsoft.com/en-us/graph/api/userscopeteamsappinstallation-get-chat?view=graph-rest-1.0) | [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) | Get one-on-one chat between user and the app |
| [Remove all access for user](https://learn.microsoft.com/en-us/graph/api/chat-removeallaccessforuser?view=graph-rest-1.0) | None | Remove access to a chat for a user. |
| [Start migration](https://learn.microsoft.com/en-us/graph/api/chat-startmigration?view=graph-rest-1.0) | [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) | Start the migration of external messages by enabling migration mode in an existing [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0). |
| [Complete migration](https://learn.microsoft.com/en-us/graph/api/chat-completemigration?view=graph-rest-1.0) | [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) | Complete the migration of external messages by removing migration mode from a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0). |
| **Messages** |  |  |
| [List messages in a chat](https://learn.microsoft.com/en-us/graph/api/chat-list-messages?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Get messages in a chat. |
| [Get message reply](https://learn.microsoft.com/en-us/graph/api/chatmessage-get?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Get a single message in a chat. |
| [Get messages across all chats](https://learn.microsoft.com/en-us/graph/api/chats-getallmessages?view=graph-rest-1.0) | [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) collection | Get messages from all chats that a user is a participant in. |
| [Get retained messages across all chats](https://learn.microsoft.com/en-us/graph/api/chat-getallretainedmessages?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) collection | Get all retained [messages](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) from all [chats](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) that a user is a participant in, including one-on-one chats, group chats, and meeting chats. |
| [Get delta chat messages for user](https://learn.microsoft.com/en-us/graph/api/chatmessage-delta?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) collection | Get the list of [messages](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) from all [chats](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) in which a user is a participant, including one-on-one chats, group chats, and meeting chats. |
| **Apps** |  |  |
| [List apps in chat](https://learn.microsoft.com/en-us/graph/api/chat-list-installedapps?view=graph-rest-1.0) | [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) collection | List apps installed in a chat \(and associated meeting\). |
| [Get app installed in chat](https://learn.microsoft.com/en-us/graph/api/chat-get-installedapps?view=graph-rest-1.0) | [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) | Get a specific app installed in a chat \(and associated meeting\). |
| [Add app in chat](https://learn.microsoft.com/en-us/graph/api/chat-post-installedapps?view=graph-rest-1.0) |  | Add \(install\) an app in a chat \(and associated meeting\). |
| [Upgrade app installed in chat](https://learn.microsoft.com/en-us/graph/api/chat-teamsappinstallation-upgrade?view=graph-rest-1.0) | None | Update to the latest version of the app installed in chat \(and associated meeting\). |
| [Remove app from chat](https://learn.microsoft.com/en-us/graph/api/chat-delete-installedapps?view=graph-rest-1.0) | None | Remove \(uninstall\) app from a chat \(and associated meeting\). |
| [List permission grants](https://learn.microsoft.com/en-us/graph/api/chat-list-permissiongrants?view=graph-rest-1.0) | [resourceSpecificPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermissiongrant?view=graph-rest-1.0) collection | List permissions granted to the apps in this chat. |
| **Tabs** |  |  |
| [List tabs in chat](https://learn.microsoft.com/en-us/graph/api/chat-list-tabs?view=graph-rest-1.0) | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) | List tabs pinned to a chat \(and associated meeting\). |
| [Get tab in chat](https://learn.microsoft.com/en-us/graph/api/chat-get-tabs?view=graph-rest-1.0) | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) | Get a specific tab pinned to a chat \(and associated meeting\). |
| [Add tab to chat](https://learn.microsoft.com/en-us/graph/api/chat-post-tabs?view=graph-rest-1.0) | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) | Add \(pin\) a tab to a chat \(and associated meeting\). |
| [Update tab in chat](https://learn.microsoft.com/en-us/graph/api/chat-patch-tabs?view=graph-rest-1.0) | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) | Update the properties of a tab in a chat \(and associated meeting\). |
| [Remove tab from chat](https://learn.microsoft.com/en-us/graph/api/chat-delete-tabs?view=graph-rest-1.0) | None | Remove \(unpin\) a tab from a chat \(and associated meeting\). |
| **Pinned messages** |  |  |
| [List pinned messages](https://learn.microsoft.com/en-us/graph/api/chat-list-pinnedmessages?view=graph-rest-1.0) | [pinnedChatMessageInfo](https://learn.microsoft.com/en-us/graph/api/resources/pinnedchatmessageinfo?view=graph-rest-1.0) collection | Get a list of pinned messages in a chat. |
| [Pin message](https://learn.microsoft.com/en-us/graph/api/chat-post-pinnedmessages?view=graph-rest-1.0) | [pinnedChatMessageInfo](https://learn.microsoft.com/en-us/graph/api/resources/pinnedchatmessageinfo?view=graph-rest-1.0) | Pin a chat message in a chat. |
| [Unpin message](https://learn.microsoft.com/en-us/graph/api/chat-delete-pinnedmessages?view=graph-rest-1.0) | None | Unpin a message from a chat. |

> **Note:** When using application permissions, be sure you know how to get the chat ID. Because listing chats with application permissions is not supported, not all scenarios are possible. It is possible to get chat IDs with delegated permissions, and from [change notifications for /chats/getAllMessages](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions?view=graph-rest-1.0) with application permissions.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| chatType | [chatType](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0#chattype-values) | Specifies the type of chat. The possible values are: `group`, `oneOnOne`, `meeting`, `unknownFutureValue`. |
| createdDateTime | dateTimeOffset | Date and time at which the chat was created. Read-only. |
| id | String | The chat's unique identifier. Read-only. |
| isHiddenForAllMembers | Boolean | Indicates whether the chat is hidden for all its members. Read-only. |
| lastUpdatedDateTime | dateTimeOffset | Date and time at which the chat was renamed or the list of members was last changed. Read-only. |
| migrationMode | [migrationMode](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0#migrationmode-values) | Indicates whether a chat is in migration mode. This value is `null` for chats that never entered migration mode. The possible values are: `inProgress`, `completed`, `unknownFutureValue`. |
| onlineMeetingInfo | [teamworkOnlineMeetingInfo](https://learn.microsoft.com/en-us/graph/api/resources/teamworkonlinemeetinginfo?view=graph-rest-1.0) | Represents details about an online meeting. If the chat isn't associated with an online meeting, the property is empty. Read-only. |
| originalCreatedDateTime | dateTimeOffset | Timestamp of the original creation time for the chat. The value is `null` if the chat never entered migration mode. |
| tenantId | String | The identifier of the tenant in which the chat was created. Read-only. |
| topic | String | \(Optional\) Subject or topic for the chat. Only available for group chats. |
| viewpoint | [chatViewpoint](https://learn.microsoft.com/en-us/graph/api/resources/chatviewpoint?view=graph-rest-1.0) | Represents caller-specific information about the chat, such as the last message read date and time. This property is populated only when the request is made in a delegated context. |
| webUrl | String | The URL for the chat in Microsoft Teams. The URL should be treated as an opaque blob, and not parsed. Read-only. |

### chatType values

| Member | Description |
| :--- | :--- |
| oneOnOne | Indicates that the chat is a 1:1 chat. The roster size is fixed for this type of chat; members can't be removed/added. |
| group | Indicates that the chat is a group chat. The roster size \(of at least two people\) can be updated for this type of chat. Members can be removed/added later. |
| meeting | Indicates that the chat is associated with an online meeting. This type of chat is only created as part of the creation of an online meeting. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| installedApps | [teamsAppInstallation](https://learn.microsoft.com/en-us/graph/api/resources/teamsappinstallation?view=graph-rest-1.0) collection | A collection of all the apps in the chat. Nullable. |
| lastMessagePreview | [chatMessageInfo](https://learn.microsoft.com/en-us/graph/api/resources/chatmessageinfo?view=graph-rest-1.0) | Preview of the last message sent in the chat. Null if no messages were sent in the chat. Currently, only the [list chats](https://learn.microsoft.com/en-us/graph/api/chat-list?view=graph-rest-1.0) operation supports this property. |
| members | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | A collection of all the members in the chat. Nullable. |
| messages | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) collection | A collection of all the messages in the chat. Nullable. |
| permissionGrants | [resourceSpecificPermissionGrant](https://learn.microsoft.com/en-us/graph/api/resources/resourcespecificpermissiongrant?view=graph-rest-1.0) collection | A collection of permissions granted to apps for the chat. |
| pinnedMessages | [pinnedChatMessageInfo](https://learn.microsoft.com/en-us/graph/api/resources/pinnedchatmessageinfo?view=graph-rest-1.0) collection | A collection of all the pinned messages in the chat. Nullable. |
| tabs | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) collection | A collection of all the tabs in the chat. Nullable. |
| targetedMessages | [targetedChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) collection | A collection of targeted messages in the chat that are visible only to specific users. Nullable. You can't expand this relationship using `$expand`. Targeted messages can also be retrieved via the [userTeamwork: getAllTargetedMessages](https://learn.microsoft.com/en-us/graph/api/userteamwork-getalltargetedmessages?view=graph-rest-1.0) API. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "chatType": "String",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "isHiddenForAllMembers": "Boolean",
  "lastUpdatedDateTime": "String (timestamp)",
  "migrationMode": "String",
  "onlineMeetingInfo": {"@odata.type": "microsoft.graph.teamworkOnlineMeetingInfo"},
  "originalCreatedDateTime": "String (timestamp)",
  "tenantId": "String",
  "topic": "String",
  "viewpoint": {"@odata.type": "microsoft.graph.chatViewpoint"},
  "webUrl": "String"
}
```

## Related content

- [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0)
- [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)
- [Chat lifecycle C# sample](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/graph-chat-lifecycle/csharp)
- [Chat lifecycle Node.js sample](https://github.com/OfficeDev/Microsoft-Teams-Samples/blob/main/samples/graph-chat-lifecycle/nodejs)
