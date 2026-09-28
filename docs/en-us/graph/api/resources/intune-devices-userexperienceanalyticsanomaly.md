<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomaly?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# userExperienceAnalyticsAnomaly resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics anomaly entity contains anomaly details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsAnomalies](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsanomaly-list?view=graph-rest-beta) | [userExperienceAnalyticsAnomaly](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomaly?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsAnomaly](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomaly?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsAnomaly](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsanomaly-get?view=graph-rest-beta) | [userExperienceAnalyticsAnomaly](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomaly?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsAnomaly](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomaly?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsAnomaly](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsanomaly-create.md?view=graph-rest-beta) | [userExperienceAnalyticsAnomaly](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomaly?view=graph-rest-beta) | Create a new [userExperienceAnalyticsAnomaly](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomaly?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsAnomaly](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsanomaly-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsAnomaly](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomaly?view=graph-rest-beta). |
| [Update userExperienceAnalyticsAnomaly](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsanomaly-update.md?view=graph-rest-beta) | [userExperienceAnalyticsAnomaly](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomaly?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsAnomaly](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomaly?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the user experience analytics anomaly device object. |
| anomalyId | String | The unique identifier of the anomaly. |
| anomalyName | String | The name of the anomaly. |
| deviceImpactedCount | Int32 | The number of devices impacted by the anomaly. Valid values -2147483648 to 2147483647 |
| severity | [userExperienceAnalyticsAnomalySeverity](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalyseverity?view=graph-rest-beta) | The severity of the anomaly. Possible values are: high, medium, low, informational or other. Possible values are: `high`, `medium`, `low`, `informational`, `other`, `unknownFutureValue`. |
| state | [userExperienceAnalyticsAnomalyState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalystate?view=graph-rest-beta) | The state of the anomaly. Possible values are: new, active, disabled, removed or other. Possible values are: `new`, `active`, `disabled`, `removed`, `other`, `unknownFutureValue`. |
| anomalyType | [userExperienceAnalyticsAnomalyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalytype?view=graph-rest-beta) | The category of the anomaly. Possible values are: device, application, stopError, driver or other. Possible values are: `device`, `application`, `stopError`, `driver`, `other`, `unknownFutureValue`. |
| anomalyFirstOccurrenceDateTime | DateTimeOffset | Indicates the first occurrence date and time for the anomaly. |
| anomalyLatestOccurrenceDateTime | DateTimeOffset | Indicates the latest occurrence date and time for the anomaly. |
| detectionModelId | String | The unique identifier of the anomaly detection model. |
| issueId | String | The unique identifier of the anomaly detection model. |
| assetName | String | The name of the application or module that caused the anomaly. |
| assetVersion | String | The version of the application or module that caused the anomaly. |
| assetPublisher | String | The publisher of the application or module that caused the anomaly. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsAnomaly",
  "id": "String (identifier)",
  "anomalyId": "String",
  "anomalyName": "String",
  "deviceImpactedCount": 1024,
  "severity": "String",
  "state": "String",
  "anomalyType": "String",
  "anomalyFirstOccurrenceDateTime": "String (timestamp)",
  "anomalyLatestOccurrenceDateTime": "String (timestamp)",
  "detectionModelId": "String",
  "issueId": "String",
  "assetName": "String",
  "assetVersion": "String",
  "assetPublisher": "String"
}
```
