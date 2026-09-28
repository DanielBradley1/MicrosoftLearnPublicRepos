<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-billing?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-15 -->

# billing resource type

Namespace: microsoft.graph.partners.billing

Note

This API is available for Cloud Solution Provider \(CSP\) partners only to access their billed and unbilled reconciliation data for a tenant. To learn more about the CSP program, see [Microsoft Cloud Solution Provider](https://learn.microsoft.com/en-us/partner-center/csp-overview).

Represents billing details for billed and unbilled data.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| manifests | [microsoft.graph.partners.billing.manifest](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-manifest?view=graph-rest-1.0) collection | Represents metadata for the exported data. |
| operations | [microsoft.graph.partners.billing.operation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-operation?view=graph-rest-1.0) collection | Represents an operation to export the billing data of a partner. |
| reconciliation | [microsoft.graph.partners.billing.billedReconciliation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-billingreconciliation?view=graph-rest-1.0) | Represents details for billed and unbilled invoice reconciliation data. |
| usage | [microsoft.graph.partners.billing.azureUsage](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-azureusage?view=graph-rest-1.0) | Represents details for billed and unbilled Azure usage data. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partners.billing.billing"
}
```
