<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsrecent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# b2BSignInActivityMetricsRecent resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the most recent snapshot of B2B sign-in activity metrics for a [related tenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta), showing current monthly active guests and application counts.

Inherits from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the metrics snapshot. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| inboundMonthlyTotalApplications | String | The total number of applications accessed by inbound users in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-beta). |
| inboundMonthlyTotalUsers | String | The total number of unique inbound users with sign-in activity in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-beta). |
| outboundMonthlyTotalApplications | String | The total number of applications accessed by outbound users in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-beta). |
| outboundMonthlyTotalUsers | String | The total number of unique outbound users with sign-in activity in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-beta). |
| updateDateTime | DateTimeOffset | Timestamp that represents the most recent time B2B registration data was aggregated and have sufficiently changed for the related tenant. |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.b2BSignInActivityMetricsRecent",
  "id": "String (identifier)",
  "watermarkDateTime": "String (timestamp)",
  "inboundMonthlyTotalUsers": "String",
  "inboundMonthlyTotalApplications": "String",
  "outboundMonthlyTotalUsers": "String",
  "outboundMonthlyTotalApplications": "String",
  "updateDateTime": "String (timestamp)"
}
```
