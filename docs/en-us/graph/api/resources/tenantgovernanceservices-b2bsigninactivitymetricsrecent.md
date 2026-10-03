<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsrecent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# b2BSignInActivityMetricsRecent resource type

Namespace: microsoft.graph

Represents the most recent snapshot of B2B sign-in activity metrics for a [related tenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-1.0), showing current monthly active guests and application counts.

Inherits from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inboundMonthlyTotalApplications | String | The total number of applications accessed by inbound users in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-1.0). |
| inboundMonthlyTotalUsers | String | The total number of unique inbound users with sign-in activity in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-1.0). |
| outboundMonthlyTotalApplications | String | The total number of applications accessed by outbound users in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-1.0). |
| outboundMonthlyTotalUsers | String | The total number of unique outbound users with sign-in activity in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-1.0). |
| updateDateTime | DateTimeOffset | Timestamp that represents the most recent time B2B registration data was aggregated and have sufficiently changed for the related tenant. |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.b2BSignInActivityMetricsRecent",
  "watermarkDateTime": "String (timestamp)",
  "inboundMonthlyTotalUsers": "String",
  "inboundMonthlyTotalApplications": "String",
  "outboundMonthlyTotalUsers": "String",
  "outboundMonthlyTotalApplications": "String",
  "updateDateTime": "String (timestamp)"
}
```
