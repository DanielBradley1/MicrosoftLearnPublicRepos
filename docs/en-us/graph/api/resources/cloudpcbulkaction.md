<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# cloudPcBulkAction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents the bulk action applied to Cloud PCs specified in a parameter.

Base type of [cloudPcBulkModifyDiskEncryptionType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkmodifydiskencryptiontype?view=graph-rest-beta), [cloudPcBulkDisasterRecovery](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkdisasterrecovery?view=graph-rest-beta), [cloudPcBulkDisasterRecoveryFailback](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkdisasterrecoveryfailback?view=graph-rest-beta), [cloudPcBulkDisasterRecoveryFailover](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkdisasterrecoveryfailover?view=graph-rest-beta), [cloudPcBulkPowerOff](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkpoweroff?view=graph-rest-beta), [cloudPcBulkPowerOn](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkpoweron?view=graph-rest-beta), [cloudPcBulkReinstallAgent](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkreinstallagent?view=graph-rest-beta), [cloudPcBulkReprovision](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkreprovision?view=graph-rest-beta), [cloudPcBulkResize](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkresize?view=graph-rest-beta), [cloudPcBulkRestart](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkrestart?view=graph-rest-beta), [cloudPcBulkRestore](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkrestore?view=graph-rest-beta), and [cloudPcBulkTroubleshoot](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulktroubleshoot?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-list-bulkactions?view=graph-rest-beta) | [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta) collection | Get a list of the [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-bulkactions?view=graph-rest-beta) | [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta) | Create a new [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/cloudpcbulkaction-get?view=graph-rest-beta) | [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta) | Read the properties and relationships of a [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta) object. |
| [Retry](https://learn.microsoft.com/en-us/graph/api/cloudpcbulkaction-retry?view=graph-rest-beta) | None | Retry a [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta) object with selected Cloud PCs. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionSummary | [cloudPcBulkActionSummary](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkactionsummary?view=graph-rest-beta) | Run summary of this bulk action. |
| cloudPcIDs | String collection | IDs of the Cloud PCs the bulk action applies to. |
| createdDateTime | DateTimeOffset | The date and time when the bulk action was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayName | String | Name of the bulk action. |
| id | String | ID of the bulk action. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| initiatedByUserPrincipalName | String | Indicates the user principal name \(UPN\) of the user who initiated this bulk action. Read-only. |
| scheduledDuringMaintenanceWindow | Boolean | Indicates whether the bulk action is scheduled according to the maintenance window. When `true`, the bulk action uses the maintenance window to schedule the action; `false` means that the bulk action doesn't use the maintenance window. The default value is `false`. |
| status | [cloudPcBulkActionStatus](#cloudpcbulkactionstatus-values) | Indicates the status of bulk actions. Possible values are `pending`, `succeeded`, `failed`, `unknownFutureValue`. The default value is `pending`. Read-only. |

### cloudPcBulkActionStatus values

| Member | Description |
| :--- | :--- |
| pending | Default. Indicates the status of the bulk action as `pending` because some of the bulk actions are still in progress and not yet completed. |
| succeeded | Indicates the status of the bulk action as `succeeded` for all associated actions. |
| failed | Indicates the status of the bulk action as `failed` for all associated actions. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcBulkAction",
  "actionSummary": {"@odata.type": "microsoft.graph.cloudPcBulkActionSummary"},
  "cloudPcIds": ["String"],
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "initiatedByUserPrincipalName": "String",
  "scheduledDuringMaintenanceWindow": "Boolean",
  "status": "String"
}
```
