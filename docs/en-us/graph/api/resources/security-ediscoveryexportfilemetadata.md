<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryexportfilemetadata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# ediscoveryExportFileMetadata resource type

Namespace: microsoft.graph.security

Represents the file metadata for an export in Microsoft Purview eDiscovery.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| downloadUrl | String | The URL to download the export. |
| fileName | String | The name of the file. |
| size | Int64 | The size of the file. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ediscoveryExportFileMetadata",
  "downloadUrl": "String",
  "fileName": "String",
  "size": "Int64"
}
```
