<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulksetdevicename?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# cloudPcBulkSetDeviceName resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a [bulk action](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta) that sets the operating system device names of Cloud PCs by using a naming template. The service generates a name for each Cloud PC in the batch. This action doesn't change the Cloud PC **displayName** property.

To submit the action, [create a cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/virtualendpoint-post-bulkactions?view=graph-rest-beta) with **@odata.type** set to `#microsoft.graph.cloudPcBulkSetDeviceName`. The operation runs asynchronously. Use [Get cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/cloudpcbulkaction-get?view=graph-rest-beta) to check its **status** and **actionSummary**.

Inherits from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta).

## Methods

For the list of supported methods, see [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionSummary | [cloudPcBulkActionSummary](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkactionsummary?view=graph-rest-beta) | The execution summary of the bulk action. Read-only. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| cloudPcIds | String collection | The IDs of the Cloud PCs that the action applies to. Individual Cloud PC IDs are GUID-formatted strings. Required when you create the action. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the bulk action was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. Read-only. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| deviceNamingTemplate | String | The template used to generate a unique device name for each Cloud PC. Required when creating the action. Use an optional prefix followed by one `%RAND:x%` macro, where `x` is the number of random alphanumeric characters and is at least 5. The generated name must be 5–15 characters long. The prefix can contain ASCII letters, digits, and hyphens, and must not start with a hyphen. The prefix length plus `x` must not exceed 15. For example, `ACRA-%RAND:5%` generates a ten-character name such as `ACRA-A1B2C`. |
| displayName | String | The name of the bulk action, not the device names of the targeted Cloud PCs. Required when you create the action. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| id | String | The unique identifier of the bulk action. Read-only. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| initiatedByUserPrincipalName | String | The user principal name \(UPN\) of the user who initiated the action. Read-only. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| scheduledDuringMaintenanceWindow | Boolean | Indicates whether the action is scheduled according to the maintenance window. The default value is `false`. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |
| status | [cloudPcBulkActionStatus](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta#cloudpcbulkactionstatus-values) | The status of the bulk action. The default value is `pending`. Read-only. Inherited from [cloudPcBulkAction](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcbulkaction?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcBulkSetDeviceName",
  "displayName": "String",
  "id": "String (identifier)",
  "cloudPcIds": [
    "String"
  ],
  "actionSummary": {
    "@odata.type": "microsoft.graph.cloudPcBulkActionSummary"
  },
  "createdDateTime": "String (timestamp)",
  "scheduledDuringMaintenanceWindow": "Boolean",
  "status": "String",
  "initiatedByUserPrincipalName": "String",
  "deviceNamingTemplate": "String"
}
```
