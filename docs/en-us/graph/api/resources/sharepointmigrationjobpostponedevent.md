<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjobpostponedevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-25 -->

# sharePointMigrationJobPostponedEvent resource type

Namespace: microsoft.graph

Represents the postponed status of a SharePoint migration job.

Inherits from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0).

## Methods

For the list of supported methods, see [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| correlationId | String | The correlation ID of a migration job. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| eventDateTime | DateTimeOffset | The date and time when the job status changes to *Postponed*. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| id | String | The unique identifier of a **sharePointMigrationJobPostponedEvent**. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| jobId | String | The unique identifier of a migration job. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| jobsInQueue | Int64 | The number of migration jobs in the queue of the current database. Read-only. |
| nextPickupDateTime | DateTimeOffset | The date and time that indicate when this job is picked up next. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| reason | String | The reason for the postponement. Read-only. |
| totalRetryCount | Int32 | The current retry count of the job. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointMigrationJobPostponedEvent",
  "correlationId": "String",
  "eventDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "jobId": "String",
  "jobsInQueue": "Int64",
  "nextPickupDateTime": "String (timestamp)",
  "reason": "String",
  "totalRetryCount": "Int32"
}
```
