<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# costManagementQuantity resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

A unit-bearing quantity that is either limited to a value or unlimited. This is an abstract type. Every quantity is one of its derived types, identified by the `@odata.type` property on write:

- [limitedCostManagementQuantity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/limitedcostmanagementquantity)
- [unlimitedCostManagementQuantity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/unlimitedcostmanagementquantity)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `unit` | [costManagementUnit](#costmanagementunit-enumeration) | The unit for the quantity. |

### costManagementUnit enumeration

An [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) with the following possible values.

| Value | Description |
| :--- | :--- |
| `copilotCredit` | The current Copilot Credits consumption unit. |
| `unknownFutureValue` | Evolvable enumeration sentinel value. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementQuantity",
  "unit": "String"
}
```
