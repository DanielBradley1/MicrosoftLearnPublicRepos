<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/restoreartifactdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-10 -->

# restoreArtifactDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents detailed count information about artifacts involved in a restore operation, including the total number of artifacts, the number successfully restored, and the number that failed.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| failedCount | Int32 | The number of artifacts that failed to be restored during the restore operation. |
| restoredCount | Int32 | The number of artifacts that were successfully restored during the restore operation. |
| totalArtifactsCount | Int32 | The total number of artifacts included in the restore operation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.restoreArtifactDetails",
  "totalArtifactsCount": "Integer",
  "restoredCount": "Integer",
  "failedCount": "Integer"
}
```
