<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdateconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-13 -->

# iosUpdateConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

IOS Update Configuration, allows you to configure time window within week to install iOS updates

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosUpdateConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosupdateconfiguration-list?view=graph-rest-1.0) | [iosUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdateconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [iosUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdateconfiguration?view=graph-rest-1.0) objects. |
| [Get iosUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosupdateconfiguration-get?view=graph-rest-1.0) | [iosUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdateconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [iosUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdateconfiguration?view=graph-rest-1.0) object. |
| [Create iosUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosupdateconfiguration-create?view=graph-rest-1.0) | [iosUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdateconfiguration?view=graph-rest-1.0) | Create a new [iosUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdateconfiguration?view=graph-rest-1.0) object. |
| [Delete iosUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosupdateconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [iosUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdateconfiguration?view=graph-rest-1.0). |
| [Update iosUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-iosupdateconfiguration-update?view=graph-rest-1.0) | [iosUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdateconfiguration?view=graph-rest-1.0) | Update the properties of a [iosUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosupdateconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| activeHoursStart | TimeOfDay | Active Hours Start \(active hours mean the time window when updates install should not happen\) |
| activeHoursEnd | TimeOfDay | Active Hours End \(active hours mean the time window when updates install should not happen\) |
| scheduledInstallDays | [dayOfWeek](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-dayofweek?view=graph-rest-1.0) collection | Days in week for which active hours are configured. This collection can contain a maximum of 7 elements. |
| utcTimeOffsetInMinutes | Int32 | UTC Time Offset indicated in minutes |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-1.0) collection | The list of assignments for the device configuration profile. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| deviceStatuses | [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-1.0) collection | Device configuration installation status by device. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| userStatuses | [deviceConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatus?view=graph-rest-1.0) collection | Device configuration installation status by user. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| deviceStatusOverview | [deviceConfigurationDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdeviceoverview?view=graph-rest-1.0) | Device Configuration devices status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| userStatusOverview | [deviceConfigurationUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuseroverview?view=graph-rest-1.0) | Device Configuration users status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| deviceSettingStateSummaries | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0) collection | Device Configuration Setting State Device Summary Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosUpdateConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
  "activeHoursStart": "String (time of day)",
  "activeHoursEnd": "String (time of day)",
  "scheduledInstallDays": [
    "String"
  ],
  "utcTimeOffsetInMinutes": 1024
}
```
