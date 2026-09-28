<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthruntimedetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsBatteryHealthRuntimeDetails resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics battery health runtime entity contains count of devices broken down into 3 categories - devices with runtime > 5 hours, devices with runtime 3-5 hours and devices with runtime < 3 hours.This API provides the count of devices in these 3 categories.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get userExperienceAnalyticsBatteryHealthRuntimeDetails](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthruntimedetails-get?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthRuntimeDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthruntimedetails?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsBatteryHealthRuntimeDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthruntimedetails?view=graph-rest-beta) object. |
| [Update userExperienceAnalyticsBatteryHealthRuntimeDetails](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthruntimedetails-update.md?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthRuntimeDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthruntimedetails?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsBatteryHealthRuntimeDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthruntimedetails?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics battery health runtime object. |
| activeDevices | Int32 | Number of active devices within the tenant. Valid values 0 to 2147483647 |
| batteryRuntimeGood | Int32 | Number of devices whose active runtime is greater than 5 hours. Valid values 0 to 2147483647 |
| batteryRuntimeFair | Int32 | Number of devices whose active runtime is greater than 3 hours but lesser than 5 hours. Valid values 0 to 2147483647 |
| batteryRuntimePoor | Int32 | Number of devices whose active runtime is lesser than 3 hours. Valid values 0 to 2147483647 |
| lastRefreshedDateTime | DateTimeOffset | Recorded date time of this runtime details instance. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsBatteryHealthRuntimeDetails",
  "id": "String (identifier)",
  "activeDevices": 1024,
  "batteryRuntimeGood": 1024,
  "batteryRuntimeFair": 1024,
  "batteryRuntimePoor": 1024,
  "lastRefreshedDateTime": "String (timestamp)"
}
```
