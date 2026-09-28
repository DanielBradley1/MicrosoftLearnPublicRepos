<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartuphistory?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsDeviceStartupHistory resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics device startup history entity contains device boot performance history details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsDeviceStartupHistories](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsdevicestartuphistory-list?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceStartupHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartuphistory?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsDeviceStartupHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartuphistory?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsDeviceStartupHistory](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsdevicestartuphistory-get?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceStartupHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartuphistory?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsDeviceStartupHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartuphistory?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsDeviceStartupHistory](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicestartuphistory-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceStartupHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartuphistory?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsDeviceStartupHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartuphistory?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsDeviceStartupHistory](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicestartuphistory-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsDeviceStartupHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartuphistory?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsDeviceStartupHistory](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsdevicestartuphistory-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsDeviceStartupHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartuphistory?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsDeviceStartupHistory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsdevicestartuphistory?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics device startup history. Supports: $select, $OrderBy. Read-only. |
| deviceId | String | The Intune device id of the device. Supports: $select, $OrderBy. Read-only. |
| startTime | DateTimeOffset | The device boot start time. The value cannot be modified and is automatically populated when the device performs a reboot. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2022 would look like this: '2022-01-01T00:00:00Z'. Returned by default. Read-only. |
| coreBootTimeInMs | Int32 | The device core boot time in milliseconds. Supports: $select, $OrderBy. Read-only. |
| groupPolicyBootTimeInMs | Int32 | The impact of device group policy client on boot time in milliseconds. Supports: $select, $OrderBy. Read-only. |
| featureUpdateBootTimeInMs | Int32 | The impact of device feature updates on boot time in milliseconds. Supports: $select, $OrderBy. Read-only. |
| totalBootTimeInMs | Int32 | The device total boot time in milliseconds. Supports: $select, $OrderBy. Read-only. |
| groupPolicyLoginTimeInMs | Int32 | The impact of device group policy client on login time in milliseconds. Supports: $select, $OrderBy. Read-only. |
| coreLoginTimeInMs | Int32 | The device core login time in milliseconds. Supports: $select, $OrderBy. Read-only. |
| responsiveDesktopTimeInMs | Int32 | The time for desktop to become responsive during login process in milliseconds. Supports: $select, $OrderBy. Read-only. |
| totalLoginTimeInMs | Int32 | The device total login time in milliseconds. Supports: $select, $OrderBy. Read-only. |
| isFirstLogin | Boolean | When TRUE, indicates the device login is the first login after a reboot. When FALSE, indicates the device login is not the first login after a reboot. Supports: $select, $OrderBy. Read-only. |
| isFeatureUpdate | Boolean | When TRUE, indicates the device boot record is associated with feature updates. When FALSE, indicates the device boot record is not associated with feature updates. Supports: $select, $OrderBy. Read-only. |
| operatingSystemVersion | String | The user experience analytics device boot record's operating system version. Supports: $select, $OrderBy. Read-only. |
| restartCategory | [userExperienceAnalyticsOperatingSystemRestartCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsoperatingsystemrestartcategory?view=graph-rest-1.0) | OS restart category. The possible values are: unknown, restartWithUpdate, restartWithoutUpdate, blueScreen, shutdownWithUpdate, shutdownWithoutUpdate, longPowerButtonPress, bootError, update. Unknown by default. Supports: $select, $OrderBy. Read-only. The possible values are: `unknown`, `restartWithUpdate`, `restartWithoutUpdate`, `blueScreen`, `shutdownWithUpdate`, `shutdownWithoutUpdate`, `longPowerButtonPress`, `bootError`, `update`, `unknownFutureValue`. |
| restartStopCode | String | OS restart stop code. This shows the bug check code which can be used to look up the blue screen reason. Supports: $select, $OrderBy. Read-only. |
| restartFaultBucket | String | OS restart fault bucket. The fault bucket is used to find additional information about a system crash. Supports: $select, $OrderBy. Read-only. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsDeviceStartupHistory",
  "id": "String (identifier)",
  "deviceId": "String",
  "startTime": "String (timestamp)",
  "coreBootTimeInMs": 1024,
  "groupPolicyBootTimeInMs": 1024,
  "featureUpdateBootTimeInMs": 1024,
  "totalBootTimeInMs": 1024,
  "groupPolicyLoginTimeInMs": 1024,
  "coreLoginTimeInMs": 1024,
  "responsiveDesktopTimeInMs": 1024,
  "totalLoginTimeInMs": 1024,
  "isFirstLogin": true,
  "isFeatureUpdate": true,
  "operatingSystemVersion": "String",
  "restartCategory": "String",
  "restartStopCode": "String",
  "restartFaultBucket": "String"
}
```
