<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-13 -->

# androidWorkProfileGeneralDeviceConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Android Work Profile general device configuration.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List androidWorkProfileGeneralDeviceConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration-list?view=graph-rest-1.0) | [androidWorkProfileGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [androidWorkProfileGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration?view=graph-rest-1.0) objects. |
| [Get androidWorkProfileGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration-get?view=graph-rest-1.0) | [androidWorkProfileGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [androidWorkProfileGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration?view=graph-rest-1.0) object. |
| [Create androidWorkProfileGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration-create?view=graph-rest-1.0) | [androidWorkProfileGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration?view=graph-rest-1.0) | Create a new [androidWorkProfileGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration?view=graph-rest-1.0) object. |
| [Delete androidWorkProfileGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [androidWorkProfileGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration?view=graph-rest-1.0). |
| [Update androidWorkProfileGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration-update?view=graph-rest-1.0) | [androidWorkProfileGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration?view=graph-rest-1.0) | Update the properties of a [androidWorkProfileGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilegeneraldeviceconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| passwordBlockFingerprintUnlock | Boolean | Indicates whether or not to block fingerprint unlock. |
| passwordBlockTrustAgents | Boolean | Indicates whether or not to block Smart Lock and other trust agents. |
| passwordExpirationDays | Int32 | Number of days before the password expires. Valid values 1 to 365 |
| passwordMinimumLength | Int32 | Minimum length of passwords. Valid values 4 to 16 |
| passwordMinutesOfInactivityBeforeScreenTimeout | Int32 | Minutes of inactivity before the screen times out. |
| passwordPreviousPasswordBlockCount | Int32 | Number of previous passwords to block. Valid values 0 to 24 |
| passwordSignInFailureCountBeforeFactoryReset | Int32 | Number of sign in failures allowed before factory reset. Valid values 1 to 16 |
| passwordRequiredType | [androidWorkProfileRequiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilerequiredpasswordtype?view=graph-rest-1.0) | Type of password that is required. The possible values are: `deviceDefault`, `lowSecurityBiometric`, `required`, `atLeastNumeric`, `numericComplex`, `atLeastAlphabetic`, `atLeastAlphanumeric`, `alphanumericWithSymbols`. |
| workProfileDataSharingType | [androidWorkProfileCrossProfileDataSharingType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilecrossprofiledatasharingtype?view=graph-rest-1.0) | Type of data sharing that is allowed. The possible values are: `deviceDefault`, `preventAny`, `allowPersonalToWork`, `noRestrictions`. |
| workProfileBlockNotificationsWhileDeviceLocked | Boolean | Indicates whether or not to block notifications while device locked. |
| workProfileBlockAddingAccounts | Boolean | Block users from adding/removing accounts in work profile. |
| workProfileBluetoothEnableContactSharing | Boolean | Allow bluetooth devices to access enterprise contacts. |
| workProfileBlockScreenCapture | Boolean | Block screen capture in work profile. |
| workProfileBlockCrossProfileCallerId | Boolean | Block display work profile caller ID in personal profile. |
| workProfileBlockCamera | Boolean | Block work profile camera. |
| workProfileBlockCrossProfileContactsSearch | Boolean | Block work profile contacts availability in personal profile. |
| workProfileBlockCrossProfileCopyPaste | Boolean | Boolean that indicates if the setting disallow cross profile copy/paste is enabled. |
| workProfileDefaultAppPermissionPolicy | [androidWorkProfileDefaultAppPermissionPolicyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofiledefaultapppermissionpolicytype?view=graph-rest-1.0) | Type of password that is required. The possible values are: `deviceDefault`, `prompt`, `autoGrant`, `autoDeny`. |
| workProfilePasswordBlockFingerprintUnlock | Boolean | Indicates whether or not to block fingerprint unlock for work profile. |
| workProfilePasswordBlockTrustAgents | Boolean | Indicates whether or not to block Smart Lock and other trust agents for work profile. |
| workProfilePasswordExpirationDays | Int32 | Number of days before the work profile password expires. Valid values 1 to 365 |
| workProfilePasswordMinimumLength | Int32 | Minimum length of work profile password. Valid values 4 to 16 |
| workProfilePasswordMinNumericCharacters | Int32 | Minimum # of numeric characters required in work profile password. Valid values 1 to 10 |
| workProfilePasswordMinNonLetterCharacters | Int32 | Minimum # of non-letter characters required in work profile password. Valid values 1 to 10 |
| workProfilePasswordMinLetterCharacters | Int32 | Minimum # of letter characters required in work profile password. Valid values 1 to 10 |
| workProfilePasswordMinLowerCaseCharacters | Int32 | Minimum # of lower-case characters required in work profile password. Valid values 1 to 10 |
| workProfilePasswordMinUpperCaseCharacters | Int32 | Minimum # of upper-case characters required in work profile password. Valid values 1 to 10 |
| workProfilePasswordMinSymbolCharacters | Int32 | Minimum # of symbols required in work profile password. Valid values 1 to 10 |
| workProfilePasswordMinutesOfInactivityBeforeScreenTimeout | Int32 | Minutes of inactivity before the screen times out. |
| workProfilePasswordPreviousPasswordBlockCount | Int32 | Number of previous work profile passwords to block. Valid values 0 to 24 |
| workProfilePasswordSignInFailureCountBeforeFactoryReset | Int32 | Number of sign in failures allowed before work profile is removed and all corporate data deleted. Valid values 1 to 16 |
| workProfilePasswordRequiredType | [androidWorkProfileRequiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofilerequiredpasswordtype?view=graph-rest-1.0) | Type of work profile password that is required. The possible values are: `deviceDefault`, `lowSecurityBiometric`, `required`, `atLeastNumeric`, `numericComplex`, `atLeastAlphabetic`, `atLeastAlphanumeric`, `alphanumericWithSymbols`. |
| workProfileRequirePassword | Boolean | Password is required or not for work profile |
| securityRequireVerifyApps | Boolean | Require the Android Verify apps feature is turned on. |

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
  "@odata.type": "#microsoft.graph.androidWorkProfileGeneralDeviceConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
  "passwordBlockFingerprintUnlock": true,
  "passwordBlockTrustAgents": true,
  "passwordExpirationDays": 1024,
  "passwordMinimumLength": 1024,
  "passwordMinutesOfInactivityBeforeScreenTimeout": 1024,
  "passwordPreviousPasswordBlockCount": 1024,
  "passwordSignInFailureCountBeforeFactoryReset": 1024,
  "passwordRequiredType": "String",
  "workProfileDataSharingType": "String",
  "workProfileBlockNotificationsWhileDeviceLocked": true,
  "workProfileBlockAddingAccounts": true,
  "workProfileBluetoothEnableContactSharing": true,
  "workProfileBlockScreenCapture": true,
  "workProfileBlockCrossProfileCallerId": true,
  "workProfileBlockCamera": true,
  "workProfileBlockCrossProfileContactsSearch": true,
  "workProfileBlockCrossProfileCopyPaste": true,
  "workProfileDefaultAppPermissionPolicy": "String",
  "workProfilePasswordBlockFingerprintUnlock": true,
  "workProfilePasswordBlockTrustAgents": true,
  "workProfilePasswordExpirationDays": 1024,
  "workProfilePasswordMinimumLength": 1024,
  "workProfilePasswordMinNumericCharacters": 1024,
  "workProfilePasswordMinNonLetterCharacters": 1024,
  "workProfilePasswordMinLetterCharacters": 1024,
  "workProfilePasswordMinLowerCaseCharacters": 1024,
  "workProfilePasswordMinUpperCaseCharacters": 1024,
  "workProfilePasswordMinSymbolCharacters": 1024,
  "workProfilePasswordMinutesOfInactivityBeforeScreenTimeout": 1024,
  "workProfilePasswordPreviousPasswordBlockCount": 1024,
  "workProfilePasswordSignInFailureCountBeforeFactoryReset": 1024,
  "workProfilePasswordRequiredType": "String",
  "workProfileRequirePassword": true,
  "securityRequireVerifyApps": true
}
```
