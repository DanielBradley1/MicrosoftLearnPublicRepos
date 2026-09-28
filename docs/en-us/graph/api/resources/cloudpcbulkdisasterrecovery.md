<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkdisasterrecovery?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-04-22 -->

# cloudPcBulkDisasterRecovery resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the entity that performs a bulk disaster recovery action. This action initiates the failover or failback process for a Cloud PC.

Inherits from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionSummary | [cloudPcBulkActionSummary](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkactionsummary?view=graph-rest-beta) | Run summary of this bulk action. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| capabilityType | [cloudPcDisasterRecoveryCapabilityType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdisasterrecoverycapability?view=graph-rest-beta#cloudpcdisasterrecoverycapabilitytype-values) | The disaster recovery action that can be performed for the Cloud PC. The possible values are: `none`, `failover`, `failback`, `unknownFutureValue`. |
| cloudPcIds | String collection | IDs of the Cloud PCs the bulk action applies to. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the bulk action was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| displayName | String | Name of the bulk action. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| id | String | ID of the bulk action. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| initiatedByUserPrincipalName | String | Indicates the user principal name \(UPN\) of the user who initiated this bulk action. Read-only. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| licenseType | [cloudPcDisasterRecoveryLicenseType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdisasterrecoverycapability?view=graph-rest-beta#cloudpcdisasterrecoverylicensetype-values) | The disaster recovery license type that provides the disaster recovery capability. The possible values are: `none`, `standard`, `unknownFutureValue`, `plus`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `plus`. |
| scheduledDuringMaintenanceWindow | Boolean | Indicates whether the bulk action is scheduled according to the maintenance window. When `true`, the bulk action uses the maintenance window to schedule the action; `false` means that the bulk action doesn't use the maintenance window. The default value is `false`. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| status | [cloudPcBulkActionStatus](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta#cloudpcbulkactionstatus-values) | Indicates the status of bulk actions. Possible values are `pending`, `succeeded`, `failed`, `unknownFutureValue`. The default value is `pending`. Read-only. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcBulkDisasterRecovery",
  "actionSummary": {"@odata.type": "microsoft.graph.cloudPcBulkActionSummary"},
  "capabilityType": "String",
  "cloudPcIds": ["String"],
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "initiatedByUserPrincipalName": "String",
  "licenseType": "String",
  "scheduledDuringMaintenanceWindow": "Boolean",
  "status": "String"
}
```
