<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementfundingusagerecord -->
<!-- Sitemap-Last-Modified: 2026-11-05 -->

# costManagementFundingUsageRecord resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

One funding class's share of reported consumption of Copilot Credits for a calendar month, including unbilled consumption. The row is keyed by the inherited `id`, whose value is the `fundingClass` member name. The quantities are consumption attributed to a funding class, not rated amounts. No currency, invoice, price, or settlement amounts are returned.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementfundingusagerecord-list) | [costManagementFundingUsageRecord](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementfundingusagerecord) collection | Get a list of costManagementFundingUsageRecord objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `consumedQuantity` | Double | Consumption attributed to this funding class during the requested month, including unbilled consumption where applicable. Supports `$orderby`. Read-only. |
| `dataStatus` | [costManagementUsageDataStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementusagedatastatus) | Freshness of the snapshot this row was computed from; `latestSourceDateTime` is the snapshot sync time. It doesn't indicate whether the covered month has closed, only how recently the underlying snapshot was synced. Read-only. |
| `fundingClass` | [costManagementFundingClass](#costmanagementfundingclass-enumeration) | The funding class this row covers. Read-only. |
| `id` | String | The row identifier. Equals the `fundingClass` member name, for example `prepaid`. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity). Read-only. |
| `unit` | [costManagementUnit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity#costmanagementunit-enumeration) | Unit that applies to `consumedQuantity`. Read-only. |

### costManagementFundingClass enumeration

The funding classification of reported consumption, including unbilled consumption. This enumeration is distinct from [costManagementBillingMethod](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementbillingmethodbalance#costmanagementbillingmethod-enumeration) and [costManagementBillingMethods](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy#costmanagementbillingmethods-enumeration): it classifies reported consumption rather than describing how a policy or balance is funded.

An [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) with the following possible values.

| Value | Description |
| :--- | :--- |
| `prepaid` | Drawn from a prepaid Copilot Credits pool. |
| `payAsYouGo` | Billed on demand, with no prepaid pool. |
| `overage` | Consumed above the purchased pool. Unbilled; it isn't an invoiced excess charge. |
| `nonBillable` | Consumed but not billed. |
| `unknownFutureValue` | Evolvable enumeration sentinel value. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementFundingUsageRecord",
  "consumedQuantity": "Double",
  "dataStatus": {
    "@odata.type": "microsoft.graph.costManagementUsageDataStatus"
  },
  "fundingClass": "String",
  "id": "String",
  "unit": "String"
}
```
