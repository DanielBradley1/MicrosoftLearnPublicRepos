<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printdocument?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-20 -->

# printDocument resource type

Namespace: microsoft.graph

Represents a document being printed.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create upload session](https://learn.microsoft.com/en-us/graph/api/printdocument-createuploadsession?view=graph-rest-1.0) | [uploadSession](https://learn.microsoft.com/en-us/graph/api/resources/uploadsession?view=graph-rest-1.0) | Create an upload session to iteratively upload ranges of binary file of the **printDocument**. |
| [Download binary file](https://learn.microsoft.com/en-us/graph/api/printdocument-get-file?view=graph-rest-1.0) | Download Url | Download the binary file associated with the **printDocument**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentType | String | The document's content \(MIME\) type. Read-only. |
| displayName | String | The document's name. Read-only. |
| id | String | The document's identifier. Read-only. |
| size | Int64 | The document's size in bytes. Read-only. |
| uploadedDateTime | DateTimeOffset | The time the document was uploaded. Read-only |
| downloadedDateTime | DateTimeOffset | The time the document was downloaded. Read-only |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printDocument",
  "id": "String (identifier)",
  "displayName": "String",
  "contentType": "String",
  "size": "Integer"
}
```
