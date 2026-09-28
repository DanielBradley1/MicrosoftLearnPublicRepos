<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printdocumentuploadproperties?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# printDocumentUploadProperties resource type

Namespace: microsoft.graph

Describes the document that is being uploaded

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentType | String | The document's content \(MIME\) type. |
| documentName | String | The document's name. |
| size | Int64 | The document's size in bytes. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printDocumentUploadProperties",
  "contentType": "String",
  "documentName": "String",
  "size": "Integer"
}
```
