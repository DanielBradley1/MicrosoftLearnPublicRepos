<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementserviceusagerecord -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# costManagementServiceUsageRecord resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

One governed service's share of reported consumption of Copilot Credits for one completed UTC day, across the tenant. The row is keyed on `serviceId` and has no separate `id`. This tenant-wide record is distinct from [costManagementUserUsageServiceDetail](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserusageservicedetail), which splits one user's raw usage by service.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementserviceusagerecord-list) | [costManagementServiceUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementserviceusagerecord) collection | Get a list of costManagementServiceUsageRecord objects. |
| [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementserviceusagerecord-get) | [costManagementServiceUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementserviceusagerecord) | Retrieve the properties and relationships of a costManagementServiceUsageRecord object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `consumedQuantity` | Double | Consumption attributed to this service for the requested completed UTC day. Supports `$orderby`. Read-only. |
| `serviceId` | String | The governed service identifier, such as `cowork` or `workIQ`. Discover valid values from the service catalog by using a category identifier, not the catalog entry's own ID. Supports `$filter`. Read-only. |
| `unit` | [costManagementUnit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity#costmanagementunit-enumeration) | Unit that applies to `consumedQuantity`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementServiceUsageRecord",
  "consumedQuantity": "Double",
  "serviceId": "String",
  "unit": "String"
}
```
