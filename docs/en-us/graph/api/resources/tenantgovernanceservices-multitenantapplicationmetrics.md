<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetrics?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# multiTenantApplicationMetrics resource type

Namespace: microsoft.graph

Represents multi-tenant application usage metrics that track the number of applications used across tenant boundaries. Includes both initial and recent snapshots showing monthly counts of inbound and outbound multi-tenant application usage associated with [related tenants](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0).

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| initial | [microsoft.graph.multiTenantApplicationMetricsInitial](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsinitial?view=graph-rest-1.0) | Multitenant application metrics corresponding to initial snapshots where metrics were aggregated for the first time. |
| recent | [microsoft.graph.multiTenantApplicationMetricsRecent](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsrecent?view=graph-rest-1.0) | Multitenant application metrics corresponding to recent snapshots where metrics were found to have sufficiently changed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.multiTenantApplicationMetrics"
}
```
