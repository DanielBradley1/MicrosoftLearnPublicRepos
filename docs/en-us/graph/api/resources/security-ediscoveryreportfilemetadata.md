<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryreportfilemetadata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-31 -->

# reportFileMetadata resource type

Namespace: microsoft.graph.security

Represents the file metadata of a job report in eDiscovery.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| downloadUrl | String | The URL to download the report. |
| fileName | String | The name of the file. |
| size | Int64 | The size of the file. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.reportFileMetadata",
  "downloadUrl": "String",
  "fileName": "String",
  "size": "Int64"
}
```
