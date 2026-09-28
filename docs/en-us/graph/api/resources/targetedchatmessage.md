<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# targetedChatMessage resource type

Namespace: microsoft.graph

Represents a targeted message in Microsoft Teams that is visible only to a specified recipient. Unlike regular messages that are visible to all participants in a group chat or channel, targeted messages provide privacy for bot interactions and app-to-user communications that require user-specific information.

Targeted messages are used in scenarios such as:

- Bot authentication requests in group contexts, where credentials should only be visible to the requesting user.
- Chat summaries for new members, visible only to the joining member.
- Proactive and reactive bot messages that contain sensitive or user-specific information.

Inherits from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get all targeted messages](https://learn.microsoft.com/en-us/graph/api/userteamwork-getalltargetedmessages?view=graph-rest-1.0) | [targetedChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) collection | Get all [targeted messages](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) sent to a specific user in group chats and channels. |
| [Get all retained targeted messages](https://learn.microsoft.com/en-us/graph/api/userteamwork-getallretainedtargetedmessages?view=graph-rest-1.0) | [targetedChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) collection | Get all retained [targeted messages](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) sent to a specific user in group chats and channels. |
| [Delete targeted message from channel](https://learn.microsoft.com/en-us/graph/api/userteamwork-deletetargetedmessage?view=graph-rest-1.0) | None | Delete a specific [targeted message](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) from a channel context. |
| [Delete targeted message from chat](https://learn.microsoft.com/en-us/graph/api/chat-delete-targetedmessages?view=graph-rest-1.0) | None | Delete a specific [targeted message](https://learn.microsoft.com/en-us/graph/api/resources/targetedchatmessage?view=graph-rest-1.0) from a chat context. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attachments | [chatMessageAttachment](https://learn.microsoft.com/en-us/graph/api/resources/chatmessageattachment?view=graph-rest-1.0) collection | References to attached objects like files, tabs, meetings, or other items. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| body | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The content of the message. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| chatId | String | The unique identifier of the chat if the targeted message was sent in a group chat context. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| channelIdentity | [channelIdentity](https://learn.microsoft.com/en-us/graph/api/resources/channelidentity?view=graph-rest-1.0) | The channel and team information if the targeted message was sent in a channel context. Contains the **channelId** and **teamId** properties. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time when the message was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| deletedDateTime | DateTimeOffset | The date and time when the message was deleted. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. Only applicable for retained messages. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| etag | String | Version number of the message. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| eventDetail | [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0) | Details about the event if this message represents a system event. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| from | [chatMessageFromIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagefromidentityset?view=graph-rest-1.0) | Details about the sender of the targeted message. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| id | String | Unique identifier of the message. The message ID is only unique within the context of a single conversation \(chat or channel\) for a specific user. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| importance | chatMessageImportance | The importance of the message. The possible values are: `normal`, `high`, `urgent`, `unknownFutureValue`. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| lastEditedDateTime | DateTimeOffset | Date and time when the message was last edited. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | Date and time when the message or any of its properties was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| locale | String | The locale of the message as set by the client, formatted as `en-us`. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| mentions | [chatMessageMention](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagemention?view=graph-rest-1.0) collection | List of entities mentioned in the message. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| messageHistory | [chatMessageHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagehistoryitem?view=graph-rest-1.0) collection | History of edits applied to the message. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| messageType | chatMessageType | The type of message. The possible values are: `message`, `chatEvent`, `typing`, `unknownFutureValue`, `systemEventMessage`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `systemEventMessage`. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| policyViolation | [chatMessagePolicyViolation](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagepolicyviolation?view=graph-rest-1.0) | Information about policy violations applied to the message by data loss prevention \(DLP\) applications. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| reactions | [chatMessageReaction](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagereaction?view=graph-rest-1.0) collection | The reactions applied to the message \(for example, like, heart, and laugh\). Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| recipient | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | The intended recipient of the targeted message. |
| replyToId | String | The ID of the parent message or root message of the thread. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| subject | String | The subject of the message. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| summary | String | Summary text of the message that can be used for notifications or summary views. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| webUrl | String | The link to the message in Microsoft Teams. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| hostedContents | [chatMessageHostedContent](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagehostedcontent?view=graph-rest-1.0) collection | Content hosted in the message, such as images or code snippets. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| replies | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) collection | Replies to the message. Currently not supported for targeted messages. Inherited from [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.targetedChatMessage",
  "attachments": [{"@odata.type": "microsoft.graph.chatMessageAttachment"}],
  "body": {"@odata.type": "microsoft.graph.itemBody"},
  "chatId": "String",
  "channelIdentity": {"@odata.type": "microsoft.graph.channelIdentity"},
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
  "recipient": {"@odata.type": "microsoft.graph.identity"},
  "replyToId": "String",
  "subject": "String",
  "summary": "String",
  "webUrl": "String"
}
```
