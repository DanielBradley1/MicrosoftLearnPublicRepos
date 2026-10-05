<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetrics?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# multiTenantApplicationMetrics resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents multi-tenant application usage metrics that track the number of applications used across tenant boundaries. Includes both initial and recent snapshots showing monthly counts of inbound and outbound multi-tenant application usage associated with [related tenants](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta).

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the metrics snapshot. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| initial | [microsoft.graph.multiTenantApplicationMetricsInitial](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsinitial?view=graph-rest-beta) | Multitenant application metrics corresponding to initial snapshots where metrics were aggregated for the first time. |
| investigationHints | [microsoft.graph.investigationActionStep](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-investigationactionstep?view=graph-rest-beta) collection | Ordered drill-in guidance for investigating multitenant application counts. This collection is returned only when explicitly requested by using a nested `$expand` query parameter, for example `$expand=multiTenantApplicationMetrics($expand=investigationHints)`. |
| recent | [microsoft.graph.multiTenantApplicationMetricsRecent](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsrecent?view=graph-rest-beta) | Multitenant application metrics corresponding to recent snapshots where metrics were found to have sufficiently changed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.multiTenantApplicationMetrics",
  "id": "String (identifier)"
}
```
