<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjobcancelledevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-25 -->

# sharePointMigrationJobCancelledEvent resource type

Namespace: microsoft.graph

Represents the canceled status of a SharePoint migration job.

Inherits from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0).

## Methods

For the list of supported methods, see [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| correlationId | String | The correlation ID of a migration job. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| eventDateTime | DateTimeOffset | The date and time when the job status changes to *Canceled*. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| id | String | The unique identifier of this event. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| isCancelledByUser | Boolean | `True` when a user cancels the job; otherwise, `false`. Read-only. |
| jobId | String | The unique identifier of a migration job. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| totalRetryCount | Int32 | The current retry count of the job. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointMigrationJobCancelledEvent",
  "correlationId": "String",
  "eventDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "isCancelledByUser": "Boolean",
  "jobId": "String",
  "totalRetryCount": "Int32"
}
```
