<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/limitedcostmanagementquantity -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# limitedCostManagementQuantity resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A quantity limited to a specific value. A value of zero permits no consumption and is distinct from unlimited. Derived from [costManagementQuantity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `unit` | [costManagementUnit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity#costmanagementunit-enumeration) | Inherited from [costManagementQuantity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity). The unit for the value. |
| `value` | Double | The numeric value, expressed in the stated unit. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.limitedCostManagementQuantity",
  "unit": "String",
  "value": "Double"
}
```
