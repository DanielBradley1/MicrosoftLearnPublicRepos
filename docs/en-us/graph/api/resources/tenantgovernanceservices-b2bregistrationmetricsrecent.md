<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsrecent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# b2BRegistrationMetricsRecent resource type

Namespace: microsoft.graph

Represents the most recent snapshot of B2B registration metrics, showing current guest counts between related tenants.

Inherits from [microsoft.graph.b2BRegistrationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inboundTotalUsers | String | The total number of inbound B2B guest users registered. Inherited from [microsoft.graph.b2BRegistrationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsbase?view=graph-rest-1.0). |
| outboundTotalUsers | String | The total number of outbound B2B users from this tenant registered in other tenants. Inherited from [microsoft.graph.b2BRegistrationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsbase?view=graph-rest-1.0). |
| updateDateTime | DateTimeOffset | Timestamp that represents the most recent time B2B registration data was aggregated and have sufficiently changed for the related tenant. |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. Inherited from [microsoft.graph.b2BRegistrationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsbase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.b2BRegistrationMetricsRecent",
  "watermarkDateTime": "String (timestamp)",
  "inboundTotalUsers": "String",
  "outboundTotalUsers": "String",
  "updateDateTime": "String (timestamp)"
}
```
