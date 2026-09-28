<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/pinnedchatmessageinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# pinnedChatMessageInfo resource type

Namespace: microsoft.graph

Represents an individual pinned message in a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List pinned messages](https://learn.microsoft.com/en-us/graph/api/chat-list-pinnedmessages?view=graph-rest-1.0) | [pinnedChatMessageInfo](https://learn.microsoft.com/en-us/graph/api/resources/pinnedchatmessageinfo?view=graph-rest-1.0) collection | Get a list of [pinnedChatMessages](https://learn.microsoft.com/en-us/graph/api/resources/pinnedchatmessageinfo?view=graph-rest-1.0) in a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0). |
| [Pin message](https://learn.microsoft.com/en-us/graph/api/chat-post-pinnedmessages?view=graph-rest-1.0) | [pinnedChatMessageInfo](https://learn.microsoft.com/en-us/graph/api/resources/pinnedchatmessageinfo?view=graph-rest-1.0) | Pin a chat message in the specified [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0). |
| [Unpin message](https://learn.microsoft.com/en-us/graph/api/chat-delete-pinnedmessages?view=graph-rest-1.0) | None | Unpin a message from a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| message | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) | Represents details about the chat message that is pinned. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.pinnedChatMessageInfo",
  "id": "String (identifier)"
}
```
