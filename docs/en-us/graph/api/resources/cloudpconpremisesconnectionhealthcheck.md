<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnectionhealthcheck?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-21 -->

# cloudPcOnPremisesConnectionHealthCheck resource type

Namespace: microsoft.graph

The result of a Cloud PC Azure network connection health check.

Important

**On-premises network connection** has been renamed as **Azure network connection**. **cloudPcOnPremisesConnection** objects here are equivalent to **Azure network connection** for the Cloud PC product.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalDetail | String | Additional details about the health check or the recommended action. For exmaple, the string value can be download.microsoft.com:443;software-download.microsoft.com:443; Read-only. |
| correlationId | String | The unique identifier of the health check item-related activities. This identifier can be useful in troubleshooting. |
| displayName | String | The display name for this health check item. |
| endDateTime | DateTimeOffset | The value cannot be modified and is automatically populated when the health check ends. The Timestamp type represents date and time information using ISO 8601 format and is in Coordinated Universal Time \(UTC\). For example, midnight UTC on Jan 1, 2024 would look like this: '2024-01-01T00:00:00Z'. Returned by default. Read-only. |
| errorType | [cloudPcOnPremisesConnectionHealthCheckErrorType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnectionhealthcheckerrortype?view=graph-rest-1.0) | The type of error that occurred during this health check. Read-only. |
| recommendedAction | String | The recommended action to fix the corresponding error. For example, The Active Directory domain join check failed because the password of the domain join user has expired. Read-Only. |
| startDateTime | DateTimeOffset | The value cannot be modified and is automatically populated when the health check starts. The Timestamp type represents date and time information using ISO 8601 format and is in Coordinated Universal Time \(UTC\). For example, midnight UTC on Jan 1, 2024 would look like this: '2024-01-01T00:00:00Z'. Returned by default. Read-only. |
| status | [cloudPcOnPremisesConnectionStatus](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-1.0#cloudpconpremisesconnectionstatus-values) | The status of the health check item. The possible values are: `pending`, `running`, `passed`, `failed`, `warning`, `informational`, `unknownFutureValue`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcOnPremisesConnectionHealthCheck",
  "displayName": "String",
  "status": "String",
  "startDateTime": "String (timestamp)",
  "endDateTime": "String (timestamp)",
  "errorType": "String",
  "recommendedAction": "String",
  "additionalDetail": "String",
  "correlationId": "String"
}
```
