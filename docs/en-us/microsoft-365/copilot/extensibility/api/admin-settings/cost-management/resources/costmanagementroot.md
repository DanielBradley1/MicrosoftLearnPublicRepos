<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementroot -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# costManagementRoot resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

The Copilot Cost Management administration root, contained by the `copilot` singleton at `/copilot/costManagement`. Reading the root itself isn't supported in this version; use the contained collections and the bound [getTenantCreditBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementroot-gettenantcreditbalance) function.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [getTenantCreditBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementroot-gettenantcreditbalance) | [costManagementTenantCreditBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementtenantcreditbalance) | Get the tenant-wide credit balance snapshot. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `id` | String | Inherited entity key. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `spendingPolicies` | [spendingPolicy](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/spendingpolicy) collection | The spending policies that govern Copilot Credits consumption. |
| `userBalances` | [costManagementUserBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementuserbalance) collection | Per-user consumption balances, addressed by the user's identifier. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementRoot",
  "id": "String"
}
```
