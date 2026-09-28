<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-25 -->

# sharePointMigrationEvent resource type

Namespace: microsoft.graph

Represents the common information of a SharePoint migration event.

Base event of the following progress events:

- [sharePointMigrationFinishManifestFileUploadEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationfinishmanifestfileuploadevent?view=graph-rest-1.0)
- [sharePointMigrationJobCancelledEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjobcancelledevent?view=graph-rest-1.0)
- [sharePointMigrationJobDeletedEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjobdeletedevent?view=graph-rest-1.0)
- [sharePointMigrationJobErrorEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjoberrorevent?view=graph-rest-1.0)
- [sharePointMigrationJobPostponedEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjobpostponedevent?view=graph-rest-1.0)
- [sharePointMigrationJobProgressEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjobprogressevent?view=graph-rest-1.0)
- [sharePointMigrationJobQueuedEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjobqueuedevent?view=graph-rest-1.0)
- [sharePointMigrationJobStartEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjobstartevent?view=graph-rest-1.0)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List progress events](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationjob-list-progressevents?view=graph-rest-1.0) | [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0) collection | Get a list of [migration events](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0) for a particular job in a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| correlationId | String | The correlation ID of a migration job. Read-only. |
| eventDateTime | DateTimeOffset | The date and time when the job status changes. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| id | String | The unique identifier of a migration progress event. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| jobId | String | The unique identifier of a migration job. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointMigrationEvent",
  "correlationId": "String",
  "eventDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "jobId": "String"
}
```
