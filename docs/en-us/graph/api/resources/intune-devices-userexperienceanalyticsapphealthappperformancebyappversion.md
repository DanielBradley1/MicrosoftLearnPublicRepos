<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# userExperienceAnalyticsAppHealthAppPerformanceByAppVersion resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics application performance entity contains app performance details by app version.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsAppHealthAppPerformanceByAppVersions](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion-list?view=graph-rest-beta) | [userExperienceAnalyticsAppHealthAppPerformanceByAppVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion?view=graph-rest-beta) collection | List properties and relationships of the [userExperienceAnalyticsAppHealthAppPerformanceByAppVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion?view=graph-rest-beta) objects. |
| [Get userExperienceAnalyticsAppHealthAppPerformanceByAppVersion](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion-get?view=graph-rest-beta) | [userExperienceAnalyticsAppHealthAppPerformanceByAppVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion?view=graph-rest-beta) | Read properties and relationships of the [userExperienceAnalyticsAppHealthAppPerformanceByAppVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion?view=graph-rest-beta) object. |
| [Create userExperienceAnalyticsAppHealthAppPerformanceByAppVersion](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion-create.md?view=graph-rest-beta) | [userExperienceAnalyticsAppHealthAppPerformanceByAppVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion?view=graph-rest-beta) | Create a new [userExperienceAnalyticsAppHealthAppPerformanceByAppVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion?view=graph-rest-beta) object. |
| [Delete userExperienceAnalyticsAppHealthAppPerformanceByAppVersion](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion-delete.md?view=graph-rest-beta) | None | Deletes a [userExperienceAnalyticsAppHealthAppPerformanceByAppVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion?view=graph-rest-beta). |
| [Update userExperienceAnalyticsAppHealthAppPerformanceByAppVersion](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion-update.md?view=graph-rest-beta) | [userExperienceAnalyticsAppHealthAppPerformanceByAppVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion?view=graph-rest-beta) | Update the properties of a [userExperienceAnalyticsAppHealthAppPerformanceByAppVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversion?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics app performance object. |
| appVersion | String | The version of the application. |
| appName | String | The name of the application. Possible values are: outlook.exe, excel.exe. Supports: $select, $OrderBy. Read-only. |
| appDisplayName | String | The friendly name of the application. Possible values are: Outlook, Excel. Supports: $select, $OrderBy. Read-only. |
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
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsAppHealthAppPerformanceByAppVersion",
  "id": "String (identifier)",
  "appVersion": "String",
  "appName": "String",
  "appDisplayName": "String",
  "appPublisher": "String",
  "appUsageDuration": 1024,
  "appCrashCount": 1024,
  "meanTimeToFailureInMinutes": 1024
}
```
