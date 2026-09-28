<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-sensor?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-05 -->

# sensor resource type

Namespace: microsoft.graph.security

Represents a Microsoft Defender for Identity sensor.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-identitycontainer-list-sensors?view=graph-rest-1.0) | [microsoft.graph.security.sensor](https://learn.microsoft.com/en-us/graph/api/resources/security-sensor?view=graph-rest-1.0) collection | Get a list of [sensor](https://learn.microsoft.com/en-us/graph/api/resources/security-sensor?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-sensor-get?view=graph-rest-1.0) | [microsoft.graph.security.sensor](https://learn.microsoft.com/en-us/graph/api/resources/security-sensor?view=graph-rest-1.0) | Read the properties and relationships of a [sensor](https://learn.microsoft.com/en-us/graph/api/resources/security-sensor?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-sensor-update?view=graph-rest-1.0) | [microsoft.graph.security.sensor](https://learn.microsoft.com/en-us/graph/api/resources/security-sensor?view=graph-rest-1.0) | Update the properties of a [sensor](https://learn.microsoft.com/en-us/graph/api/resources/security-sensor?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-sensor-delete?view=graph-rest-1.0) | None | Delete a [sensor](https://learn.microsoft.com/en-us/graph/api/resources/security-sensor?view=graph-rest-1.0) object. |
| [Get deployment access key](https://learn.microsoft.com/en-us/graph/api/security-sensor-getdeploymentaccesskey?view=graph-rest-1.0) | [microsoft.graph.security.deploymentAccessKeyType](https://learn.microsoft.com/en-us/graph/api/resources/security-deploymentaccesskeytype?view=graph-rest-1.0) | Get the deployment access key for Microsoft Defender for Identity that is required to install sensors associated with the workspace. |
| [Get deployment package URI](https://learn.microsoft.com/en-us/graph/api/security-sensor-getdeploymentpackageuri?view=graph-rest-1.0) | [microsoft.graph.security.sensorDeploymentPackage](https://learn.microsoft.com/en-us/graph/api/resources/security-sensordeploymentpackage?view=graph-rest-1.0) | Get the [sensor](https://learn.microsoft.com/en-us/graph/api/resources/security-sensor?view=graph-rest-1.0) deployment package URL and version. |
| [Regenerate deployment access key](https://learn.microsoft.com/en-us/graph/api/security-sensor-regeneratedeploymentaccesskey?view=graph-rest-1.0) | [microsoft.graph.security.deploymentAccessKeyType](https://learn.microsoft.com/en-us/graph/api/resources/security-deploymentaccesskeytype?view=graph-rest-1.0) | Generate a new deployment access key that can be used to install a [sensor](https://learn.microsoft.com/en-us/graph/api/resources/security-sensor?view=graph-rest-1.0) associated with the workspace. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the sensor was generated. The Timestamp represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| deploymentStatus | [microsoft.graph.security.deploymentStatus](#deploymentstatus-values) | The deployment status of the sensor. The possible values are: `upToDate`, `outdated`, `updating`, `updateFailed`, `notConfigured`, `unreachable`, `disconnected`, `startFailure`, `syncing`, `unknownFutureValue`. |
| displayName | String | The display name of the sensor. |
| domainName | String | The fully qualified domain name of the sensor. |
| healthStatus | [microsoft.graph.security.sensorHealthStatus](#sensorhealthstatus-values) | The health status of the sensor. The possible values are: `healthy`, `notHealthyLow`, `notHealthyMedium`, `notHealthyHigh`, `unknownFutureValue`. |
| id | String | Unique identifier to represent the sensor. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| openHealthIssuesCount | Int64 | This field displays the count of health issues related to this sensor. |
| sensorType | [microsoft.graph.security.sensorType](#sensortype-values) | The type of the sensor. The possible values are: `adConnectIntegrated`, `adcsIntegrated`, `adfsIntegrated`, `domainControllerIntegrated`, `domainControllerStandalone`, `unknownFutureValue`. |
| serviceStatus | microsoft.graph.security.serviceStatus | The service status. The possible values are: `stopped`, `starting`, `running`, `disabled`, `onboarding`, `unknown`, `unknownFutureValue`. |
| settings | [microsoft.graph.security.sensorSettings](https://learn.microsoft.com/en-us/graph/api/resources/security-sensorsettings?view=graph-rest-1.0) | Sensor settings information. |
| version | String | The version of the sensor. |

### deploymentStatus values

| Member | Description |
| :--- | :--- |
| upToDate | Sensor is running a current version of the sensor. |
| outdated | Sensor is running a version of the software that is at least three versions behind the current version. |
| updating | Sensor software is being updated. |
| updateFailed | Sensor failed to update to a new version. |
| notConfigured | Sensor requires more configuration before it's fully operational. This applies to sensors installed on ADFS and ADCS servers or standalone sensors. |
| unreachable | The domain controller was deleted from Active Directory. However, the sensor installation wasn't uninstalled and removed from the domain controller before it was decommissioned. You can safely delete this entry. |
| disconnected | The Defender for Identity service hasn't seen any communication from this sensor in 10 minutes. |
| startFailure | Sensor didn't pull configuration for more than 30 minutes. |
| syncing | Sensor has configuration updates pending, but it didn't yet pull the new configuration. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### sensorHealthStatus values

| Member | Description |
| :--- | :--- |
| healthy | No opened health issues. |
| notHealthyLow | The highest severity opened health issue is low. |
| notHealthyMedium | The highest severity opened health issue is medium. |
| notHealthyHigh | The highest severity opened health issue is high. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### sensorType values

| Member | Description |
| :--- | :--- |
| adConnectIntegrated | Entra Connect sensor. |
| adcsIntegrated | Active Directory Certificate Services \(ADCS\) sensor. |
| adfsIntegrated | Active Directory Federation Services \(ADFS\) sensor. |
| domainControllerIntegrated | Domain controller sensor. |
| domainControllerStandalone | Standalone sensor. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| healthIssues | [microsoft.graph.security.healthIssue](https://learn.microsoft.com/en-us/graph/api/resources/security-healthissue?view=graph-rest-1.0) collection | Represents potential issues within a customer's Microsoft Defender for Identity configuration that Microsoft Defender for Identity identified related to the sensor. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.sensor",
  "createdDateTime": "String (timestamp)",
  "deploymentStatus": "String",
  "displayName": "String",
  "domainName": "String",
  "healthStatus": "String",
  "id": "String (identifier)",
  "openHealthIssuesCount": "Int64",
  "sensorType": "String",
  "settings": {"@odata.type": "microsoft.graph.security.sensorSettings"},
  "version": "String",
  "serviceStatus": "String"
}
```
