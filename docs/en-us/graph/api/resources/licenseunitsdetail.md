<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/licenseunitsdetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# licenseUnitsDetail resource type

Namespace: microsoft.graph

The **prepaidUnits** property of the [subscribedSku](https://learn.microsoft.com/en-us/graph/api/resources/subscribedsku?view=graph-rest-1.0) entity is of type **licenseUnitsDetail**. For more information on the progression states of a subscription, see [What if my subscription expires?](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires?view=o365-worldwide&preserve-view=true)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| enabled | Int32 | The number of units that are enabled for the active subscription of the service SKU. |
| lockedOut | Int32 | The number of units that are locked out because the customer canceled their subscription of the service SKU. |
| suspended | Int32 | The number of units that are suspended because the subscription of the service SKU has been canceled. The units can't be assigned but can still be reactivated before they're deleted. |
| warning | Int32 | The number of units that are in warning status. When the subscription of the service SKU has expired, the customer has a grace period to renew their subscription before it's canceled \(moved to a `suspended` state\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "enabled": "Int32",
  "lockedOut": "Int32",
  "suspended": "Int32",
  "warning": "Int32"
}
```
