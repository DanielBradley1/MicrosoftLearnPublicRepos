<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# sharePointMigrationTask resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the migration task for migrating a specific source resource to a target organization and indicates the status of that migration operation. This entity captures a specific intent to perform a **sharePointMigrationTask** operation, has a unique ID, can exist independently, has a defined lifetime, and can be retrieved using the ID.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationtask-get?view=graph-rest-beta) | [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) | Get a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) that was previously created, using the task ID. |
| [Create or update](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationtask-update?view=graph-rest-beta) | [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) | Create or update a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) to migrate a resource from the source organization to the target organization, using the **sharePointMigrationTaskParameters**. |
| [Get by source user principal name](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationtask-getbysourceuserprincipalname?view=graph-rest-beta) | [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) | Get a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) that was previously created for a user, using the source **userPrincipalName**. |
| [Get by source site URL](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationtask-getbysourcesiteurl?view=graph-rest-beta) | [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) | Get a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) that was previously created for a regular site, using the source site URL. |
| [Get by source group mail nickname](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationtask-getbysourcegroupmailnickname?view=graph-rest-beta) | [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) | Get a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) that was previously created for a group, using the source group mail nickname. |
| [Cancel](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationtask-cancel?view=graph-rest-beta) | None | Cancel a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) that moves a specific object from a source organization to a target organization. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-beta) | The error information to provide context for failures. Optional. Read-only. Only on OneDrive and SharePoint. |
| finishedDateTime | DateTimeOffset | Date and time when the **sharePointMigrationTask** ended, if available. The task might complete successfully or fail, but it ends at that time. Read-only. Only on OneDrive and SharePoint. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The unique ID of the **sharePointMigrationTask** operation for the source organization and resource defined in the parameters. Omit this property during creation. The service returns it automatically. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastUpdatedDateTime | DateTimeOffset | Date and time when the **sharePointMigrationTask** was last updated or processed, if available. Use this property to find tasks that stopped processing for a long time. Read-only. Optional. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| parameters | [sharePointMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtaskparameters?view=graph-rest-beta) | Identifies the source resource and organization, defines the target organization, and includes settings that control the migration process. These settings must be specified during task creation and are also returned in every query about this task for tracking and identification. |
| startedDateTime | DateTimeOffset | Date and time when the **sharePointMigrationTask** started, if available. Read-only. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| status | sharePointMigrationTaskStatus | Indicates the status of the migration activity that this task represents. Omit this property during creation. The service returns it automatically. The possible values are: `notStarted`, `inProgress`, `completed`, `cancelled`, `failed`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointMigrationTask",
  "error": {"@odata.type": "microsoft.graph.publicError"},
  "finishedDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastUpdatedDateTime": "String (timestamp)",
  "parameters": {"@odata.type": "microsoft.graph.sharePointMigrationTaskParameters"},
  "startedDateTime": "String (timestamp)",
  "status": "String"
}
```
