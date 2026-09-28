<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkcreatesnapshot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-13 -->

# cloudPcBulkCreateSnapshot resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the entity that performs a bulk create Cloud PC snapshot action.

Inherits from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionSummary | [cloudPcBulkActionSummary](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkactionsummary?view=graph-rest-beta) | The run summary of this bulk action. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| cloudPcIds | String collection | The IDs of the Cloud PCs the bulk action applies to. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the bulk action was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| displayName | String | Name of the bulk action. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| id | String | The ID of the bulk action. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| initiatedByUserPrincipalName | String | The user principal name \(UPN\) of the user who initiated this bulk action. Read-only. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| scheduledDuringMaintenanceWindow | Boolean | Indicates whether the bulk action is scheduled according to the maintenance window. When `true`, the bulk action uses the maintenance window to schedule the action; `false` means that the bulk action doesn't use the maintenance window. The default value is `false`. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| status | [cloudPcBulkActionStatus](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta#cloudpcbulkactionstatus-values) | The status of the bulk actions. Possible values are `pending`, `succeeded`, `failed`, `unknownFutureValue`. The default value is `pending`. Read-only. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| storageAccountId | String | Indicates the unique identifier for Secure Azure Storage Account, which receives the restore points \(snapshots\). The value can't be modified after it's created. For example, '/subscriptions/06199b73-30a1-4922-8734-93feca64cdf6/resourceGroups/res2627/providers/Microsoft.Storage/storageAccounts/sto1125'. Read-Only. |
| accessTier | [cloudPcBlobAccessTier](#cloudpcblobaccesstier-values) | Indicates the access tier of the blob file that the snapshot is copied to. Possible values are `hot`, `cool`, `cold`, `archive`, and `unknownFutureValue`. The default value is `hot`. Read-Only. |

### cloudPcBlobAccessTier values

| Member | Description |
| :--- | :--- |
| hot | Indicates an online tier optimized for storing data that is accessed or modified frequently. |
| cool | Indicates an online tier optimized for storing data that is infrequently accessed or modified. |
| cold | Indicates an online tier optimized for storing data that is rarely accessed or modified, but still requires fast retrieval. |
| archive | Indicates an offline access tier optimized for storing data that is rarely accessed, and that has flexible latency requirements that can be up to a few hours. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcBulkCreateSnapshot",
  "actionSummary": {"@odata.type": "microsoft.graph.cloudPcBulkActionSummary"},
  "cloudPcIds": ["String"],
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "initiatedByUserPrincipalName": "String",
  "scheduledDuringMaintenanceWindow": "Boolean",
  "status": "String",
  "storageAccountId": "String",
  "accessTier": "String"
}
```
