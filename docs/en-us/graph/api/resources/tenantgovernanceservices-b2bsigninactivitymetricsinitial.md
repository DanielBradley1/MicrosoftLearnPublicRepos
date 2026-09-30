<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsinitial?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# b2BSignInActivityMetricsInitial resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the initial snapshot of B2B sign-in activity metrics captured when the [related tenant](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-relatedtenant?view=graph-rest-beta) was first discovered, establishing a baseline for monthly active guests and applications.

Inherits from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Timestamp that represents when the time B2B sign-in activity content was initially aggregated for the related tenant. |
| id | String | Unique identifier for the metrics snapshot. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| inboundMonthlyTotalApplications | String | The total number of applications accessed by inbound users in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-beta). |
| inboundMonthlyTotalUsers | String | The total number of unique inbound users with sign-in activity in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-beta). |
| outboundMonthlyTotalApplications | String | The total number of applications accessed by outbound users in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-beta). |
| outboundMonthlyTotalUsers | String | The total number of unique outbound users with sign-in activity in the last month. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-beta). |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. Inherited from [microsoft.graph.b2BSignInActivityMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bsigninactivitymetricsbase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.b2BSignInActivityMetricsInitial",
  "id": "String (identifier)",
  "watermarkDateTime": "String (timestamp)",
  "inboundMonthlyTotalUsers": "String",
  "inboundMonthlyTotalApplications": "String",
  "outboundMonthlyTotalUsers": "String",
  "outboundMonthlyTotalApplications": "String",
  "createdDateTime": "String (timestamp)"
}
```
