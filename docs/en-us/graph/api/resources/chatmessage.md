<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-25 -->

# chatMessage resource type

Namespace: microsoft.graph

Represents an individual chat message within a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) or [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0). The message can be a root message or part of a thread that is defined by the **replyToId** property in the message.

The [targetedChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) resource is a specialized type of chat message that is visible only to specified recipients. For more information, see [targetedChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0).

> **Note**: This resource supports subscribing to changes \(create, update, and delete\) using [change notifications](https://learn.microsoft.com/en-us/graph/api/resources/change-notifications-api-overview?view=graph-rest-1.0). This allows callers to subscribe and get changes in real time. For details, see [Get notifications for messages](https://learn.microsoft.com/en-us/graph/teams-changenotifications-chatMessage).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| **Channel messages** |  |  |
| [List messages in channel](https://learn.microsoft.com/en-us/graph/api/channel-list-messages?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) collection | List of all root messages in a channel. |
| [Create subscription for new channel messages](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions?view=graph-rest-1.0) | [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0) | Listen for new, edited, and deleted messages, and reactions to them. |
| [Get message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-get?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Get a single root message in a channel. |
| [Send message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-post?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Create a new root message in a channel. |
| [Update message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-update?view=graph-rest-1.0) | None | Update the **policyViolation** property of a chat message. |
| [Delete message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-softdelete?view=graph-rest-1.0) | None | Delete the message in a channel. |
| [Undo the deletion of a message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-undosoftdelete?view=graph-rest-1.0) | None | Undelete the message in a channel. |
| [Set reaction to a message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-setreaction?view=graph-rest-1.0) | None | Set reaction to a message in a channel. |
| [Unset reaction to a message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-unsetreaction?view=graph-rest-1.0) | None | Unset reaction to a message in a channel. |
| **Channel message replies** |  |  |
| [List replies to message](https://learn.microsoft.com/en-us/graph/api/chatmessage-list-replies?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) collection | List of all replies to a chat message in channel. |
| [Get reply message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-get?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Get a single reply message in a channel. |
| [Reply to a message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-post-replies?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Reply to an existing chat message in a channel. |
| [Update reply message](https://learn.microsoft.com/en-us/graph/api/chatmessage-update?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Update the **policyViolation** property of a chat message. |
| [Delete reply message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-softdelete?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Delete the single reply message in a channel. |
| [Undo deletion of a reply message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-undosoftdelete?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Undelete the single reply message in a channel. |
| [Set reaction to a message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-setreaction?view=graph-rest-1.0) | None | Set reaction to a message in a channel. |
| [Unset reaction to a message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-unsetreaction?view=graph-rest-1.0) | None | Unset reaction to a message in a channel. |
| **Chat messages** |  |  |
| [List messages in chat](https://learn.microsoft.com/en-us/graph/api/chat-list-messages?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | List chat messages in a chat. |
| [Get message in chat](https://learn.microsoft.com/en-us/graph/api/chatmessage-get?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Get a single chat message in a chat. |
| [Get messages across all chats for user](https://learn.microsoft.com/en-us/graph/api/chats-getallmessages?view=graph-rest-1.0) | [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) collection | Get messages from all chats that a user is a participant in, that includes 1:1 chats, group chats, and meeting chats. |
| [Get delta chat messages for user](https://learn.microsoft.com/en-us/graph/api/chatmessage-delta?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) collection | Get the list of [messages](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) from all [chats](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) in which a user is a participant, including one-on-one chats, group chats, and meeting chats. |
| [Get all channel messages](https://learn.microsoft.com/en-us/graph/api/channel-getallmessages?view=graph-rest-1.0) | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) collection | Get all messages from all channels that a user is a participant in. |
| [Create subscription for new chat messages](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions?view=graph-rest-1.0) | [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0) | Listen for new, edited, and deleted chat messages, and reactions to them. |
| [Send message in chat](https://learn.microsoft.com/en-us/graph/api/chat-post-messages?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Send a chat message in an existing 1:1 or group chat conversation. |
| [Update message in chat](https://learn.microsoft.com/en-us/graph/api/chatmessage-update?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Update the **policyViolation** property of a chat message. |
| [Delete message in chat](https://learn.microsoft.com/en-us/graph/api/chatmessage-softdelete?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Delete the message of a chat. |
| [Undo the deletion of a message in chat](https://learn.microsoft.com/en-us/graph/api/chatmessage-undosoftdelete?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Undelete the message in a chat. |
| [Set reaction to a message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-setreaction?view=graph-rest-1.0) | None | Set reaction to a message in a channel. |
| [Unset reaction to a message in channel](https://learn.microsoft.com/en-us/graph/api/chatmessage-unsetreaction?view=graph-rest-1.0) | None | Unset reaction to a message in a channel. |
| [Reply with quote](https://learn.microsoft.com/en-us/graph/api/chatmessage-replywithquote?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Reply with quote to a single [chat message](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) or multiple chat messages in a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0). |
| **Hosted content** |  |  |
| [List all hosted content](https://learn.microsoft.com/en-us/graph/api/chatmessage-list-hostedcontents?view=graph-rest-1.0) | [chatMessageHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagehostedcontent?view=graph-rest-1.0) collection | Get all hosted contents associated with a message. |
| [Get hosted content](https://learn.microsoft.com/en-us/graph/api/chatmessagehostedcontent-get?view=graph-rest-1.0) | [chatMessageHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagehostedcontent?view=graph-rest-1.0) | Get hosted content \(and its bytes\) for a message. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attachments | [chatMessageAttachment](https://learn.microsoft.com/en-us/graph/api/resources/chatmessageattachment?view=graph-rest-1.0) collection | References to attached objects like files, tabs, meetings etc. |
| body | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | Plaintext/HTML representation of the content of the chat message. Representation is specified by the contentType inside the body. The content is always in HTML if the chat message contains a [chatMessageMention](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagemention?view=graph-rest-1.0). |
| chatId | string | If the message was sent in a chat, represents the identity of the chat. |
| channelIdentity | [channelIdentity](https://learn.microsoft.com/en-us/graph/api/resources/channelidentity?view=graph-rest-1.0) | If the message was sent in a channel, represents identity of the channel. |
| createdDateTime | dateTimeOffset | Timestamp of when the chat message was created. |
| deletedDateTime | dateTimeOffset | Read-only. Timestamp at which the chat message was deleted, or null if not deleted. |
| etag | string | Read-only. Version number of the chat message. |
| eventDetail | [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0) | Read-only. If present, represents details of an event that happened in a **chat**, a **channel**, or a **team**, for example, adding new members. For event messages, the **messageType** property will be set to `systemEventMessage`. |
| from | [chatMessageFromIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagefromidentityset?view=graph-rest-1.0) | Details of the sender of the chat message. Can only be set during [migration](https://learn.microsoft.com/en-us/microsoftteams/platform/graph-api/import-messages/import-external-messages-to-teams). |
| id | String | Read-only. Unique ID of the message. IDs are unique within a chat/channel/reply-to-message, but might be duplicated in other chats/channels/reply-to-messages. |
| importance | chatMessageImportance | The importance of the message. The possible values are: `normal`, `high`, `urgent`, `unknownFutureValue`. |
| lastEditedDateTime | dateTimeOffset | Read-only. Timestamp when edits to the chat message were made. Triggers an "Edited" flag in the Teams UI. If no edits are made the value is `null`. |
| lastModifiedDateTime | dateTimeOffset | Read-only. Timestamp when the chat message is created \(initial setting\) or modified, including when a reaction is added or removed. |
| locale | string | Locale of the chat message set by the client. Always set to `en-us`. |
| mentions | [chatMessageMention](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagemention?view=graph-rest-1.0) collection | List of entities mentioned in the chat message. Supported entities are: user, bot, team, channel, chat, and tag. |
| messageHistory | [chatMessageHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagehistoryitem?view=graph-rest-1.0) collection | List of activity history of a message item, including modification time and actions, such as reactionAdded, reactionRemoved, or reaction changes, on the message. |
| messageType | chatMessageType | The type of chat message. The possible values are: `message`, `chatEvent`, `typing`, `unknownFutureValue`, `systemEventMessage`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `systemEventMessage`. |
| policyViolation | [chatMessagePolicyViolation](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagepolicyviolation?view=graph-rest-1.0) | Defines the properties of a policy violation set by a data loss prevention \(DLP\) application. |
| reactions | [chatMessageReaction](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagereaction?view=graph-rest-1.0) collection | Reactions for this chat message \(for example, Like\). |
| replyToId | string | Read-only. ID of the parent chat message or root chat message of the thread. \(Only applies to chat messages in channels, not chats.\) |
| subject | string | The subject of the chat message, in plaintext. |
| summary | string | Summary text of the chat message that could be used for push notifications and summary views or fall back views. Only applies to channel chat messages, not chat messages in a chat. |
| webUrl | string | Read-only. Link to the message in Microsoft Teams. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| hostedContents | [chatMessageHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagehostedcontent?view=graph-rest-1.0) collection | Content in a message hosted by Microsoft Teams - for example, images or code snippets. |
| replies | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) collection | Replies for a specified message. Supports `$expand` for channel messages. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "attachments": [{"@odata.type": "microsoft.graph.chatMessageAttachment"}],
  "body": {"@odata.type": "microsoft.graph.itemBody"},
  "channelIdentity": {"@odata.type": "microsoft.graph.channelIdentity"},
  "chatId": "String",
  "createdDateTime": "String (timestamp)",
  "deletedDateTime": "String (timestamp)",
  "etag": "String",
  "eventDetail": {"@odata.type": "microsoft.graph.eventMessageDetail"},
  "from": {"@odata.type": "microsoft.graph.chatMessageFromIdentitySet"},
  "id": "String (identifier)",
  "importance": "String",
  "lastEditedDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "locale": "String",
  "mentions": [{"@odata.type": "microsoft.graph.chatMessageMention"}],
  "messageHistory": [{"@odata.type": "microsoft.graph.chatMessageHistoryItem"}],
  "messageType": "String",
  "policyViolation": {"@odata.type": "microsoft.graph.chatMessagePolicyViolation"},
  "reactions": [{"@odata.type": "microsoft.graph.chatMessageReaction"}],
  "replyToId": "String (identifier)",
  "subject": "String",
  "summary": "String",
  "webUrl": "String"
}
```
