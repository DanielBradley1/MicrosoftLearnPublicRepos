<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-19 -->

# conversation resource type

Namespace: microsoft.graph

A conversation is a collection of [threads](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0), and a thread contains posts to that thread. All threads and posts in a conversation share the same subject.

This resource supports subscribing to [change notifications](https://learn.microsoft.com/en-us/graph/change-notifications-overview).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/group-list-conversations?view=graph-rest-1.0) | [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) collection | Get the list of conversations in this group. |
| [Create](https://learn.microsoft.com/en-us/graph/api/group-post-conversations?view=graph-rest-1.0) | [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) | Create a new conversation by including a thread and a post. |
| [Get](https://learn.microsoft.com/en-us/graph/api/conversation-get?view=graph-rest-1.0) | [conversation](https://learn.microsoft.com/en-us/graph/api/resources/conversation?view=graph-rest-1.0) | Read properties and relationships of conversation object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/conversation-delete?view=graph-rest-1.0) | None | Delete conversation object. |
| [List conversation threads](https://learn.microsoft.com/en-us/graph/api/conversation-list-threads?view=graph-rest-1.0) | [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) collection | Get all the threads in a group conversation. |
| [Create conversation thread](https://learn.microsoft.com/en-us/graph/api/conversation-post-threads?view=graph-rest-1.0) | [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) collection | Create a thread in the specified conversation. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hasAttachments | Boolean | Indicates whether any of the posts within this Conversation has at least one attachment. Supports `$filter` \(`eq`, `ne`\) and `$search`. |
| id | String | The conversation's unique identifier. Read-only. |
| lastDeliveredDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| preview | String | A short summary from the body of the latest post in this conversation. Supports `$filter` \(`eq`, `ne`, `le`, `ge`\). |
| topic | String | The topic of the conversation. This property can be set when the conversation is created, but it cannot be updated. |
| uniqueSenders | String collection | All the users that sent a message to this Conversation. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| threads | [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) collection | A collection of all the conversation threads in the conversation. A navigation property. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "hasAttachments": true,
  "id": "string (identifier)",
  "lastDeliveredDateTime": "String (timestamp)",
  "preview": "string",
  "threads": [{"@odata.type": "microsoft.graph.conversationThread"}],
  "topic": "string",
  "uniqueSenders": ["string"]
}
```
