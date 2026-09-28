<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sharedpcconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# sharedPCConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This topic provides descriptions of the declared methods, properties and relationships exposed by the sharedPCConfiguration resource.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List sharedPCConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-sharedpcconfiguration-list?view=graph-rest-1.0) | [sharedPCConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sharedpcconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [sharedPCConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sharedpcconfiguration?view=graph-rest-1.0) objects. |
| [Get sharedPCConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-sharedpcconfiguration-get?view=graph-rest-1.0) | [sharedPCConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sharedpcconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [sharedPCConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sharedpcconfiguration?view=graph-rest-1.0) object. |
| [Create sharedPCConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-sharedpcconfiguration-create?view=graph-rest-1.0) | [sharedPCConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sharedpcconfiguration?view=graph-rest-1.0) | Create a new [sharedPCConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sharedpcconfiguration?view=graph-rest-1.0) object. |
| [Delete sharedPCConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-sharedpcconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [sharedPCConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sharedpcconfiguration?view=graph-rest-1.0). |
| [Update sharedPCConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-sharedpcconfiguration-update?view=graph-rest-1.0) | [sharedPCConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sharedpcconfiguration?view=graph-rest-1.0) | Update the properties of a [sharedPCConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sharedpcconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| accountManagerPolicy | [sharedPCAccountManagerPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sharedpcaccountmanagerpolicy?view=graph-rest-1.0) | Specifies how accounts are managed on a shared PC. Only applies when disableAccountManager is false. |
| allowedAccounts | [sharedPCAllowedAccountType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sharedpcallowedaccounttype?view=graph-rest-1.0) | Indicates which type of accounts are allowed to use on a shared PC. The possible values are: `guest`, `domain`. |
| allowLocalStorage | Boolean | Specifies whether local storage is allowed on a shared PC. |
| disableAccountManager | Boolean | Disables the account manager for shared PC mode. |
| disableEduPolicies | Boolean | Specifies whether the default shared PC education environment policies should be disabled. For Windows 10 RS2 and later, this policy will be applied without setting Enabled to true. |
| disablePowerPolicies | Boolean | Specifies whether the default shared PC power policies should be disabled. |
| disableSignInOnResume | Boolean | Disables the requirement to sign in whenever the device wakes up from sleep mode. |
| enabled | Boolean | Enables shared PC mode and applies the shared pc policies. |
| idleTimeBeforeSleepInSeconds | Int32 | Specifies the time in seconds that a device must sit idle before the PC goes to sleep. Setting this value to 0 prevents the sleep timeout from occurring. |
| kioskAppDisplayName | String | Specifies the display text for the account shown on the sign-in screen which launches the app specified by SetKioskAppUserModelId. Only applies when KioskAppUserModelId is set. |
| kioskAppUserModelId | String | Specifies the application user model ID of the app to use with assigned access. |
| maintenanceStartTime | TimeOfDay | Specifies the daily start time of maintenance hour. |

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
  "@odata.type": "#microsoft.graph.sharedPCConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
  "accountManagerPolicy": {
    "@odata.type": "microsoft.graph.sharedPCAccountManagerPolicy",
    "accountDeletionPolicy": "String",
    "cacheAccountsAboveDiskFreePercentage": 1024,
    "inactiveThresholdDays": 1024,
    "removeAccountsBelowDiskFreePercentage": 1024
  },
  "allowedAccounts": "String",
  "allowLocalStorage": true,
  "disableAccountManager": true,
  "disableEduPolicies": true,
  "disablePowerPolicies": true,
  "disableSignInOnResume": true,
  "enabled": true,
  "idleTimeBeforeSleepInSeconds": 1024,
  "kioskAppDisplayName": "String",
  "kioskAppUserModelId": "String",
  "maintenanceStartTime": "String (time of day)"
}
```
