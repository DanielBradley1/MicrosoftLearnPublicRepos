<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocess?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsDeviceStartupProcess resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics device startup process details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsDeviceStartupProcesses](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsdevicestartupprocess-list?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceStartupProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocess?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsDeviceStartupProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocess?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsDeviceStartupProcess](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsdevicestartupprocess-get?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceStartupProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocess?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsDeviceStartupProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocess?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsDeviceStartupProcess](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicestartupprocess-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceStartupProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocess?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsDeviceStartupProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocess?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsDeviceStartupProcess](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicestartupprocess-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsDeviceStartupProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocess?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsDeviceStartupProcess](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicestartupprocess-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceStartupProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocess?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsDeviceStartupProcess](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartupprocess?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics device startup process. Supports: $select, $OrderBy. Read-only. |
| managedDeviceId | String | The Intune device id of the device. Supports: $select, $OrderBy. Read-only. |
| processName | String | The name of the process. Examples: outlook, excel. Supports: $select, $OrderBy. Read-only. |
| productName | String | The product name of the process. Examples: Microsoft Outlook, Microsoft Excel. Supports: $select, $OrderBy. Read-only. |
| publisher | String | The publisher of the process. Examples: Microsoft Corporation, Contoso Corp. Supports: $select, $OrderBy. Read-only. |
| startupImpactInMs | Int32 | The impact of startup process on device boot time in milliseconds. Supports: $select, $OrderBy. Read-only. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsDeviceStartupProcess",
  "id": "String (identifier)",
  "managedDeviceId": "String",
  "processName": "String",
  "productName": "String",
  "publisher": "String",
  "startupImpactInMs": 1024
}
```
