<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-billingreconciliation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-15 -->

# billingReconciliation resource type

Namespace: microsoft.graph.partners.billing

Note

This API is available for Cloud Solution Provider \(CSP\) partners only to access their billed and unbilled reconciliation data for a tenant. To learn more about the CSP program, see [Microsoft Cloud Solution Provider](https://learn.microsoft.com/en-us/partner-center/csp-overview).

Represents details for billed invoice reconciliation and unbilled invoice reconciliation data.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| billed | [microsoft.graph.partners.billing.billedReconciliation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-billedreconciliation?view=graph-rest-1.0) | Represents details for billed invoice reconciliation data. |
| unbilled | [microsoft.graph.partners.billing.unbilledReconciliation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-unbilledreconciliation?view=graph-rest-1.0) | Represents details for unbilled invoice reconciliation data. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partners.billing.billingReconciliation"
}
```
