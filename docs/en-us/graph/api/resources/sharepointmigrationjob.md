<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjob?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-25 -->

# sharePointMigrationJob resource type

Namespace: microsoft.graph

Represents a SharePoint migration timer job that's queued for later processing. A migration import job moves content to SharePoint. An asynchronous metadata read \(AMR\) job, on the contrary, exports content from SharePoint.

The job might take anywhere from a few minutes to several hours to complete and is automatically removed from the queue upon completion; however, progress events remain accessible for up to four days.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-post-migrationjobs?view=graph-rest-1.0) | [sharePointMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjob?view=graph-rest-1.0) | Create a new [sharePointMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjob?view=graph-rest-1.0) object that is scheduled to run at a later time to migrate content from an intermediary storage to the target [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationjob-delete?view=graph-rest-1.0) | None | Delete a [sharePointMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjob?view=graph-rest-1.0) object from a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). |
| [List progress events](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationjob-list-progressevents?view=graph-rest-1.0) | [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0) collection | Get a list of [migration events](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0) for a particular job in a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0). |
| [Provision migration containers](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-provisionmigrationcontainers?view=graph-rest-1.0) | [sharePointMigrationContainerInfo](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationcontainerinfo?view=graph-rest-1.0) | Provision SharePoint-managed Azure blob containers as temporary storage for migration content and metadata. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| containerInfo | [sharePointMigrationContainerInfo](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationcontainerinfo?view=graph-rest-1.0) | The Azure blob containers associated with the migration job. It contains two container URLs and the key for content encryption. Read-only. |
| id | String | The unique identifier of the migration job. Read-only. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| progressEvents | [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0) collection | A collection of migration events that reflects the job status changes. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointMigrationJob",
  "id": "String (identifier)",
  "containerInfo": {
    "@odata.type": "microsoft.graph.sharePointMigrationContainerInfo"
  }
}
```

## Related content

For information about the status or progress of a SharePoint migration job, see [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0).
