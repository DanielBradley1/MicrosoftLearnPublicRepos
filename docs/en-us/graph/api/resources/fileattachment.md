<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/fileattachment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-08 -->

# fileAttachment resource type

Namespace: microsoft.graph

A file \(such as a text file or Word document\) attached to a user [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0), [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0), or [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0).

When creating a file attachment, include the following in the request body:

- `"@odata.type": "#microsoft.graph.fileAttachment"`
- The required properties **name** and **contentBytes**.

Derived from [attachment](https://learn.microsoft.com/en-us/graph/api/resources/attachment?view=graph-rest-1.0).

Note

Make sure to encode the file content in base64 before assigning it to **contentBytes**.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/attachment-get?view=graph-rest-1.0) | [fileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/fileattachment?view=graph-rest-1.0) | Read properties, relationships, or raw contents of a **fileAttachment** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/attachment-delete?view=graph-rest-1.0) | None | Delete a **fileAttachment** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentBytes | Edm.Binary | The base64-encoded contents of the file. |
| contentId | String | The ID of the attachment in the Exchange store. |
| contentLocation | String | Don't use this property as it isn't supported. |
| contentType | String | The content type of the attachment. |
| id | String | The attachment ID. |
| isInline | Boolean | Set to `true` if the attachment is an inline attachment. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the attachment was last modified. |
| name | String | The name representing the text that is displayed below the icon representing the embedded attachment and doesn't need to be the actual file name. |
| size | Int32 | The size in bytes of the attachment. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "contentBytes": "string (binary)",
  "contentId": "string",
  "contentLocation": "string",
  "contentType": "string",
  "id": "string (identifier)",
  "isInline": true,
  "lastModifiedDateTime": "String (timestamp)",
  "name": "string",
  "size": "Int32"
}
```
