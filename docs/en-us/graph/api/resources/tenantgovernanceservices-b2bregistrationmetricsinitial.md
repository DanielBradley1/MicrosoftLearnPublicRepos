<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsinitial?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# b2BRegistrationMetricsInitial resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the initial snapshot of B2B registration metrics captured when the relationship between two tenants was first discovered, establishing a baseline for guest counts.

Inherits from [microsoft.graph.b2BRegistrationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsbase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Timestamp that represents the date time that B2B registration data was initially aggregated. |
| id | String | Unique identifier for the metrics snapshot. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| inboundTotalUsers | String | The total number of inbound B2B guest users registered. Inherited from [microsoft.graph.b2BRegistrationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsbase?view=graph-rest-beta). |
| outboundTotalUsers | String | The total number of outbound B2B users from this tenant registered in other tenants. Inherited from [microsoft.graph.b2BRegistrationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsbase?view=graph-rest-beta). |
| watermarkDateTime | DateTimeOffset | The date and time when the metrics snapshot was taken. Inherited from [microsoft.graph.b2BRegistrationMetricsBase](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-b2bregistrationmetricsbase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.b2BRegistrationMetricsInitial",
  "id": "String (identifier)",
  "watermarkDateTime": "String (timestamp)",
  "inboundTotalUsers": "String",
  "outboundTotalUsers": "String",
  "createdDateTime": "String (timestamp)"
}
```
