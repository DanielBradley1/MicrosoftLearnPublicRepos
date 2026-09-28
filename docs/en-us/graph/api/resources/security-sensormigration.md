<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-sensormigration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# sensorMigration resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Microsoft Defender for Identity sensor that can be migrated from the classic portal to the unified security portal.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-identitycontainer-list-sensormigration?view=graph-rest-beta) | [microsoft.graph.security.sensorMigration](https://learn.microsoft.com/en-us/graph/api/resources/security-sensormigration?view=graph-rest-beta) collection | Get a list of the sensorMigration objects and their properties. |
| [Migrate](https://learn.microsoft.com/en-us/graph/api/security-sensormigration-migrate?view=graph-rest-beta) | [microsoft.graph.security.migrateSensorsResult](https://learn.microsoft.com/en-us/graph/api/resources/security-migratesensorsresult?view=graph-rest-beta) | Migrate the specified sensors to the unified security portal. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time the sensor was created. |
| displayName | String | The display name of the sensor. |
| domainName | String | The fully qualified domain name \(FQDN\) of the domain controller where the sensor is installed. |
| healthStatus | [microsoft.graph.security.sensorHealthStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-beta#sensorhealthstatus-values) | The health status of the sensor. The possible values are: `healthy`, `notHealthyLow`, `notHealthyMedium`, `notHealthyHigh`, `unknownFutureValue`. |
| id | String | The unique identifier for the sensor. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| migrationState | [microsoft.graph.security.migrationState](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-beta#migrationstate-values) | The migration state of the sensor. The possible values are: `readyForMigration`, `notReadyForMigration`, `upToDate`, `migrationFailed`, `migrating`, `unknownFutureValue`. |
| sensorType | [microsoft.graph.security.sensorType](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-beta#sensortype-values) | The type of sensor. The possible values are: `adConnectIntegrated`, `adcsIntegrated`, `adfsIntegrated`, `domainControllerIntegrated`, `domainControllerStandalone`, `unknownFutureValue`. |
| serviceStatus | [microsoft.graph.security.serviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-beta#servicestatus-values) | The status of the sensor service. The possible values are: `stopped`, `starting`, `running`, `disabled`, `onboarding`, `unknown`, `unknownFutureValue`. |
| version | String | The version number of the sensor software. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.sensorMigration",
  "id": "String (identifier)",
  "displayName": "String",
  "sensorType": "String",
  "version": "String",
  "createdDateTime": "String (timestamp)",
  "domainName": "String",
  "healthStatus": "String",
  "serviceStatus": "String",
  "migrationState": "String"
}
```
