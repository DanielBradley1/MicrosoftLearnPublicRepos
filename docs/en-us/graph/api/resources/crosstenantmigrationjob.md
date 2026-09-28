<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# crossTenantMigrationJob resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a [cross-tenant migration](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigration?view=graph-rest-beta) batch job that migrates user data from a source tenant to a target tenant. After you [create](https://learn.microsoft.com/en-us/graph/api/migrationsroot-post-crosstenantmigrationjobs?view=graph-rest-beta) a job, call [validate](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-validate?view=graph-rest-beta) to verify tenant and resource configuration, then call [migrate](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-migrate?view=graph-rest-beta) to begin the actual migration.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/migrationsroot-list-crosstenantmigrationjobs?view=graph-rest-beta) | [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) collection | Get a list of the crossTenantMigrationJob objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/migrationsroot-post-crosstenantmigrationjobs?view=graph-rest-beta) | [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) | Create a new [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-get?view=graph-rest-beta) | [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) | Read the properties and relationships of a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-update?view=graph-rest-beta) | [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) | Update the properties of a [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/migrationsroot-delete-crosstenantmigrationjobs?view=graph-rest-beta) | None | Delete a crossTenantMigrationJob object. |
| [cancel](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-cancel?view=graph-rest-beta) | [crossTenantMigrationCancelResponse](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationcancelresponse?view=graph-rest-beta) | Cancel a [cross-tenant migration job](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta). |
| [migrate](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-migrate?view=graph-rest-beta) | [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) | Migrate a [cross-tenant migration job](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) asynchronously. |
| [validate](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-validate?view=graph-rest-beta) | [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) | Validate a [cross-tenant migration job](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) asynchronously. |
| [List users](https://learn.microsoft.com/en-us/graph/api/crosstenantmigrationjob-list-users?view=graph-rest-beta) | [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-beta) collection | List the users in the migration and the status of their migration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completeAfterDateTime | DateTimeOffset | Date and time after which the migration should be performed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. |
| createdBy | String | User principal name \(UPN\) of the user who created the job. Read-only. |
| createdDateTime | DateTimeOffset | When the job was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. Read-only. |
| displayName | String | Display name of the job. Must be unique per tenant. |
| exchangeSettings | [exchangeOnlineCrossTenantMigrationSettings](https://learn.microsoft.com/en-us/graph/api/resources/exchangeonlinecrosstenantmigrationsettings?view=graph-rest-beta) | Settings to use for migration of Exchange workload. Nullable. |
| id | String | Unique identifier for the migration job. Read-only. |
| jobType | crossTenantMigrationJobType | Type of the migration job. The possible values are: `validate` \(only validation is performed, no migration\), `migrate` \(content is migrated\). |
| lastUpdatedDateTime | DateTimeOffset | When this migration job was last updated. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. Read-only. |
| message | String | Status message of the migration job. Nullable. Read-only. |
| resources | String collection | IDs \(GUID\) of the resources that are migrated with the migration job. |
| resourceType | String | Type of resource being migrated. Only `Users` is currently supported. |
| sourceTenantId | String | ID \(GUID\) of the tenant that content is migrated from. |
| status | crossTenantMigrationJobStatus | Most recent status of the migration job. Read-only. The possible values are: `submitted`, `approved`, `processing`, `cuttingOver`, `inProgress`, `completed`, `completedWithErrors`, `failed`, `cancelled`, `pendingCancel`, `adminActionRequired`, `validateSubmitted`, `validateProcessing`, `validateInProgress`, `validatePassed`, `validateFailed`, `pendingDelete`, and `deleted`. |
| targetTenantId | String | ID of the tenant that content is migrated to. Read-only. |
| workloads | String collection | Workloads to migrate. Supported workloads are `Teams`, `Exchange`, and `ODSP` \(OneDrive/SharePoint\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| users | [crossTenantMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationtask?view=graph-rest-beta) collection | Details and status of the users migrated in this migration job. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.crossTenantMigrationJob",
  "id": "String (identifier)",
  "displayName": "String",
  "jobType": "String",
  "sourceTenantId": "String",
  "targetTenantId": "String",
  "completeAfterDateTime": "String (timestamp)",
  "status": "String",
  "message": "String",
  "createdDateTime": "String (timestamp)",
  "createdBy": "String",
  "lastUpdatedDateTime": "String (timestamp)",
  "exchangeSettings": {
    "@odata.type": "microsoft.graph.exchangeOnlineCrossTenantMigrationSettings"
  },
  "workloads": [
    "String"
  ],
  "resourceType": "String",
  "resources": [
    "String"
  ]
}
```
