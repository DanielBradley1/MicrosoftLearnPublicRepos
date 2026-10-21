<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementbillingmethodbalance -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# costManagementBillingMethodBalance resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Credit balance for one billing method.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `billingMethod` | [costManagementBillingMethod](#costmanagementbillingmethod-enumeration) | The billing method this balance covers. |
| `consumedQuantity` | Double | Credits consumed. |
| `dataStatus` | [costManagementDataStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementdatastatus) | Last modification time for this row's source data. |
| `purchasedQuantity` | Double | Credits purchased. Omitted when there's no purchased pool, for example pay-as-you-go. |
| `remainingQuantity` | Double | Credits still available, as calculated by the service, not the difference between `purchasedQuantity` and `consumedQuantity`. Omitted when there's no finite pool. |
| `unit` | [costManagementUnit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity#costmanagementunit-enumeration) | Unit that applies to every quantity in this row. |

### costManagementBillingMethod enumeration

An [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) with the following possible values.

| Value | Description |
| :--- | :--- |
| `prepaidCredits` | Prepaid Copilot Credits, purchased through the pre-purchase plan. |
| `payAsYouGo` | Consumption billed on demand, with no prepaid pool. |
| `notSpecified` | The billing method isn't known or wasn't specified. |
| `unknownFutureValue` | Evolvable enumeration sentinel value. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementBillingMethodBalance",
  "billingMethod": "String",
  "consumedQuantity": "Double",
  "dataStatus": {
    "@odata.type": "microsoft.graph.costManagementDataStatus"
  },
  "purchasedQuantity": "Double",
  "remainingQuantity": "Double",
  "unit": "String"
}
```
