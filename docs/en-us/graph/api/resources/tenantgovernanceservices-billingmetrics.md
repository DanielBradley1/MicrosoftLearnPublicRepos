<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetrics?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# billingMetrics resource type

Namespace: microsoft.graph

Represents billing metrics that show commerce and billing account connections between the calling tenant and a [related tenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0). Tracks associated billing relationships where one tenant manages billing or provisioning for another tenant's subscriptions. Includes both initial and recent snapshots with local \(calling tenant as primary billing tenant\) and foreign \(related tenant as primary billing tenant\) connection counts.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| initial | [microsoft.graph.billingMetricsInitial](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsinitial?view=graph-rest-1.0) | Billing metrics corresponding to initial snapshots where metrics were aggregated for the first time. |
| recent | [microsoft.graph.billingMetricsRecent](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-billingmetricsrecent?view=graph-rest-1.0) | Billing metrics corresponding to recent snapshots where metrics were found to have sufficiently changed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.billingMetrics"
}
```
