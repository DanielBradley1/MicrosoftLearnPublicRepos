<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdeviceperformance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-13 -->

# userExperienceAnalyticsDevicePerformance resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics device performance entity contains device boot performance details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsDevicePerformances](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsdeviceperformance-list?view=graph-rest-1.0) | [userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdeviceperformance?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdeviceperformance?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsdeviceperformance-get?view=graph-rest-1.0) | [userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdeviceperformance?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdeviceperformance?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdeviceperformance-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdeviceperformance?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdeviceperformance?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdeviceperformance-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdeviceperformance?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdeviceperformance-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdeviceperformance?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdeviceperformance?view=graph-rest-1.0) object. |
| [summarizeDevicePerformanceDevices function](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsdeviceperformance-summarizedeviceperformancedevices?view=graph-rest-1.0) | [userExperienceAnalyticsDevicePerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdeviceperformance?view=graph-rest-1.0) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics device boot performance device. |
| deviceName | String | The user experience analytics device name. |
| model | String | The user experience analytics device model. |
| manufacturer | String | The user experience analytics device manufacturer. |
| diskType | [diskType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-disktype?view=graph-rest-1.0) | The user experience analytics device disk type. The possible values are: `unknown`, `hdd`, `ssd`, `unknownFutureValue`. |
| operatingSystemVersion | String | The user experience analytics device Operating System version. |
| bootScore | Int32 | The user experience analytics device boot score. |
| coreBootTimeInMs | Int32 | The user experience analytics device core boot time in milliseconds. |
| groupPolicyBootTimeInMs | Int32 | The user experience analytics device group policy boot time in milliseconds. |
| healthStatus | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-1.0) | The health state of the user experience analytics device. The possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |
| loginScore | Int32 | The user experience analytics device login score. |
| coreLoginTimeInMs | Int32 | The user experience analytics device core login time in milliseconds. |
| groupPolicyLoginTimeInMs | Int32 | The user experience analytics device group policy login time in milliseconds. |
| deviceCount | Int64 | User experience analytics summarized device count. |
| responsiveDesktopTimeInMs | Int32 | The user experience analytics responsive desktop time in milliseconds. |
| blueScreenCount | Int32 | Number of Blue Screens in the last 30 days. Valid values 0 to 9999999 |
| restartCount | Int32 | Number of Restarts in the last 30 days. Valid values 0 to 9999999 |
| averageBlueScreens | Double | Average \(mean\) number of Blue Screens per device in the last 30 days. Valid values 0 to 9999999 |
| averageRestarts | Double | Average \(mean\) number of Restarts per device in the last 30 days. Valid values 0 to 9999999 |
| startupPerformanceScore | Double | The user experience analytics device startup performance score. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| modelStartupPerformanceScore | Double | The user experience analytics model level startup performance score. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsDevicePerformance",
  "id": "String (identifier)",
  "deviceName": "String",
  "model": "String",
  "manufacturer": "String",
  "diskType": "String",
  "operatingSystemVersion": "String",
  "bootScore": 1024,
  "coreBootTimeInMs": 1024,
  "groupPolicyBootTimeInMs": 1024,
  "healthStatus": "String",
  "loginScore": 1024,
  "coreLoginTimeInMs": 1024,
  "groupPolicyLoginTimeInMs": 1024,
  "deviceCount": 1024,
  "responsiveDesktopTimeInMs": 1024,
  "blueScreenCount": 1024,
  "restartCount": 1024,
  "averageBlueScreens": "4.2",
  "averageRestarts": "4.2",
  "startupPerformanceScore": "4.2",
  "modelStartupPerformanceScore": "4.2"
}
```
