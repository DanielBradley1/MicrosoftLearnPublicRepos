<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# note resource type

Namespace: microsoft.graph

Represents a simple note in the user's *Notes* folder. Notes support text content with optional inline image attachments, and are suitable for quick capture scenarios.

Inherits from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/user-list-notes?view=graph-rest-1.0) | [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) collection | Get a list of the [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) objects in the user's *Notes* folder. |
| [Create](https://learn.microsoft.com/en-us/graph/api/user-post-notes?view=graph-rest-1.0) | [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) | Create a new [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) in the user's *Notes* folder. |
| [Get](https://learn.microsoft.com/en-us/graph/api/note-get?view=graph-rest-1.0) | [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) | Read the properties and relationships of a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/note-update?view=graph-rest-1.0) | [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) | Update the properties of a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/note-delete?view=graph-rest-1.0) | None | Delete a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) object. |
| [Get delta](https://learn.microsoft.com/en-us/graph/api/note-delta?view=graph-rest-1.0) | [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) collection | Get a set of [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) objects that were added, updated, or deleted in the user's *Notes* folder since the last delta query. |
| [List attachments](https://learn.microsoft.com/en-us/graph/api/note-list-attachments?view=graph-rest-1.0) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) collection | Get the list of file attachments associated with a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0). |
| [Create attachment](https://learn.microsoft.com/en-us/graph/api/note-post-attachments?view=graph-rest-1.0) | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) | Create a [fileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/fileattachment?view=graph-rest-1.0) object, which adds an inline image attachment to a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0). |
| [Delete attachment](https://learn.microsoft.com/en-us/graph/api/attachment-delete?view=graph-rest-1.0) | None | Delete an inline image attachment from a [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| body | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The content of the note. Supports `text` or `html` content types. |
| bodyPreview | String | Auto-generated preview of the note body content \(first ~255 characters, plain text\). Read-only. |
| categories | String collection | The categories associated with the note. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| changeKey | String | Version identifier used for optimistic concurrency control via the `If-Match` header. Read-only. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time when the note was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. Supports `$filter` \(`eq`, `ne`, `ge`, `le`, `gt`, `lt`\). Read-only. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| hasAttachments | Boolean | Indicates whether the note has file attachments. Supports `$filter` \(`eq`\). Read-only. |
| id | String | The unique identifier for the note. Read-only. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| isDeleted | Boolean | Indicates whether the note is soft-deleted. Read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the note was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. Supports `$filter` \(`eq`, `ne`, `ge`, `le`, `gt`, `lt`\) and `$orderby`. Read-only. Inherited from [outlookItem](https://learn.microsoft.com/en-us/graph/api/resources/outlookitem?view=graph-rest-1.0). |
| subject | String | The title of the note. Supports `$filter` \(`eq`, `ne`, `startsWith`\) and `$orderby`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| attachments | [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0) collection | The file attachments for the note. Only inline image attachments \(image/png, image/jpeg, image/gif, or image/bmp\) are supported, with a maximum size of 3 MB per attachment. Use `$expand` to retrieve attachments. |
| extensions | [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-1.0) collection | The collection of open extensions defined for the note. |
| multiValueExtendedProperties | [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of multi-value extended properties defined for the note. |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0) collection | The collection of single-value extended properties defined for the note. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.note",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "changeKey": "String",
  "categories": [
    "String"
  ],
  "subject": "String",
  "body": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "bodyPreview": "String",
  "isDeleted": "Boolean",
  "hasAttachments": "Boolean"
}
```
