<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthappimpact?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsBatteryHealthAppImpact resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics battery health app impact entity contains battery usage related information at an app level for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsBatteryHealthAppImpacts](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthappimpact-list?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthappimpact?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsBatteryHealthAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthappimpact?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsBatteryHealthAppImpact](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthappimpact-get?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthappimpact?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsBatteryHealthAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthappimpact?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsBatteryHealthAppImpact](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthappimpact-create.md?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthappimpact?view=graph-rest-beta) | Create a new [userExperienceAnalyticsBatteryHealthAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthappimpact?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsBatteryHealthAppImpact](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthappimpact-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsBatteryHealthAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthappimpact?view=graph-rest-beta). |
| [Update userExperienceAnalyticsBatteryHealthAppImpact](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthappimpact-update.md?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthappimpact?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsBatteryHealthAppImpact](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthappimpact?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics battery app impact object. |
| activeDevices | Int32 | Number of active devices for using that app over a 14-day period. Valid values 0 to 2147483647 |
| appName | String | App name. Eg: oltk.exe |
| appDisplayName | String | User friendly display name for the app. Eg: Outlook |
| appPublisher | String | App publisher. Eg: Microsoft Corporation |
| isForegroundApp | Boolean | true if the user had active interaction with the app. |
| batteryUsagePercentage | Double | The percent of total battery power used by this application when the device was not plugged into AC power, over 14 days computed across all devices in the tenant. Unit in percentage. Valid values 0 to 1.79769313486232E+308 |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsBatteryHealthAppImpact",
  "id": "String (identifier)",
  "activeDevices": 1024,
  "appName": "String",
  "appDisplayName": "String",
  "appPublisher": "String",
  "isForegroundApp": true,
  "batteryUsagePercentage": "4.2"
}
```
