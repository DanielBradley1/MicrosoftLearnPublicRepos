<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/unlimitedcostmanagementquantity -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# unlimitedCostManagementQuantity resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A quantity that is not limited. Carries no numeric value. Derived from [costManagementQuantity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `unit` | [costManagementUnit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity#costmanagementunit-enumeration) | Inherited from [costManagementQuantity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity). The unit. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unlimitedCostManagementQuantity",
  "unit": "String"
}
```
