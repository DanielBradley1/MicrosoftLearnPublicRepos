<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownerdeviceconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# aospDeviceOwnerDeviceConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This topic provides descriptions of the declared methods, properties and relationships exposed by the AndroidDeviceOwnerAOSPDeviceConfiguration resource.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List aospDeviceOwnerDeviceConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-aospdeviceownerdeviceconfiguration-list?view=graph-rest-beta) | [aospDeviceOwnerDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownerdeviceconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [aospDeviceOwnerDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownerdeviceconfiguration?view=graph-rest-beta) objects. |
| [Get aospDeviceOwnerDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-aospdeviceownerdeviceconfiguration-get?view=graph-rest-beta) | [aospDeviceOwnerDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownerdeviceconfiguration?view=graph-rest-beta) | Read properties and relationships of the [aospDeviceOwnerDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownerdeviceconfiguration?view=graph-rest-beta) object. |
| [Create aospDeviceOwnerDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-aospdeviceownerdeviceconfiguration-create?view=graph-rest-beta) | [aospDeviceOwnerDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownerdeviceconfiguration?view=graph-rest-beta) | Create a new [aospDeviceOwnerDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownerdeviceconfiguration?view=graph-rest-beta) object. |
| [Delete aospDeviceOwnerDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-aospdeviceownerdeviceconfiguration-delete?view=graph-rest-beta) | None | Deletes a [aospDeviceOwnerDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownerdeviceconfiguration?view=graph-rest-beta). |
| [Update aospDeviceOwnerDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-aospdeviceownerdeviceconfiguration-update?view=graph-rest-beta) | [aospDeviceOwnerDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownerdeviceconfiguration?view=graph-rest-beta) | Update the properties of a [aospDeviceOwnerDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownerdeviceconfiguration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| supportsScopeTags | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceManagementApplicabilityRuleOsEdition | [deviceManagementApplicabilityRuleOsEdition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementapplicabilityruleosedition?view=graph-rest-beta) | The OS edition applicability for this Policy. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceManagementApplicabilityRuleOsVersion | [deviceManagementApplicabilityRuleOsVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementapplicabilityruleosversion?view=graph-rest-beta) | The OS version applicability rule for this Policy. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceManagementApplicabilityRuleDeviceMode | [deviceManagementApplicabilityRuleDeviceMode](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementapplicabilityruledevicemode?view=graph-rest-beta) | The device mode applicability rule for this Policy. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| appsBlockInstallFromUnknownSources | Boolean | Indicates whether or not the user is allowed to enable unknown sources setting. When set to true, user is not allowed to enable unknown sources settings. |
| bluetoothBlocked | Boolean | Indicates whether or not to disable the use of bluetooth. When set to true, bluetooth cannot be enabled on the device. |
| bluetoothBlockConfiguration | Boolean | Indicates whether or not to block a user from configuring bluetooth. |
| cameraBlocked | Boolean | Indicates whether or not to disable the use of the camera. |
| factoryResetBlocked | Boolean | Indicates whether or not the factory reset option in settings is disabled. |
| passwordMinimumLength | Int32 | Indicates the minimum length of the password required on the device. Valid values 4 to 16 |
| passwordMinutesOfInactivityBeforeScreenTimeout | Int32 | Minutes of inactivity before the screen times out. |
| passwordRequiredType | [androidDeviceOwnerRequiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownerrequiredpasswordtype?view=graph-rest-beta) | Indicates the minimum password quality required on the device. Possible values are: `deviceDefault`, `required`, `numeric`, `numericComplex`, `alphabetic`, `alphanumeric`, `alphanumericWithSymbols`, `lowSecurityBiometric`, `customPassword`. |
| passwordSignInFailureCountBeforeFactoryReset | Int32 | Indicates the number of times a user can enter an incorrect password before the device is wiped. Valid values 4 to 11 |
| screenCaptureBlocked | Boolean | Indicates whether or not to disable the capability to take screenshots. |
| securityAllowDebuggingFeatures | Boolean | Indicates whether or not to block the user from enabling debugging features on the device. |
| storageBlockExternalMedia | Boolean | Indicates whether or not to block external media. |
| storageBlockUsbFileTransfer | Boolean | Indicates whether or not to block USB file transfer. |
| wifiBlockEditConfigurations | Boolean | Indicates whether or not to block the user from editing the wifi connection settings. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| groupAssignments | [deviceConfigurationGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationgroupassignment?view=graph-rest-beta) collection | The list of group assignments for the device configuration profile. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| assignments | [deviceConfigurationAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationassignment?view=graph-rest-beta) collection | The list of assignments for the device configuration profile. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceStatuses | [deviceConfigurationDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdevicestatus?view=graph-rest-beta) collection | Device configuration installation status by device. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| userStatuses | [deviceConfigurationUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuserstatus?view=graph-rest-beta) collection | Device configuration installation status by user. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceStatusOverview | [deviceConfigurationDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationdeviceoverview?view=graph-rest-beta) | Device Configuration devices status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| userStatusOverview | [deviceConfigurationUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationuseroverview?view=graph-rest-beta) | Device Configuration users status overview Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceSettingStateSummaries | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-beta) collection | Device Configuration Setting State Device Summary Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.aospDeviceOwnerDeviceConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
  "supportsScopeTags": true,
  "deviceManagementApplicabilityRuleOsEdition": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsEdition",
    "osEditionTypes": [
      "String"
    ],
    "name": "String",
    "ruleType": "String"
  },
  "deviceManagementApplicabilityRuleOsVersion": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsVersion",
    "minOSVersion": "String",
    "maxOSVersion": "String",
    "name": "String",
    "ruleType": "String"
  },
  "deviceManagementApplicabilityRuleDeviceMode": {
    "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleDeviceMode",
    "deviceMode": "String",
    "name": "String",
    "ruleType": "String"
  },
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
  "appsBlockInstallFromUnknownSources": true,
  "bluetoothBlocked": true,
  "bluetoothBlockConfiguration": true,
  "cameraBlocked": true,
  "factoryResetBlocked": true,
  "passwordMinimumLength": 1024,
  "passwordMinutesOfInactivityBeforeScreenTimeout": 1024,
  "passwordRequiredType": "String",
  "passwordSignInFailureCountBeforeFactoryReset": 1024,
  "screenCaptureBlocked": true,
  "securityAllowDebuggingFeatures": true,
  "storageBlockExternalMedia": true,
  "storageBlockUsbFileTransfer": true,
  "wifiBlockEditConfigurations": true
}
```
