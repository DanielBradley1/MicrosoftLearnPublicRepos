<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics application performance entity contains application performance by application version details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetailses](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails-list?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails-get?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondetails?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics application performance by application version details object. Supports: $select, $OrderBy. Read-only. |
| deviceCountWithCrashes | Int32 | The total number of devices that have reported one or more application crashes for this application and version. Valid values 0 to 2147483647. Supports: $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
| isMostUsedVersion | Boolean | When TRUE, indicates the version of application is the most used version for that application. When FALSE, indicates the version is not the most used version. FALSE by default. Supports: $select, $OrderBy. Read-only. |
| isLatestUsedVersion | Boolean | When TRUE, indicates the version of application is the latest version for that application that is in use. When FALSE, indicates the version is not the latest version. FALSE by default. Supports: $select, $OrderBy. |
| appName | String | The name of the application. |
| appDisplayName | String | The friendly name of the application. |
| appPublisher | String | The publisher of the application. |
| appVersion | String | The version of the application. |
| appCrashCount | Int32 | The number of crashes for the app. Valid values -2147483648 to 2147483647 |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDetails",
  "id": "String (identifier)",
  "deviceCountWithCrashes": 1024,
  "isMostUsedVersion": true,
  "isLatestUsedVersion": true,
  "appName": "String",
  "appDisplayName": "String",
  "appPublisher": "String",
  "appVersion": "String",
  "appCrashCount": 1024
}
```
