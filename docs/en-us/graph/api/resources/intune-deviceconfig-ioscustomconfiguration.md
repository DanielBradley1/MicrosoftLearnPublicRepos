<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscustomconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosCustomConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This topic provides descriptions of the declared methods, properties and relationships exposed by the iosCustomConfiguration resource.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List iosCustomConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioscustomconfiguration-list?view=graph-rest-1.0) | [iosCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscustomconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [iosCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscustomconfiguration?view=graph-rest-1.0) objects. |
| [Get iosCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioscustomconfiguration-get?view=graph-rest-1.0) | [iosCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscustomconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [iosCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscustomconfiguration?view=graph-rest-1.0) object. |
| [Create iosCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioscustomconfiguration-create?view=graph-rest-1.0) | [iosCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscustomconfiguration?view=graph-rest-1.0) | Create a new [iosCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscustomconfiguration?view=graph-rest-1.0) object. |
| [Delete iosCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioscustomconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [iosCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscustomconfiguration?view=graph-rest-1.0). |
| [Update iosCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ioscustomconfiguration-update?view=graph-rest-1.0) | [iosCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscustomconfiguration?view=graph-rest-1.0) | Update the properties of a [iosCustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ioscustomconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |  |
| :--- | :--- | :--- | --- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |  |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |  |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |  |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |  |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |  |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |  |
| payloadName | String | Name that is displayed to the user. |  |
| payloadFileName | String | Payload file name \(\*.mobileconfig | \*.xml\). |
| payload | Binary | Payload. \(UTF8 encoded byte array\) |  |

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
  "@odata.type": "#microsoft.graph.iosCustomConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
  "payloadName": "String",
  "payloadFileName": "String",
  "payload": "binary"
}
```
