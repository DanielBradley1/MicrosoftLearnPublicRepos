<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationfinishmanifestfileuploadevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-25 -->

# sharePointMigrationFinishManifestFileUploadEvent resource type

Namespace: microsoft.graph

Represents the manifest uploaded status of a SharePoint migration job.

Inherits from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0).

## Methods

For the list of supported methods, see [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| correlationId | String | The correlation ID of a migration job. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| eventDateTime | DateTimeOffset | The date and time when the job status changes to *ManifestFileUploadFinished*. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| id | String | The unique identifier of this event. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| jobId | String | The unique identifier of a migration job. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| manifestFileName | String | The exported manifest file name. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointMigrationFinishManifestFileUploadEvent",
  "correlationId": "String",
  "eventDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "jobId": "String",
  "manifestFileName": "String"
}
```
