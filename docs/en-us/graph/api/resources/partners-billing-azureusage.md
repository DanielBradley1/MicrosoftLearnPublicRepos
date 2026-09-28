<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-azureusage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# azureUsage resource type

Namespace: microsoft.graph.partners.billing

Note

This API is available for Cloud Solution Provider \(CSP\) partners only to access their billed and unbilled reconciliation data for a tenant. To learn more about the CSP program, see [Microsoft Cloud Solution Provider](https://learn.microsoft.com/en-us/partner-center/csp-overview).

Represents details for billed and unbilled Azure usage data.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| billed | [microsoft.graph.partners.billing.billedUsage](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-billedusage?view=graph-rest-1.0) | Represents details for billed Azure usage data. |
| unbilled | [microsoft.graph.partners.billing.unbilledUsage](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-unbilledusage?view=graph-rest-1.0) | Represents details for unbilled Azure usage data. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partners.billing.azureUsage"
}
```
