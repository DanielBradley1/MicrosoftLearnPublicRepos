<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadstats?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-17 -->

# customDataProvidedResourceUploadStats resource type

Namespace: microsoft.graph

Metadata related to the files that were uploaded as part of a [customDataProvidedResourceUploadSession](https://learn.microsoft.com/en-us/graph/api/resources/customdataprovidedresourceuploadsession?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| filesUploaded | Int32 | Number of files uploaded in this session. |
| totalBytesUploaded | Int64 | Total bytes uploaded in this session. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customDataProvidedResourceUploadStats",
  "filesUploaded": "Int32",
  "totalBytesUploaded": "Int64"
}
```
