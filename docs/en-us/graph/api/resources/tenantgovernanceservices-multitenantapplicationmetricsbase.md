<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# multiTenantApplicationMetricsBase resource type

Namespace: microsoft.graph

This resource is an abstract base type and does not appear directly in API responses. Use the concrete types [multiTenantApplicationMetricsInitial](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsinitial?view=graph-rest-1.0) or [multiTenantApplicationMetricsRecent](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsrecent?view=graph-rest-1.0).

Abstract base type that defines common properties for multi-tenant application metrics.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inboundMonthlyTotalApplications | String | The total number of inbound multi-tenant applications in the last month. |
| outboundMonthlyTotalApplications | String | The total number of outbound multi-tenant applications in the last month. |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

Note

This abstract type is not returned in API responses. See concrete implementations.

```json
{
  "@odata.type": "#microsoft.graph.multiTenantApplicationMetricsBase",
  "watermarkDateTime": "String (timestamp)",
  "inboundMonthlyTotalApplications": "String",
  "outboundMonthlyTotalApplications": "String"
}
```
