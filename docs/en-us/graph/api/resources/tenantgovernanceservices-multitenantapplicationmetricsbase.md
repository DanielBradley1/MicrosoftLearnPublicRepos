<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsbase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# multiTenantApplicationMetricsBase resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

This resource is an abstract base type and does not appear directly in API responses. Use the concrete types [multiTenantApplicationMetricsInitial](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsinitial?view=graph-rest-beta) or [multiTenantApplicationMetricsRecent](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationmetricsrecent?view=graph-rest-beta).

Abstract base type that defines common properties for multi-tenant application metrics.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the metrics snapshot. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
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
  "id": "String (identifier)",
  "watermarkDateTime": "String (timestamp)",
  "inboundMonthlyTotalApplications": "String",
  "outboundMonthlyTotalApplications": "String"
}
```
