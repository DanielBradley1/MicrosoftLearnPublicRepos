<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookcommentreply?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-20 -->

# workbookCommentReply resource type

Namespace: microsoft.graph

Represents a reply to an Excel comment.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/workbookcomment-list-replies?view=graph-rest-1.0) | [workbookCommentReply](https://learn.microsoft.com/en-us/graph/api/resources/workbookcommentreply?view=graph-rest-1.0) collection | Get a list of comment replies. |
| [Create](https://learn.microsoft.com/en-us/graph/api/workbookcomment-post-replies?view=graph-rest-1.0) | [workbookCommentReply](https://learn.microsoft.com/en-us/graph/api/resources/workbookcommentreply?view=graph-rest-1.0) | Create a new comment reply. |
| [Get](https://learn.microsoft.com/en-us/graph/api/workbookcommentreply-get?view=graph-rest-1.0) | [workbookCommentReply](https://learn.microsoft.com/en-us/graph/api/resources/workbookcommentreply?view=graph-rest-1.0) | Read the properties and relationships of a reply. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | The content of the reply. |
| contentType | String | The content type for the reply. |
| id | String | The unique identifier for the reply. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "content": "String",
  "contentType": "String",
  "id": "String (identifier)"
}
```
