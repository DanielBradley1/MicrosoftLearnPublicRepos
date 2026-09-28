<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjoberrorevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-25 -->

# sharePointMigrationJobErrorEvent resource type

Namespace: microsoft.graph

Represents the error status of a SharePoint migration job.

Inherits from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0).

## Methods

For the list of supported methods, see [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| correlationId | String | The correlation ID of a migration job. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | The error code and message. Read-only. |
| errorLevel | sharePointMigrationJobErrorLevel | The error level. Read-only. The possible values are: `important`, `warning`, `error`, `fatalError`, `unknownFutureValue`. |
| eventDateTime | DateTimeOffset | The date and time when the job status changes to a specific type of *JobError*. Read-only. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| id | String | The unique identifier of this event. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| jobId | String | The unique identifier of a migration job. Read-only. Inherited from [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0). |
| objectId | String | The object ID. Read-only. |
| objectType | sharePointMigrationObjectType | The object type. Read-only. The possible values are: `site`, `web`, `folder`, `list`, `listItem`, `file`, `alert`, `sharedWithObject`, `invalid`, `unknownFutureValue`. |
| objectUrl | String | The object URL. Read-only. |
| totalRetryCount | Int32 | The current retry count of the job. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointMigrationJobErrorEvent",
  "correlationId": "String",
  "error": {"@odata.type": "microsoft.graph.publicError"},
  "errorLevel": "String",
  "eventDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "jobId": "String",
  "objectId": "String",
  "objectType": "String",
  "objectUrl": "String",
  "totalRetryCount": "Int32"
}
```
