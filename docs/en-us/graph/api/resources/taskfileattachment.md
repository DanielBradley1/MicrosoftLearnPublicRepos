<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/taskfileattachment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# taskFileAttachment resource type

Namespace: microsoft.graph

Represents a file, such as a text file or Word document, attached to a [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0). When you create a file attachment on a task, include `"@odata.type": "#microsoft.graph.taskFileAttachment"` and the properties **name** and **contentBytes**.

Inherits from [attachmentBase](https://learn.microsoft.com/en-us/graph/api/resources/attachmentbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/todotask-list-attachments?view=graph-rest-1.0) | [taskFileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/taskfileattachment?view=graph-rest-1.0) collection | Get a list of the [taskFileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/taskfileattachment?view=graph-rest-1.0) objects and their properties. |
| [Attach small file](https://learn.microsoft.com/en-us/graph/api/todotask-post-attachments?view=graph-rest-1.0) | [taskFileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/taskfileattachment?view=graph-rest-1.0) collection | Add a new [taskFileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/taskfileattachment?view=graph-rest-1.0) object to a [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0). |
| [Attach all file sizes](https://learn.microsoft.com/en-us/graph/api/taskfileattachment-createuploadsession?view=graph-rest-1.0) | [taskFileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/taskfileattachment?view=graph-rest-1.0) collection | Create an upload session to iteratively upload ranges of a file as an attachment to a [todoTask](https://learn.microsoft.com/en-us/graph/api/resources/todotask?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/taskfileattachment-get?view=graph-rest-1.0) | [taskFileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/taskfileattachment?view=graph-rest-1.0) | Read the properties and relationships of a [taskFileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/taskfileattachment?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/taskfileattachment-delete?view=graph-rest-1.0) | None | Delete a [taskFileAttachment](https://learn.microsoft.com/en-us/graph/api/resources/taskfileattachment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentBytes | Binary | The base64-encoded contents of the file. |
| contentType | String | The content type of the attachment. Inherited from [attachmentBase](https://learn.microsoft.com/en-us/graph/api/resources/attachmentbase?view=graph-rest-1.0). |
| id | String | The ID of the attachment. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the attachment was last modified. Inherited from [attachmentBase](https://learn.microsoft.com/en-us/graph/api/resources/attachmentbase?view=graph-rest-1.0). |
| name | String | The name of the text displayed under the icon that represents the embedded attachment. This does not need to be the actual file name. Inherited from [attachmentBase](https://learn.microsoft.com/en-us/graph/api/resources/attachmentbase?view=graph-rest-1.0). |
| size | Int32 | The size in bytes of the attachment. Inherited from [attachmentBase](https://learn.microsoft.com/en-us/graph/api/resources/attachmentbase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.taskFileAttachment",
  "contentBytes": "Binary",
  "contentType": "String",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "name": "String",
  "size": "Int32"
}
```
