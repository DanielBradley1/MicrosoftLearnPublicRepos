<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/documentsetcontent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# documentSetContent resource type

Namespace: microsoft.graph

Represents the default content of document set in SharePoint.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentType | microsoft.graph.contentTypeInfo | Content type information of the file. |
| fileName | string | Name of the file in resource folder that should be added as a default content or a template in the document set. |
| folderName | string | Folder name in which the file will be placed when a new document set is created in the library. |

## JSON representation

Here is a JSON representation of a **documentSetContent** resource.

```json
{
  "contentType": { "@type": "microsoft.graph.contentTypeInfo" },
  "fileName": "string",
  "folderName": "string"
}
```
