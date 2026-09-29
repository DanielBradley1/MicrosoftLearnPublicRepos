<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetrics?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# b2BSignInActivityMetrics resource type

Namespace: microsoft.graph

Represents B2B sign-in activity metrics that track monthly active guest users and applications accessed between the calling tenant and a [related tenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0). Includes both initial and recent snapshots with inbound and outbound activity counts.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| initial | [microsoft.graph.b2BSignInActivityMetricsInitial](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsinitial?view=graph-rest-1.0) | B2B sign-in activity metrics corresponding to initial snapshots where metrics were aggregated for the first time. |
| recent | [microsoft.graph.b2BSignInActivityMetricsRecent](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsrecent?view=graph-rest-1.0) | B2B sign-in activity metrics corresponding to recent snapshots where metrics were found to have sufficiently changed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.b2BSignInActivityMetrics"
}
```
