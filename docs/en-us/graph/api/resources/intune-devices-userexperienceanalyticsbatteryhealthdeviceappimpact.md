<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsBatteryHealthDeviceAppImpact resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics battery health device app impact entity contains battery usage related information at an app level for a given device.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsBatteryHealthDeviceAppImpacts](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact-list?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthDeviceAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsBatteryHealthDeviceAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsBatteryHealthDeviceAppImpact](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact-get?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthDeviceAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsBatteryHealthDeviceAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsBatteryHealthDeviceAppImpact](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact-create.md?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthDeviceAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact?view=graph-rest-beta) | Create a new [userExperienceAnalyticsBatteryHealthDeviceAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsBatteryHealthDeviceAppImpact](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsBatteryHealthDeviceAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact?view=graph-rest-beta). |
| [Update userExperienceAnalyticsBatteryHealthDeviceAppImpact](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact-update.md?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthDeviceAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsBatteryHealthDeviceAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceappimpact?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics battery device app impact object. |
| deviceId | String | The unique identifier of the device, Intune DeviceID or SCCM device id. |
| appName | String | App name. Eg: oltk.exe |
| appDisplayName | String | User friendly display name for the app. Eg: Outlook |
| appPublisher | String | App publisher. Eg: Microsoft Corporation |
| isForegroundApp | Boolean | true if the user had active interaction with the app. |
| batteryUsagePercentage | Double | The percent of total battery power used by this application when the device was not plugged into AC power, over 14 days. Unit in percentage. Valid values 0 to 1.79769313486232E+308 |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsBatteryHealthDeviceAppImpact",
  "id": "String (identifier)",
  "deviceId": "String",
  "appName": "String",
  "appDisplayName": "String",
  "appPublisher": "String",
  "isForegroundApp": true,
  "batteryUsagePercentage": "4.2"
}
```
