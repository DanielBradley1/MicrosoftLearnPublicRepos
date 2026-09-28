<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjobqueuedevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-25 -->

# sharePointMigrationJobQueuedEvent resource type

Namespace: microsoft.graph

Represents the queued status of a migration job.

Inherits from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0).

## Methods

For the list of supported methods, see [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| correlationId | String | The correlation ID of a migration job. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| eventDateTime | DateTimeOffset | The date and time when the job status changes to *Queued*. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| id | String | The unique identifier of this event. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| jobId | String | The unique identifier of a migration job. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointMigrationJobQueuedEvent",
  "correlationId": "String",
  "eventDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "jobId": "String"
}
```
