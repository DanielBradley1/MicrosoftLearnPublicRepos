<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetrics?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# b2BSignInActivityMetrics resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents B2B sign-in activity metrics that track monthly active guest users and applications accessed between the calling tenant and a [related tenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta). Includes both initial and recent snapshots with inbound and outbound activity counts.

Inherits from [b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the metrics snapshot. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| initial | [microsoft.graph.b2BSignInActivityMetricsInitial](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsinitial?view=graph-rest-beta) | B2B sign-in activity metrics corresponding to initial snapshots where metrics were aggregated for the first time. |
| investigationHints | [microsoft.graph.investigationActionStep](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-investigationactionstep?view=graph-rest-beta) collection | Ordered drill-in guidance for investigating sign-in user and application counts. This collection is returned only when explicitly requested by using a nested `$expand` query parameter, for example `$expand=b2BSignInActivityMetrics($expand=investigationHints)`. |
| recent | [microsoft.graph.b2BSignInActivityMetricsRecent](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsrecent?view=graph-rest-beta) | B2B sign-in activity metrics corresponding to recent snapshots where metrics were found to have sufficiently changed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.b2BSignInActivityMetrics",
  "id": "String (identifier)"
}
```
