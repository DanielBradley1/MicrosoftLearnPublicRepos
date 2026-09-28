<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalydevice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsAnomalyDevice resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics anomaly entity contains device details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsAnomalyDevices](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsanomalydevice-list?view=graph-rest-beta) | [userExperienceAnalyticsAnomalyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalydevice?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsAnomalyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalydevice?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsAnomalyDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsanomalydevice-get?view=graph-rest-beta) | [userExperienceAnalyticsAnomalyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalydevice?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsAnomalyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalydevice?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsAnomalyDevice](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsanomalydevice-create.md?view=graph-rest-beta) | [userExperienceAnalyticsAnomalyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalydevice?view=graph-rest-beta) | Create a new [userExperienceAnalyticsAnomalyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalydevice?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsAnomalyDevice](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsanomalydevice-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsAnomalyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalydevice?view=graph-rest-beta). |
| [Update userExperienceAnalyticsAnomalyDevice](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsanomalydevice-update.md?view=graph-rest-beta) | [userExperienceAnalyticsAnomalyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalydevice?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsAnomalyDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsanomalydevice?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the user experience analytics anomaly device object. |
| deviceId | String | The unique identifier of the device. |
| deviceName | String | The name of the device. |
| deviceModel | String | The model name of the device. |
| deviceManufacturer | String | The manufacturer name of the device. |
| osName | String | The name of the OS installed on the device. |
| osVersion | String | The OS version installed on the device. |
| anomalyId | String | The unique identifier of the anomaly. |
| anomalyOnDeviceFirstOccurrenceDateTime | DateTimeOffset | Indicates the first occurance date and time for the anomaly on the device. |
| anomalyOnDeviceLatestOccurrenceDateTime | DateTimeOffset | Indicates the latest occurance date and time for the anomaly on the device. |
| correlationGroupId | String | The unique identifier of the correlation group. |
| deviceStatus | [userExperienceAnalyticsDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestatus?view=graph-rest-beta) | Indicates the device status with respect to the correlation group. At risk devices are devices that share correlation group features but may not yet be affected by an anomaly, such as when a device is experiencing crashes on an application but that application has not been used on the device but is currently installed. This could lead to the device becoming anomalous if the application in question were to be used. Possible values are: anomolous, affected or atRisk. Possible values are: `anomalous`, `affected`, `atRisk`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsAnomalyDevice",
  "id": "String (identifier)",
  "deviceId": "String",
  "deviceName": "String",
  "deviceModel": "String",
  "deviceManufacturer": "String",
  "osName": "String",
  "osVersion": "String",
  "anomalyId": "String",
  "anomalyOnDeviceFirstOccurrenceDateTime": "String (timestamp)",
  "anomalyOnDeviceLatestOccurrenceDateTime": "String (timestamp)",
  "correlationGroupId": "String",
  "deviceStatus": "String"
}
```
