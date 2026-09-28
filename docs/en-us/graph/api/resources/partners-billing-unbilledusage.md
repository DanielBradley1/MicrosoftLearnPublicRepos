<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-unbilledusage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# unbilledUsage resource type

Namespace: microsoft.graph.partners.billing

Note

This API is available for Cloud Solution Provider \(CSP\) partners only to access their billed and unbilled reconciliation data for a tenant. To learn more about the CSP program, see [Microsoft Cloud Solution Provider](https://learn.microsoft.com/en-us/partner-center/csp-overview).

Represents details for unbilled Azure usage data.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Export](https://learn.microsoft.com/en-us/graph/api/partners-billing-unbilledusage-export?view=graph-rest-1.0) | [microsoft.graph.partners.billing.operation](https://learn.microsoft.com/en-us/graph/api/resources/partners-billing-operation?view=graph-rest-1.0) | Export unbilled Azure usage data for a specific billing period and currency. |

## Properties

None.

### billingPeriod values

| Member | Description |
| :--- | :--- |
| current | The current month or billing period that is in progress. |
| last | The last month or billing period. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.partners.billing.unbilledUsage"
}
```
