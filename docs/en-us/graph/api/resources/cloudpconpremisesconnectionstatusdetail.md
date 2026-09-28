<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnectionstatusdetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-23 -->

# cloudPcOnPremisesConnectionStatusDetail resource type

Namespace: microsoft.graph

The status details of a [cloudPcOnPremisesConnection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0).

Important

**On-premises network connection** has been renamed as **Azure network connection**. **cloudPcOnPremisesConnection** objects here are equivalent to **Azure network connection** for the Cloud PC product.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endDateTime | DateTimeOffset | The end time of the connection health check. The Timestamp is shown in ISO 8601 format and Coordinated Universal Time \(UTC\). For example, midnight UTC on Jan 1, 2014 appears as `2014-01-01T00:00:00Z`. Read-Only. |
| healthChecks | [cloudPcOnPremisesConnectionHealthCheck](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnectionhealthcheck?view=graph-rest-1.0) collection | A list of all checks that have been run on the connection. Read-Only. |
| startDateTime | DateTimeOffset | The start time of the health check. The timestamp is shown in ISO 8601 format and Coordinated Universal Time \(UTC\). For example, midnight UTC on Jan 1, 2014 appear as `2014-01-01T00:00:00Z`. Read-Only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcOnPremisesConnectionStatusDetail",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "healthChecks": [
    {
      "@odata.type": "microsoft.graph.cloudPcOnPremisesConnectionHealthCheck",
      "displayName": "String",
      "status": "String",
      "startDateTime": "String (timestamp)",
      "endDateTime": "String (timestamp)",
      "errorType": "String",
      "recommendedAction": "String",
      "additionalDetail": "String",
      "correlationId": "String"
    }
  ]
}
```
