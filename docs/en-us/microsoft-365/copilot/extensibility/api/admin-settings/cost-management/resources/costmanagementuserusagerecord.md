<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagerecord -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# costManagementUserUsageRecord resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

One user's reported \(processed\) consumption of Copilot Credits for one completed UTC day. The row is keyed on `userId` and has no separate `id`. This processed, date-bounded report is distinct from the raw, timestamp-bounded detail returned by [costManagementUserUsageDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagedetail); the `sessionCount` values of the two resources aren't guaranteed to be equal.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagerecord-list) | [costManagementUserUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagerecord) collection | Get a list of costManagementUserUsageRecord objects. |
| [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusagerecord-get) | [costManagementUserUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagerecord) | Retrieve the properties and relationships of a costManagementUserUsageRecord object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `consumedQuantity` | Double | Billable consumption attributed to this user for the requested completed UTC day. Supports `$orderby`. Read-only. |
| `sessionCount` | Int64 | Count of distinct non-null session identifiers on billable activity for this user during the requested completed UTC day, subject to the source filters and plan processing watermarks. Excludes non-billable activity. Read-only. |
| `unit` | [costManagementUnit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity#costmanagementunit-enumeration) | Unit that applies to `consumedQuantity`. Read-only. |
| `userId` | String | The identifier of the user this row reports. Supports `$filter`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementUserUsageRecord",
  "consumedQuantity": "Double",
  "sessionCount": "Int64",
  "unit": "String",
  "userId": "String"
}
```
