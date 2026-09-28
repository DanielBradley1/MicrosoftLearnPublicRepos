<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkrestore?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-06-10 -->

# cloudPcBulkRestore resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the entity that performs a bulk restore action. Perform a bulk restore for a set of Cloud PCs with associated Cloud PC ID and restore point. If some of the devices don't have any snapshots to restore, they're set as restore failed, while the others with snapshots still be triggered successfully.

Inherits from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionSummary | [cloudPcBulkActionSummary](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkactionsummary?view=graph-rest-beta) | Run summary of this bulk action. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| cloudPcIds | String collection | IDs of the Cloud PCs the bulk action applies to. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the bulk action was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| displayName | String | Name of the bulk action. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| id | String | ID of the bulk action. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| ignoreUnhealthySnapshots | Boolean | `True` indicates that snapshots of unhealthy Cloud PCs are ignored. If no healthy snapshot exists within the selected **timeRange**, the healthy snapshot closest to the **restorePointDateTime** is used. `False` indicates that the snapshot within the selected **timeRange** and closest to the **restorePointDateTime** is used. The default value is `false`. |
| initiatedByUserPrincipalName | String | Indicates the user principal name \(UPN\) of the user who initiated this bulk action. Read-only. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| restorePointDateTime | DateTimeOffset | The date and time point for the selected Cloud PCs to restore. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| scheduledDuringMaintenanceWindow | Boolean | Indicates whether the bulk action is scheduled according to the maintenance window. When `true`, the bulk action uses the maintenance window to schedule the action; `false` means that the bulk action doesn't use the maintenance window. The default value is `false`. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| status | [cloudPcBulkActionStatus](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta#cloudpcbulkactionstatus-values) | Indicates the status of bulk actions. Possible values are `pending`, `succeeded`, `failed`, `unknownFutureValue`. The default value is `pending`. Read-only. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| timeRange | [restoreTimeRange](#restoretimerange-values) | Indicates the time range of the restore point. The possible values are: `before`, `after`, `beforeOrAfter`, `unknownFutureValue`. The default value is `before`. |

### restoreTimeRange values

| Member | Description |
| :--- | :--- |
| before | Choose the closest snapshot before the selected time point. Default. |
| after | Choose the closest snapshot after the selected time point. |
| beforeOrAfter | Choose the closest snapshot around the selected time point. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcBulkRestore",
  "actionSummary": {"@odata.type": "microsoft.graph.cloudPcBulkActionSummary"},
  "cloudPcIds": ["String"],
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "ignoreUnhealthySnapshots": "Boolean",
  "initiatedByUserPrincipalName": "String",
  "restorePointDateTime": "String (timestamp)",
  "scheduledDuringMaintenanceWindow": "Boolean",
  "status": "String",
  "timeRange": "String"
}
```
