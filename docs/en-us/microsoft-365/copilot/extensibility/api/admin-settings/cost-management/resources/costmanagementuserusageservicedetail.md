<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusageservicedetail -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# costManagementUserUsageServiceDetail resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

One governed service's share of a user's raw usage detail, contained by [costManagementUserUsageDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusagedetail). This per-user row is distinct from the tenant-wide [costManagementServiceUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementserviceusagerecord).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserusageservicedetail-list) | [costManagementUserUsageServiceDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusageservicedetail) collection | Get a list of costManagementUserUsageServiceDetail objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `consumedQuantity` | Double | Raw, billable-flagged consumption attributed to this service within the containing user's detail window. Independently rounded; child rows aren't guaranteed to sum exactly to the containing detail's `consumedQuantity`. Read-only. |
| `id` | String | The governed service identifier, such as `cowork` or `workIQ`. It's the same value as `serviceId` elsewhere in the API; it's named `id` here because it's this row's own key. Read-only. |
| `unit` | [costManagementUnit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity#costmanagementunit-enumeration) | Unit that applies to `consumedQuantity`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementUserUsageServiceDetail",
  "consumedQuantity": "Double",
  "id": "String",
  "unit": "String"
}
```
