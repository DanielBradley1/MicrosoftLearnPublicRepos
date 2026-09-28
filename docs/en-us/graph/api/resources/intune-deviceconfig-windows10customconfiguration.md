<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10customconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windows10CustomConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This topic provides descriptions of the declared methods, properties and relationships exposed by the windows10CustomConfiguration resource.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windows10CustomConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10customconfiguration-list?view=graph-rest-1.0) | [windows10CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10customconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [windows10CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10customconfiguration?view=graph-rest-1.0) objects. |
| [Get windows10CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10customconfiguration-get?view=graph-rest-1.0) | [windows10CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10customconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [windows10CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10customconfiguration?view=graph-rest-1.0) object. |
| [Create windows10CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10customconfiguration-create?view=graph-rest-1.0) | [windows10CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10customconfiguration?view=graph-rest-1.0) | Create a new [windows10CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10customconfiguration?view=graph-rest-1.0) object. |
| [Delete windows10CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10customconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [windows10CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10customconfiguration?view=graph-rest-1.0). |
| [Update windows10CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10customconfiguration-update?view=graph-rest-1.0) | [windows10CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10customconfiguration?view=graph-rest-1.0) | Update the properties of a [windows10CustomConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10customconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| omaSettings | [omaSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-omasetting?view=graph-rest-1.0) collection | OMA settings. This collection can contain a maximum of 1000 elements. |

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
  "@odata.type": "#microsoft.graph.windows10CustomConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
  "omaSettings": [
    {
      "@odata.type": "microsoft.graph.omaSetting",
      "displayName": "String",
      "description": "String",
      "omaUri": "String"
    }
  ]
}
```
