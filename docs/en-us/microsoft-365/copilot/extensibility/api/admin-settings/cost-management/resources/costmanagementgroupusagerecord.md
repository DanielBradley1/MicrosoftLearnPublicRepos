<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementgroupusagerecord -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# costManagementGroupUsageRecord resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

One security group's reported \(processed\) consumption of Copilot Credits for one completed UTC day. The row is keyed on `groupId` and has no separate `id`. Consumption is attributed to the group based on the membership of the users who consumed it.

Note

A group usage record reports attributed consumption only. It isn't an allocation, a group balance, a cost-center hierarchy, or a chargeback position.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementgroupusagerecord-list) | [costManagementGroupUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementgroupusagerecord) collection | Get a list of costManagementGroupUsageRecord objects. |
| [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementgroupusagerecord-get) | [costManagementGroupUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementgroupusagerecord) | Retrieve the properties and relationships of a costManagementGroupUsageRecord object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `consumedQuantity` | Double | Billable consumption attributed to members of this group for the requested completed UTC day. Supports `$orderby`. Read-only. |
| `groupId` | String | The identifier of the security group this row reports. Supports `$filter`. Read-only. |
| `sessionCount` | Int64 | Count of distinct non-null session identifiers on billable activity attributed to this group during the requested completed UTC day, subject to the source filters and plan processing watermarks. Excludes non-billable activity. Read-only. |
| `unit` | [costManagementUnit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity#costmanagementunit-enumeration) | Unit that applies to `consumedQuantity`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementGroupUsageRecord",
  "consumedQuantity": "Double",
  "groupId": "String",
  "sessionCount": "Int64",
  "unit": "String"
}
```
