<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookcomment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-20 -->

# workbookComment resource type

Namespace: microsoft.graph

Represents a comment in a workbook.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/workbook-list-comments?view=graph-rest-1.0) | [workbookComment](https://learn.microsoft.com/en-us/graph/api/resources/workbookcomment?view=graph-rest-1.0) collection | Get a **workbookComment** object collection. |
| [Get](https://learn.microsoft.com/en-us/graph/api/workbookcomment-get?view=graph-rest-1.0) | [workbookComment](https://learn.microsoft.com/en-us/graph/api/resources/workbookcomment?view=graph-rest-1.0) | Read the properties and relationships of a **workbookComment** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | The content of the comment. |
| contentType | String | The content type of the comment. |
| id | String | The unique identifier of the comment. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| replies | [workbookCommentReply](https://learn.microsoft.com/en-us/graph/api/resources/workbookcommentreply?view=graph-rest-1.0) collection | The list of replies to the comment. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "content": "String",
  "contentType": "String",
  "id": "String (identifier)"
}
```
