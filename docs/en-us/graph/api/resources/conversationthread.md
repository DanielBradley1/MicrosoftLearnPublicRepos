<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-20 -->

# conversationThread resource type

Namespace: microsoft.graph

A conversationThread is a collection of [posts](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0).

The last post's recipients collection is the aggregated recipients of the entire thread. A thread can have a growing collection of recipients. A new thread is created when a recipient is removed from the thread.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/group-list-threads?view=graph-rest-1.0) | [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) collection | Get all the threads of a group. |
| [Create](https://learn.microsoft.com/en-us/graph/api/group-post-threads?view=graph-rest-1.0) | [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) | Start a new conversation by first creating a thread. A new conversation, conversation thread, and post are created in the group. |
| [Get](https://learn.microsoft.com/en-us/graph/api/conversationthread-get?view=graph-rest-1.0) | [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) | Get a specific thread that belongs to a group. |
| [Update](https://learn.microsoft.com/en-us/graph/api/conversationthread-update?view=graph-rest-1.0) | [conversationThread](https://learn.microsoft.com/en-us/graph/api/resources/conversationthread?view=graph-rest-1.0) | Update conversationThread object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/conversationthread-delete?view=graph-rest-1.0) | None | Delete conversationThread object. |
| [Reply to conversation thread](https://learn.microsoft.com/en-us/graph/api/conversationthread-reply?view=graph-rest-1.0) | None | Reply to this thread by creating a new Post entity. |
| [List posts](https://learn.microsoft.com/en-us/graph/api/conversationthread-list-posts?view=graph-rest-1.0) | [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) collection | Get the posts of the specified thread. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ccRecipients | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The Cc: recipients for the thread.  <br>  <br>Requires `$select` to retrieve. |
| hasAttachments | Boolean | Indicates whether any of the posts within this thread has at least one attachment.  <br>  <br>Returned by default. |
| id | String | Read-only.  <br>  <br>Returned by default. |
| isLocked | Boolean | Indicates if the thread is locked.  <br>  <br>Returned by default. |
| lastDeliveredDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`.  <br>  <br>Returned by default. |
| preview | String | A short summary from the body of the latest post in this conversation.  <br>  <br>Returned by default. |
| topic | String | The topic of the conversation. This property can be set when the conversation is created, but it cannot be updated.  <br>  <br>Returned by default. |
| toRecipients | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The To: recipients for the thread.  <br>  <br>Requires `$select` to retrieve. |
| uniqueSenders | String collection | All the users that sent a message to this thread.  <br>  <br>Returned by default. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| posts | [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) collection | Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "ccRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "hasAttachments": true,
  "id": "string (identifier)",
  "isLocked": true,
  "lastDeliveredDateTime": "String (timestamp)",
  "preview": "string",
  "topic": "string",
  "toRecipients": [{"@odata.type": "microsoft.graph.recipient"}],
  "uniqueSenders": ["string"]
}
```
