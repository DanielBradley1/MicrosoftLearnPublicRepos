<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnectionstatusdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-16 -->

# cloudPcOnPremisesConnectionStatusDetails resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The **cloudPcOnPremisesConnectionStatusDetails** resource is deprecated and stopped returning data on January 31, 2024. Going forward, use the [cloudPcOnPremisesConnectionStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnectionstatusdetail?view=graph-rest-beta) resource.

The status details of a [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-beta).

Important

**On-premises network connection** has been renamed as **Azure network connection**. **cloudPcOnPremisesConnection** objects here are equivalent to **Azure network connection** for the Cloud PC product.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endDateTime | DateTimeOffset | The end time of the connection health check. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| healthChecks | [cloudPcOnPremisesConnectionHealthCheck](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnectionhealthcheck?view=graph-rest-beta) collection | All checks that are done on the connection. |
| startDateTime | DateTimeOffset | The start time of the connection health check. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcOnPremisesConnectionStatusDetails",
  "endDateTime": "String (timestamp)",
  "healthChecks": [{ "@odata.type": "microsoft.graph.cloudPcOnPremisesConnectionHealthCheck" }],
  "startDateTime": "String (timestamp)"
}
```
