<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatviewpoint?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# chatViewpoint resource type

Namespace: microsoft.graph

Represents user-specific properties of a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0). These properties might change based on who the caller of the API is.

> **Note:** Currently, only the [List chats](https://learn.microsoft.com/en-us/graph/api/chat-list?view=graph-rest-1.0) operation supports **chatViewpoint**.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isHidden | Boolean | Indicates whether the chat is hidden for the current user. |
| lastMessageReadDateTime | DateTimeOffset | Represents the dateTime up until which the current user has read [chatMessages](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) in a specific chat. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.chatViewpoint",
  "isHidden": "Boolean",
  "lastMessageReadDateTime": "String (timestamp)"
}
```
