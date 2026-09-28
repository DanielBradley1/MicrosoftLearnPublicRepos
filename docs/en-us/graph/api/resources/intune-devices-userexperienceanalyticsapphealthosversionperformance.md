<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthosversionperformance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsAppHealthOSVersionPerformance resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics device OS version performance entity contains OS version performance details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsAppHealthOSVersionPerformances](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthosversionperformance-list?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthOSVersionPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthosversionperformance?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsAppHealthOSVersionPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthosversionperformance?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsAppHealthOSVersionPerformance](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsapphealthosversionperformance-get?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthOSVersionPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthosversionperformance?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsAppHealthOSVersionPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthosversionperformance?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsAppHealthOSVersionPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthosversionperformance-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthOSVersionPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthosversionperformance?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsAppHealthOSVersionPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthosversionperformance?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsAppHealthOSVersionPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthosversionperformance-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsAppHealthOSVersionPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthosversionperformance?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsAppHealthOSVersionPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsapphealthosversionperformance-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsAppHealthOSVersionPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthosversionperformance?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsAppHealthOSVersionPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsapphealthosversionperformance?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics OS version performance object. Supports: $select, $OrderBy. Read-only. |
| osVersion | String | The OS version installed on the device. Supports: $select, $OrderBy. Read-only. |
| osBuildNumber | String | The OS build number installed on the device. Supports: $select, $OrderBy. Read-only. |
| activeDeviceCount | Int32 | The number of active devices for the OS version. Valid values 0 to 2147483647. Supports: $filter, $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
| meanTimeToFailureInMinutes | Int32 | The mean time to failure for the application in minutes. Valid values 0 to 2147483647. Supports: $filter, $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
| osVersionAppHealthScore | Double | The application health score of the OS version. Valid values 0 to 100. Supports: $filter, $select, $OrderBy. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| osVersionAppHealthStatus | String | The overall app health status of the OS version. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsAppHealthOSVersionPerformance",
  "id": "String (identifier)",
  "osVersion": "String",
  "osBuildNumber": "String",
  "activeDeviceCount": 1024,
  "meanTimeToFailureInMinutes": 1024,
  "osVersionAppHealthScore": "4.2",
  "osVersionAppHealthStatus": "String"
}
```
