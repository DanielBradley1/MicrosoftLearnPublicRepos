<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsinitial?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# multiTenantApplicationMetricsInitial resource type

Namespace: microsoft.graph

Represents the initial snapshot of multi-tenant application metrics captured when the [related tenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0) was first discovered, establishing a baseline for application usage across tenant boundaries.

Inherits from [microsoft.graph.multiTenantApplicationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Timestamp that represents when multitenant application metrics are initially aggregated for the related tenant. |
| inboundMonthlyTotalApplications | String | The total number of inbound multi-tenant applications in the last month. Inherited from [microsoft.graph.multiTenantApplicationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsbase?view=graph-rest-1.0). |
| outboundMonthlyTotalApplications | String | The total number of outbound multi-tenant applications in the last month. Inherited from [microsoft.graph.multiTenantApplicationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsbase?view=graph-rest-1.0). |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. Inherited from [microsoft.graph.multiTenantApplicationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsbase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.multiTenantApplicationMetricsInitial",
  "watermarkDateTime": "String (timestamp)",
  "inboundMonthlyTotalApplications": "String",
  "outboundMonthlyTotalApplications": "String",
  "createdDateTime": "String (timestamp)"
}
```
