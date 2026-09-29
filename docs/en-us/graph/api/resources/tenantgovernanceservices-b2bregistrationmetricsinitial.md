<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsinitial?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# b2BRegistrationMetricsInitial resource type

Namespace: microsoft.graph

Represents the initial snapshot of B2B registration metrics captured when the relationship between two tenants was first discovered, establishing a baseline for guest counts.

Inherits from [microsoft.graph.b2BRegistrationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Timestamp that represents the date time that B2B registration data was initially aggregated. |
| inboundTotalUsers | String | The total number of inbound B2B guest users registered. Inherited from [microsoft.graph.b2BRegistrationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsbase?view=graph-rest-1.0). |
| outboundTotalUsers | String | The total number of outbound B2B users from this tenant registered in other tenants. Inherited from [microsoft.graph.b2BRegistrationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsbase?view=graph-rest-1.0). |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. Inherited from [microsoft.graph.b2BRegistrationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsbase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.b2BRegistrationMetricsInitial",
  "watermarkDateTime": "String (timestamp)",
  "inboundTotalUsers": "String",
  "outboundTotalUsers": "String",
  "createdDateTime": "String (timestamp)"
}
```
