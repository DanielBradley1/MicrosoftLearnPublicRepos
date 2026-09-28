<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics battery health runtime history entity contains the trend of runtime of a device over a period of 30 days

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsBatteryHealthDeviceRuntimeHistories](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory-list?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory-get?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory-create.md?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory?view=graph-rest-beta) | Create a new [userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory?view=graph-rest-beta). |
| [Update userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory-update.md?view=graph-rest-beta) | [userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsbatteryhealthdeviceruntimehistory?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics battery health runtime object. |
| deviceId | String | The unique identifier of the device, Intune DeviceID or SCCM device id. |
| runtimeDateTime | String | The datetime for the instance of runtime history. |
| estimatedRuntimeInMinutes | Int32 | The estimated runtime of the device when the battery is fully charged. Unit in minutes. Valid values 0 to 2147483647 |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsBatteryHealthDeviceRuntimeHistory",
  "id": "String (identifier)",
  "deviceId": "String",
  "runtimeDateTime": "String",
  "estimatedRuntimeInMinutes": 1024
}
```
