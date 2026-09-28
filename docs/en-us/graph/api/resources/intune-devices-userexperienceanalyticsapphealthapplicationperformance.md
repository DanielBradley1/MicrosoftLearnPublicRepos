<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthapplicationperformance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsAppHealthApplicationPerformance resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics application performance entity contains application performance details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsAppHealthApplicationPerformances](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthapplicationperformance-list?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthApplicationPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthapplicationperformance?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsAppHealthApplicationPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthapplicationperformance?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsAppHealthApplicationPerformance](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthapplicationperformance-get?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthApplicationPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthapplicationperformance?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsAppHealthApplicationPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthapplicationperformance?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsAppHealthApplicationPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthapplicationperformance-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthApplicationPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthapplicationperformance?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsAppHealthApplicationPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthapplicationperformance?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsAppHealthApplicationPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthapplicationperformance-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsAppHealthApplicationPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthapplicationperformance?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsAppHealthApplicationPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthapplicationperformance-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthApplicationPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthapplicationperformance?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsAppHealthApplicationPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthapplicationperformance?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics application performance object. Supports: $select, $OrderBy. Read-only. |
| appHangCount | Int32 | The number of hangs for the application. Supports: $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
| appHealthScore | Double | The health score of the application. Valid values 0 to 100. Supports: $filter, $select, $OrderBy. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| appHealthStatus | String | The overall health status of the application. Read-only. |
| allOrgsHealthScore | Double | The median health score of the application across all organizations. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| activeDeviceCount | Int32 | The health score of the application. Valid values 0 to 100. Supports: $filter, $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
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
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsAppHealthApplicationPerformance",
  "id": "String (identifier)",
  "appHangCount": 1024,
  "appHealthScore": "4.2",
  "appHealthStatus": "String",
  "allOrgsHealthScore": "4.2",
  "activeDeviceCount": 1024,
  "appName": "String",
  "appDisplayName": "String",
  "appPublisher": "String",
  "appUsageDuration": 1024,
  "appCrashCount": 1024,
  "meanTimeToFailureInMinutes": 1024
}
```
