<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# crossTenantMigrationTask resource type

Namespace: microsoft.graph

Represents a unit of user data to migrate as part of a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-list-users?view=graph-rest-1.0) | [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-1.0) collection | Get a list of the [crossTenantMigrationTasks](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-1.0) for users in a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationtask-get?view=graph-rest-1.0) | [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-1.0) | Read the properties and relationships of a [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-1.0) object that provides details about the migration task for a single user in a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0). |
| [Cancel](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationtask-cancel?view=graph-rest-1.0) | [crossTenantMigrationCancelResponse](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationcancelresponse?view=graph-rest-1.0) | Cancel a specific [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-1.0) for a user in a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| currentStatus | [crossTenantMigrationServiceStatusDetails](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationservicestatusdetails?view=graph-rest-1.0) collection | Most recent status of this migration task. |
| id | String | ID \(GUID\) of the resource that's migrated with this task. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastUpdatedDateTime | DateTimeOffset | Date and time when the task was last updated. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. |
| taskType | String | Type of migration task. Currently, only `Users` is supported. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantMigrationTask",
  "id": "String (identifier)",
  "taskType": "String",
  "lastUpdatedDateTime": "String (timestamp)",
  "currentStatus": [
    {
      "@odata.type": "microsoft.graph.crossTenantMigrationServiceStatusDetails"
    }
  ]
}
```
