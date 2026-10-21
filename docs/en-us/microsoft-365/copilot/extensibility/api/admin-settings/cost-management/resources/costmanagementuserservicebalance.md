<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserservicebalance -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# costManagementUserServiceBalance resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Per-service balance and enforcement-selection diagnosis for a user. Keyed by `serviceId`; a user holds at most one balance per service.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserservicebalance-list) | [costManagementUserServiceBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserservicebalance) collection | Get a list of costManagementUserServiceBalance objects. |
| [Get](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementuserservicebalance-get) | [costManagementUserServiceBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserservicebalance) | Retrieve the properties of a costManagementUserServiceBalance object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `accessDecisionReason` | [accessDecisionReason](#accessdecisionreason-enumeration) | The reason for the access decision. |
| `configuredPerUserLimit` | [costManagementQuantity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity) | The selected policy's per-user limit for the current UTC month; `unlimitedCostManagementQuantity` when no per-user cap. |
| `configuredPeriodLimit` | [costManagementQuantity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity) | The selected policy's consumption limit for the current UTC month. |
| `consumedQuantity` | Double | Measured consumption for the selected service context, month-to-date in UTC. |
| `dataStatus` | [costManagementDataStatus](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementdatastatus) | Freshness of the source data behind this row. |
| `effectiveCapacityQuantity` | [costManagementQuantity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity) | Capacity available from the selected policy; `unlimitedCostManagementQuantity` when no cap. |
| `isConsumptionAllowed` | Boolean | Whether the user can currently consume the service. A false value can mean missing entitlement or an exhausted limit; inspect `accessDecisionReason`. Supports `$filter` \(`eq`\). |
| `remainingQuantity` | [costManagementQuantity](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity) | Remaining quantity under the selected policy for the current period; `unlimitedCostManagementQuantity` when no cap. |
| `serviceId` | String | The service identifier. Key, read-only. Case-sensitive. Supports `$filter` \(`eq`, `in`\) and `$orderby` when listing one user's service balances. |
| `spendingPolicyId` | String | Identifier of the spending policy selected for this service. Always present for a balance row. Read-only. |
| `unit` | [costManagementUnit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementquantity#costmanagementunit-enumeration) | The unit for `consumedQuantity`. |

### accessDecisionReason enumeration

An [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations) with the following possible values.

| Value | Description |
| :--- | :--- |
| `allowed` | The user is allowed to consume. |
| `notEntitled` | The user isn't entitled to the service. |
| `limitExhausted` | The applicable limit is exhausted. |
| `unknownFutureValue` | Evolvable enumeration sentinel value. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementUserServiceBalance",
  "accessDecisionReason": "String",
  "configuredPerUserLimit": {
    "@odata.type": "microsoft.graph.costManagementQuantity"
  },
  "configuredPeriodLimit": {
    "@odata.type": "microsoft.graph.costManagementQuantity"
  },
  "consumedQuantity": "Double",
  "dataStatus": {
    "@odata.type": "microsoft.graph.costManagementDataStatus"
  },
  "effectiveCapacityQuantity": {
    "@odata.type": "microsoft.graph.costManagementQuantity"
  },
  "isConsumptionAllowed": "Boolean",
  "remainingQuantity": {
    "@odata.type": "microsoft.graph.costManagementQuantity"
  },
  "serviceId": "String",
  "spendingPolicyId": "String",
  "unit": "String"
}
```
