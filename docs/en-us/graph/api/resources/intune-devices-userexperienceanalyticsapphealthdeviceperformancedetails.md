<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# userExperienceAnalyticsAppHealthDevicePerformanceDetails resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics device performance entity contains device performance details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsAppHealthDevicePerformanceDetailses](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails-list?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthDevicePerformanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsAppHealthDevicePerformanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsAppHealthDevicePerformanceDetails](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails-get?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthDevicePerformanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsAppHealthDevicePerformanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsAppHealthDevicePerformanceDetails](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthDevicePerformanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsAppHealthDevicePerformanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsAppHealthDevicePerformanceDetails](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsAppHealthDevicePerformanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsAppHealthDevicePerformanceDetails](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthDevicePerformanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsAppHealthDevicePerformanceDetails](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthdeviceperformancedetails?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics device performance details object. Supports: $select, $OrderBy. Read-only. |
| eventDateTime | DateTimeOffset | The time the event occurred. The value cannot be modified and is automatically populated when the statistics are computed. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2022 would look like this: '2022-01-01T00:00:00Z'. Returned by default. Read-only. |
| eventType | String | The type of the event. Supports: $select, $OrderBy. Read-only. |
| appDisplayName | String | The friendly name of the application for which the event occurred. The possible values are: outlook.exe, excel.exe. Supports: $select, $OrderBy. Read-only. |
| appPublisher | String | The publisher of the application. Supports: $select, $OrderBy. Read-only. |
| appVersion | String | The version of the application. The possible values are: 1.0.0.1, 75.65.23.9. Supports: $select, $OrderBy. Read-only. |
| deviceId | String | The Intune device id of the device. Supports: $select, $OrderBy. Read-only. |
| deviceDisplayName | String | The name of the device. Supports: $select, $OrderBy. Read-only. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsAppHealthDevicePerformanceDetails",
  "id": "String (identifier)",
  "eventDateTime": "String (timestamp)",
  "eventType": "String",
  "appDisplayName": "String",
  "appPublisher": "String",
  "appVersion": "String",
  "deviceId": "String",
  "deviceDisplayName": "String"
}
```
