<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocessperformance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# userExperienceAnalyticsDeviceStartupProcessPerformance resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics device startup process performance.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsDeviceStartupProcessPerformances](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsdevicestartupprocessperformance-list?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceStartupProcessPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocessperformance?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsDeviceStartupProcessPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocessperformance?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsDeviceStartupProcessPerformance](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsdevicestartupprocessperformance-get?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceStartupProcessPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocessperformance?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsDeviceStartupProcessPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocessperformance?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsDeviceStartupProcessPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicestartupprocessperformance-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceStartupProcessPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocessperformance?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsDeviceStartupProcessPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocessperformance?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsDeviceStartupProcessPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicestartupprocessperformance-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsDeviceStartupProcessPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocessperformance?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsDeviceStartupProcessPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicestartupprocessperformance-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceStartupProcessPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocessperformance?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsDeviceStartupProcessPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocessperformance?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics device startup process performance. Supports: $select, $OrderBy. Read-only. |
| processName | String | The name of the startup process. Examples: outlook, excel. Supports: $select, $OrderBy. Read-only. |
| productName | String | The product name of the startup process. Examples: Microsoft Outlook, Microsoft Excel. Supports: $select, $OrderBy. Read-only. |
| publisher | String | The publisher of the startup process. Examples: Microsoft Corporation, Contoso Corp. Supports: $select, $OrderBy. Read-only. |
| deviceCount | Int64 | The count of devices which initiated this process on startup. Supports: $filter, $select, $OrderBy. Read-only. |
| medianImpactInMs | Int64 | The median impact of startup process on device boot time in milliseconds. Supports: $filter, $select, $OrderBy. Read-only. |
| totalImpactInMs | Int64 | The total impact of startup process on device boot time in milliseconds. Supports: $filter, $select, $OrderBy. Read-only. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsDeviceStartupProcessPerformance",
  "id": "String (identifier)",
  "processName": "String",
  "productName": "String",
  "publisher": "String",
  "deviceCount": 1024,
  "medianImpactInMs": 1024,
  "totalImpactInMs": 1024
}
```
