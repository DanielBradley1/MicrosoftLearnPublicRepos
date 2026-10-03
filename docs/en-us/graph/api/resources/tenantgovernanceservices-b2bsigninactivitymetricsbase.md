<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# b2BSignInActivityMetricsBase resource type

Namespace: microsoft.graph

This resource is an abstract base type and does not appear directly in API responses. Use the concrete types [b2BSignInActivityMetricsInitial](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsinitial?view=graph-rest-1.0) or [b2BSignInActivityMetricsRecent](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsrecent?view=graph-rest-1.0).

Abstract base type that defines common properties for B2B sign-in activity metrics.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inboundMonthlyTotalApplications | String | The total number of applications accessed by inbound users in the last month. |
| inboundMonthlyTotalUsers | String | The total number of unique inbound users with sign-in activity in the last month. |
| outboundMonthlyTotalApplications | String | The total number of applications accessed by outbound users in the last month. |
| outboundMonthlyTotalUsers | String | The total number of unique outbound users with sign-in activity in the last month. |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

Note

This abstract type is not returned in API responses. See concrete implementations.

```json
{
  "@odata.type": "#microsoft.graph.b2BSignInActivityMetricsBase",
  "watermarkDateTime": "String (timestamp)",
  "inboundMonthlyTotalUsers": "String",
  "inboundMonthlyTotalApplications": "String",
  "outboundMonthlyTotalUsers": "String",
  "outboundMonthlyTotalApplications": "String"
}
```
