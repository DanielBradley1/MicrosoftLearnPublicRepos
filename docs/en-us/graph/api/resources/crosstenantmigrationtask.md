<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-20 -->

# crossTenantMigrationTask resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-beta), which is a component of a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta). A [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-beta) is scoped to a particular unit to be migrated, such as a User.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-list-users?view=graph-rest-beta) | [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-beta) collection | Get a list of the crossTenantMigrationTask objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationtask-get?view=graph-rest-beta) | [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-beta) | Read the properties and relationships of [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-beta) object. |
| [cancel](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationtask-cancel?view=graph-rest-beta) | [crossTenantMigrationCancelResponse](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationcancelresponse?view=graph-rest-beta) | Cancel the migration task for this resource |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| currentStatus | [crossTenantMigrationServiceStatusDetails](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationservicestatusdetails?view=graph-rest-beta) collection | Most recent status of this migration task |
| ID | String | ID \(GUID\) of the resource being migrated with this task |
| lastUpdatedDateTime | DateTimeOffset | Time the task was last updated |
| taskType | String | Type of migration task. Only Users are supported at this time. |

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
