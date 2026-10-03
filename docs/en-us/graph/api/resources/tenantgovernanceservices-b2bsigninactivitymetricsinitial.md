<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsinitial?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# b2BSignInActivityMetricsInitial resource type

Namespace: microsoft.graph

Represents the initial snapshot of B2B sign-in activity metrics captured when the [related tenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0) was first discovered, establishing a baseline for monthly active guests and applications.

Inherits from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Timestamp that represents when the time B2B sign-in activity content was initially aggregated for the related tenant. |
| inboundMonthlyTotalApplications | String | The total number of applications accessed by inbound users in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-1.0). |
| inboundMonthlyTotalUsers | String | The total number of unique inbound users with sign-in activity in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-1.0). |
| outboundMonthlyTotalApplications | String | The total number of applications accessed by outbound users in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-1.0). |
| outboundMonthlyTotalUsers | String | The total number of unique outbound users with sign-in activity in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-1.0). |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.b2BSignInActivityMetricsInitial",
  "watermarkDateTime": "String (timestamp)",
  "inboundMonthlyTotalUsers": "String",
  "inboundMonthlyTotalApplications": "String",
  "outboundMonthlyTotalUsers": "String",
  "outboundMonthlyTotalApplications": "String",
  "createdDateTime": "String (timestamp)"
}
```
