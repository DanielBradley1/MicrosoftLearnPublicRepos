<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics application performance entity contains application performance by application version device id.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceIds](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid-list?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid-get?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthappperformancebyappversiondeviceid?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics application performance by application version device id object. Supports: $select, $OrderBy. Read-only. |
| deviceId | String | The Intune device id of the device. Supports: $select, $OrderBy. Read-only. |
| deviceDisplayName | String | The name of the device. Supports: $select, $OrderBy. Read-only. |
| processedDateTime | DateTimeOffset | The date and time when the statistics were last computed. The value cannot be modified and is automatically populated when the statistics are computed. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2022 would look like this: '2022-01-01T00:00:00Z'. Returned by default. Read-only. |
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
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsAppHealthAppPerformanceByAppVersionDeviceId",
  "id": "String (identifier)",
  "deviceId": "String",
  "deviceDisplayName": "String",
  "processedDateTime": "String (timestamp)",
  "appName": "String",
  "appDisplayName": "String",
  "appPublisher": "String",
  "appVersion": "String",
  "appCrashCount": 1024
}
```
