<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjobstartevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-25 -->

# sharePointMigrationJobStartEvent resource type

Namespace: microsoft.graph

Represents the start status of a migration job, either *Started* or *Restarted*.

Inherits from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0).

## Methods

For the list of supported methods, see [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| correlationId | String | The correlation ID of a migration job. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| eventDateTime | DateTimeOffset | The date and time when the job status changes to *Started* or *Restarted*. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| id | String | The unique identifier of this event. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| isRestarted | Boolean | `True` if the job is restarted. `False` if it's the initial start. Read-only. |
| jobId | String | The unique identifier of a migration job. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| totalRetryCount | Int32 | The current retry count of the job. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointMigrationJobStartEvent",
  "correlationId": "String",
  "eventDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "isRestarted": "Boolean",
  "jobId": "String",
  "totalRetryCount": "Int32"
}
```
