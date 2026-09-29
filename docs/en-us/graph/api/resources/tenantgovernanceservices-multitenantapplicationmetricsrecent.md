<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsrecent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# multiTenantApplicationMetricsRecent resource type

Namespace: microsoft.graph

Represents the most recent snapshot of multi-tenant application metrics, showing current application usage across [related tenants](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0).

Inherits from [microsoft.graph.multiTenantApplicationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inboundMonthlyTotalApplications | String | The total number of inbound multi-tenant applications in the last month. Inherited from [microsoft.graph.multiTenantApplicationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsbase?view=graph-rest-1.0). |
| outboundMonthlyTotalApplications | String | The total number of outbound multi-tenant applications in the last month. Inherited from [microsoft.graph.multiTenantApplicationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsbase?view=graph-rest-1.0). |
| updateDateTime | DateTimeOffset | Timestamp that represents when multitenant application metrics are aggregated and have sufficiently changed for the related tenant. |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. Inherited from [microsoft.graph.multiTenantApplicationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsbase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.multiTenantApplicationMetricsRecent",
  "watermarkDateTime": "String (timestamp)",
  "inboundMonthlyTotalApplications": "String",
  "outboundMonthlyTotalApplications": "String",
  "updateDateTime": "String (timestamp)"
}
```
