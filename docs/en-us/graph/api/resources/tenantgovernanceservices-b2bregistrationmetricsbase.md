<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# b2BRegistrationMetricsBase resource type

Namespace: microsoft.graph

This resource is an abstract base type and does not appear directly in API responses. Use the concrete types [b2BRegistrationMetricsInitial](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsinitial?view=graph-rest-1.0) or [b2BRegistrationMetricsRecent](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsrecent?view=graph-rest-1.0).

Abstract base type that defines common properties for B2B registration metrics snapshots.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inboundTotalUsers | String | The total number of inbound B2B guest users registered. |
| outboundTotalUsers | String | The total number of outbound B2B users from this tenant registered in other tenants. |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

Note

This abstract type is not returned in API responses. See concrete implementations.

```json
{
  "@odata.type": "#microsoft.graph.b2BRegistrationMetricsBase",
  "watermarkDateTime": "String (timestamp)",
  "inboundTotalUsers": "String",
  "outboundTotalUsers": "String"
}
```
