<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementtenantcreditbalance -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# costManagementTenantCreditBalance resource type

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

The tenant's Copilot credit balance snapshot, returned by the [getTenantCreditBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/costmanagementroot-gettenantcreditbalance) function.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| `billingMethodBalances` | [costManagementBillingMethodBalance](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/cost-management/resources/costmanagementbillingmethodbalance) collection | Credit balances, one per billing method. Each entry carries its own data status. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.costManagementTenantCreditBalance",
  "billingMethodBalances": [
    {
      "@odata.type": "microsoft.graph.costManagementBillingMethodBalance"
    }
  ]
}
```
