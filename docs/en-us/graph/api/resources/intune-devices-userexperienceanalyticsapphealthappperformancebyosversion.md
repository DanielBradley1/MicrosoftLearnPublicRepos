<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsAppHealthAppPerformanceByOSVersion resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics application performance entity contains app performance details by OS version.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsAppHealthAppPerformanceByOSVersions](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion-list?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthAppPerformanceByOSVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsAppHealthAppPerformanceByOSVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsAppHealthAppPerformanceByOSVersion](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion-get?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthAppPerformanceByOSVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsAppHealthAppPerformanceByOSVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsAppHealthAppPerformanceByOSVersion](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthAppPerformanceByOSVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsAppHealthAppPerformanceByOSVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsAppHealthAppPerformanceByOSVersion](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsAppHealthAppPerformanceByOSVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsAppHealthAppPerformanceByOSVersion](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthAppPerformanceByOSVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsAppHealthAppPerformanceByOSVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyosversion?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics application performance by OS version object. Supports: $select, $OrderBy. Read-only. |
| osVersion | String | The OS version of the application. Supports: $select, $OrderBy. Read-only. |
| osBuildNumber | String | The OS build number of the application. Supports: $select, $OrderBy. Read-only. |
| activeDeviceCount | Int32 | The number of devices where the application has been active. Valid values 0 to 2147483647. Supports: $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
| appName | String | The name of the application. The possible values are: outlook.exe, excel.exe. Supports: $select, $OrderBy. Read-only. |
| appDisplayName | String | The friendly name of the application. The possible values are: Outlook, Excel. Supports: $select, $OrderBy. Read-only. |
| appPublisher | String | The publisher of the application. Supports: $select, $OrderBy. Read-only. |
| appUsageDuration | Int32 | The total usage time of the application in minutes. Valid values 0 to 2147483647. Supports: $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
| appCrashCount | Int32 | The number of crashes for the application. Valid values 0 to 2147483647. Supports: $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
| meanTimeToFailureInMinutes | Int32 | The mean time to failure for the application in minutes. Valid values 0 to 2147483647. Supports: $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsAppHealthAppPerformanceByOSVersion",
  "id": "String (identifier)",
  "osVersion": "String",
  "osBuildNumber": "String",
  "activeDeviceCount": 1024,
  "appName": "String",
  "appDisplayName": "String",
  "appPublisher": "String",
  "appUsageDuration": 1024,
  "appCrashCount": 1024,
  "meanTimeToFailureInMinutes": 1024
}
```
