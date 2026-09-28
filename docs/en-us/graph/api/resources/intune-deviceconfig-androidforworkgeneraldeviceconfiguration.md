<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkgeneraldeviceconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-12 -->

# androidForWorkGeneralDeviceConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Android For Work general device configuration.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List androidForWorkGeneralDeviceConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidforworkgeneraldeviceconfiguration-list?view=graph-rest-beta) | [androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkgeneraldeviceconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkgeneraldeviceconfiguration?view=graph-rest-beta) objects. |
| [Get androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidforworkgeneraldeviceconfiguration-get?view=graph-rest-beta) | [androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkgeneraldeviceconfiguration?view=graph-rest-beta) | Read properties and relationships of the [androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkgeneraldeviceconfiguration?view=graph-rest-beta) object. |
| [Create androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidforworkgeneraldeviceconfiguration-create?view=graph-rest-beta) | [androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkgeneraldeviceconfiguration?view=graph-rest-beta) | Create a new [androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkgeneraldeviceconfiguration?view=graph-rest-beta) object. |
| [Delete androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidforworkgeneraldeviceconfiguration-delete?view=graph-rest-beta) | None | Deletes a [androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkgeneraldeviceconfiguration?view=graph-rest-beta). |
| [Update androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidforworkgeneraldeviceconfiguration-update?view=graph-rest-beta) | [androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkgeneraldeviceconfiguration?view=graph-rest-beta) | Update the properties of a [androidForWorkGeneralDeviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkgeneraldeviceconfiguration?view=graph-rest-beta) object. |

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
| passwordBlockFaceUnlock | Boolean | Indicates whether or not to block face unlock. |
| passwordBlockFingerprintUnlock | Boolean | Indicates whether or not to block fingerprint unlock. |
| passwordBlockIrisUnlock | Boolean | Indicates whether or not to block iris unlock. |
| passwordBlockTrustAgents | Boolean | Indicates whether or not to block Smart Lock and other trust agents. |
| passwordExpirationDays | Int32 | Number of days before the password expires. Valid values 1 to 365 |
| passwordMinimumLength | Int32 | Minimum length of passwords. Valid values 4 to 16 |
| passwordMinutesOfInactivityBeforeScreenTimeout | Int32 | Minutes of inactivity before the screen times out. |
| passwordPreviousPasswordBlockCount | Int32 | Number of previous passwords to block. Valid values 0 to 24 |
| passwordSignInFailureCountBeforeFactoryReset | Int32 | Number of sign in failures allowed before factory reset. Valid values 1 to 16 |
| passwordRequiredType | [androidForWorkRequiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkrequiredpasswordtype?view=graph-rest-beta) | Type of password that is required. Possible values are: `deviceDefault`, `lowSecurityBiometric`, `required`, `atLeastNumeric`, `numericComplex`, `atLeastAlphabetic`, `atLeastAlphanumeric`, `alphanumericWithSymbols`. |
| requiredPasswordComplexity | [androidRequiredPasswordComplexity](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidrequiredpasswordcomplexity?view=graph-rest-beta) | Indicates the required device password complexity on Android. One of: NONE, LOW, MEDIUM, HIGH. This is a new API targeted to Android 12+. Possible values are: `none`, `low`, `medium`, `high`. |
| workProfileDataSharingType | [androidForWorkCrossProfileDataSharingType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkcrossprofiledatasharingtype?view=graph-rest-beta) | Type of data sharing that is allowed. Possible values are: `deviceDefault`, `preventAny`, `allowPersonalToWork`, `noRestrictions`. |
| workProfileBlockNotificationsWhileDeviceLocked | Boolean | Indicates whether or not to block notifications while device locked. |
| workProfileBlockAddingAccounts | Boolean | Block users from adding/removing accounts in work profile. |
| workProfileBluetoothEnableContactSharing | Boolean | Allow bluetooth devices to access enterprise contacts. |
| workProfileBlockScreenCapture | Boolean | Block screen capture in work profile. |
| workProfileBlockCrossProfileCallerId | Boolean | Block display work profile caller ID in personal profile. |
| workProfileBlockCamera | Boolean | Block work profile camera. |
| workProfileBlockCrossProfileContactsSearch | Boolean | Block work profile contacts availability in personal profile. |
| workProfileBlockCrossProfileCopyPaste | Boolean | Boolean that indicates if the setting disallow cross profile copy/paste is enabled. |
| workProfileDefaultAppPermissionPolicy | [androidForWorkDefaultAppPermissionPolicyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkdefaultapppermissionpolicytype?view=graph-rest-beta) | Type of password that is required. Possible values are: `deviceDefault`, `prompt`, `autoGrant`, `autoDeny`. |
| workProfilePasswordBlockFaceUnlock | Boolean | Indicates whether or not to block face unlock for work profile. |
| workProfilePasswordBlockFingerprintUnlock | Boolean | Indicates whether or not to block fingerprint unlock for work profile. |
| workProfilePasswordBlockIrisUnlock | Boolean | Indicates whether or not to block iris unlock for work profile. |
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
| workProfilePasswordRequiredType | [androidForWorkRequiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidforworkrequiredpasswordtype?view=graph-rest-beta) | Type of work profile password that is required. Possible values are: `deviceDefault`, `lowSecurityBiometric`, `required`, `atLeastNumeric`, `numericComplex`, `atLeastAlphabetic`, `atLeastAlphanumeric`, `alphanumericWithSymbols`. |
| workProfileRequiredPasswordComplexity | [androidRequiredPasswordComplexity](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidrequiredpasswordcomplexity?view=graph-rest-beta) | Indicates the required work profile password complexity on Android. One of: NONE, LOW, MEDIUM, HIGH. This is a new API targeted to Android 12+. Possible values are: `none`, `low`, `medium`, `high`. |
| workProfileRequirePassword | Boolean | Password is required or not for work profile |
| securityRequireVerifyApps | Boolean | Require the Android Verify apps feature is turned on. |
| vpnAlwaysOnPackageIdentifier | String | Enable lockdown mode for always-on VPN. |
| vpnEnableAlwaysOnLockdownMode | Boolean | Enable lockdown mode for always-on VPN. |
| workProfileAllowWidgets | Boolean | Allow widgets from work profile apps. |
| workProfileBlockPersonalAppInstallsFromUnknownSources | Boolean | Prevent app installations from unknown sources in the personal profile. |
| workProfileAccountUse | [androidWorkProfileAccountUse](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidworkprofileaccountuse?view=graph-rest-beta) | Control user's ability to add accounts in work profile including Google accounts. Possible values are: `allowAllExceptGoogleAccounts`, `blockAll`, `allowAll`, `unknownFutureValue`. |
| allowedGoogleAccountDomains | String collection | Determine domains allow-list for accounts that can be added to work profile. |
| blockUnifiedPasswordForWorkProfile | Boolean | Prevent using unified password for unlocking device and work profile. |

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
  "@odata.type": "#microsoft.graph.androidForWorkGeneralDeviceConfiguration",
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
  "passwordBlockFaceUnlock": true,
  "passwordBlockFingerprintUnlock": true,
  "passwordBlockIrisUnlock": true,
  "passwordBlockTrustAgents": true,
  "passwordExpirationDays": 1024,
  "passwordMinimumLength": 1024,
  "passwordMinutesOfInactivityBeforeScreenTimeout": 1024,
  "passwordPreviousPasswordBlockCount": 1024,
  "passwordSignInFailureCountBeforeFactoryReset": 1024,
  "passwordRequiredType": "String",
  "requiredPasswordComplexity": "String",
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
  "workProfilePasswordBlockFaceUnlock": true,
  "workProfilePasswordBlockFingerprintUnlock": true,
  "workProfilePasswordBlockIrisUnlock": true,
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
  "workProfileRequiredPasswordComplexity": "String",
  "workProfileRequirePassword": true,
  "securityRequireVerifyApps": true,
  "vpnAlwaysOnPackageIdentifier": "String",
  "vpnEnableAlwaysOnLockdownMode": true,
  "workProfileAllowWidgets": true,
  "workProfileBlockPersonalAppInstallsFromUnknownSources": true,
  "workProfileAccountUse": "String",
  "allowedGoogleAccountDomains": [
    "String"
  ],
  "blockUnifiedPasswordForWorkProfile": true
}
```
