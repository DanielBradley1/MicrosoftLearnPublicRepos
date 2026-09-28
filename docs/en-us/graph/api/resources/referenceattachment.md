<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/referenceattachment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-08 -->

# referenceAttachment resource type

Namespace: microsoft.graph

A link to a file, such as a text file or Word document, on a OneDrive for work or school cloud drive or other supported storage locations, attached to an event, message, or post.

Derived from [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/attachment-get?view=graph-rest-1.0) | [referenceAttachment](https://learn.microsoft.com/en-us/graph/api/resources/referenceattachment?view=graph-rest-1.0) | Read properties and relationships of referenceAttachment object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/attachment-delete?view=graph-rest-1.0) | None | Delete referenceAttachment object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentType | String | The content type of the attachment. Returned as `null` by default, when not set explicitly. Optional. |
| id | String | The attachment ID. Read-only. |
| isInline | Boolean | Set to true if the attachment appears inline in the body of the embedding object. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the attachment was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| name | String | The text that is displayed below the icon representing the embedded attachment. This value doesn't need to be the actual file name. |
| size | Int32 | The size of the metadata that is stored on the message for the attachment in bytes. This value doesn't indicate the size of the actual file. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "contentType": "string",
  "id": "string (identifier)",
  "isInline": true,
  "lastModifiedDateTime": "String (timestamp)",
  "name": "string",
  "size": 1024
}
```
