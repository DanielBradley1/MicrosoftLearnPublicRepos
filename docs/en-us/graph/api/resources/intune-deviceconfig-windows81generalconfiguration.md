<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windows81GeneralConfiguration resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This topic provides descriptions of the declared methods, properties and relationships exposed by the windows81GeneralConfiguration resource.

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windows81GeneralConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows81generalconfiguration-list?view=graph-rest-1.0) | [windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration?view=graph-rest-1.0) collection | List properties and relationships of the [windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration?view=graph-rest-1.0) objects. |
| [Get windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows81generalconfiguration-get?view=graph-rest-1.0) | [windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration?view=graph-rest-1.0) | Read properties and relationships of the [windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration?view=graph-rest-1.0) object. |
| [Create windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows81generalconfiguration-create?view=graph-rest-1.0) | [windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration?view=graph-rest-1.0) | Create a new [windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration?view=graph-rest-1.0) object. |
| [Delete windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows81generalconfiguration-delete?view=graph-rest-1.0) | None | Deletes a [windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration?view=graph-rest-1.0). |
| [Update windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows81generalconfiguration-update?view=graph-rest-1.0) | [windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration?view=graph-rest-1.0) | Update the properties of a [windows81GeneralConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81generalconfiguration?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfiguration?view=graph-rest-1.0) |
| accountsBlockAddingNonMicrosoftAccountEmail | Boolean | Indicates whether or not to Block the user from adding email accounts to the device that are not associated with a Microsoft account. |
| applyOnlyToWindows81 | Boolean | Value indicating whether this policy only applies to Windows 8.1. This property is read-only. |
| browserBlockAutofill | Boolean | Indicates whether or not to block auto fill. |
| browserBlockAutomaticDetectionOfIntranetSites | Boolean | Indicates whether or not to block automatic detection of Intranet sites. |
| browserBlockEnterpriseModeAccess | Boolean | Indicates whether or not to block enterprise mode access. |
| browserBlockJavaScript | Boolean | Indicates whether or not to Block the user from using JavaScript. |
| browserBlockPlugins | Boolean | Indicates whether or not to block plug-ins. |
| browserBlockPopups | Boolean | Indicates whether or not to block popups. |
| browserBlockSendingDoNotTrackHeader | Boolean | Indicates whether or not to Block the user from sending the do not track header. |
| browserBlockSingleWordEntryOnIntranetSites | Boolean | Indicates whether or not to block a single word entry on Intranet sites. |
| browserRequireSmartScreen | Boolean | Indicates whether or not to require the user to use the smart screen filter. |
| browserEnterpriseModeSiteListLocation | String | The enterprise mode site list location. Could be a local file, local network or http location. |
| browserInternetSecurityLevel | [internetSiteSecurityLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-internetsitesecuritylevel?view=graph-rest-1.0) | The internet security level. The possible values are: `userDefined`, `medium`, `mediumHigh`, `high`. |
| browserIntranetSecurityLevel | [siteSecurityLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sitesecuritylevel?view=graph-rest-1.0) | The Intranet security level. The possible values are: `userDefined`, `low`, `mediumLow`, `medium`, `mediumHigh`, `high`. |
| browserLoggingReportLocation | String | The logging report location. |
| browserRequireHighSecurityForRestrictedSites | Boolean | Indicates whether or not to require high security for restricted sites. |
| browserRequireFirewall | Boolean | Indicates whether or not to require a firewall. |
| browserRequireFraudWarning | Boolean | Indicates whether or not to require fraud warning. |
| browserTrustedSitesSecurityLevel | [siteSecurityLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-sitesecuritylevel?view=graph-rest-1.0) | The trusted sites security level. The possible values are: `userDefined`, `low`, `mediumLow`, `medium`, `mediumHigh`, `high`. |
| cellularBlockDataRoaming | Boolean | Indicates whether or not to block data roaming. |
| diagnosticsBlockDataSubmission | Boolean | Indicates whether or not to block diagnostic data submission. |
| passwordBlockPicturePasswordAndPin | Boolean | Indicates whether or not to Block the user from using a pictures password and pin. |
| passwordExpirationDays | Int32 | Password expiration in days. |
| passwordMinimumLength | Int32 | The minimum password length. |
| passwordMinutesOfInactivityBeforeScreenTimeout | Int32 | The minutes of inactivity before the screen times out. |
| passwordMinimumCharacterSetCount | Int32 | The number of character sets required in the password. |
| passwordPreviousPasswordBlockCount | Int32 | The number of previous passwords to prevent re-use of. Valid values 0 to 24 |
| passwordRequiredType | [requiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-requiredpasswordtype?view=graph-rest-1.0) | The required password type. The possible values are: `deviceDefault`, `alphanumeric`, `numeric`. |
| passwordSignInFailureCountBeforeFactoryReset | Int32 | The number of sign in failures before factory reset. |
| storageRequireDeviceEncryption | Boolean | Indicates whether or not to require encryption on a mobile device. |
| updatesRequireAutomaticUpdates | Boolean | Indicates whether or not to require automatic updates. |
| userAccountControlSettings | [windowsUserAccountControlSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsuseraccountcontrolsettings?view=graph-rest-1.0) | The user account control settings. The possible values are: `userDefined`, `alwaysNotify`, `notifyOnAppChanges`, `notifyOnAppChangesWithoutDimming`, `neverNotify`. |
| workFoldersUrl | String | The work folders url. |

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
  "@odata.type": "#microsoft.graph.windows81GeneralConfiguration",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "version": 1024,
  "accountsBlockAddingNonMicrosoftAccountEmail": true,
  "applyOnlyToWindows81": true,
  "browserBlockAutofill": true,
  "browserBlockAutomaticDetectionOfIntranetSites": true,
  "browserBlockEnterpriseModeAccess": true,
  "browserBlockJavaScript": true,
  "browserBlockPlugins": true,
  "browserBlockPopups": true,
  "browserBlockSendingDoNotTrackHeader": true,
  "browserBlockSingleWordEntryOnIntranetSites": true,
  "browserRequireSmartScreen": true,
  "browserEnterpriseModeSiteListLocation": "String",
  "browserInternetSecurityLevel": "String",
  "browserIntranetSecurityLevel": "String",
  "browserLoggingReportLocation": "String",
  "browserRequireHighSecurityForRestrictedSites": true,
  "browserRequireFirewall": true,
  "browserRequireFraudWarning": true,
  "browserTrustedSitesSecurityLevel": "String",
  "cellularBlockDataRoaming": true,
  "diagnosticsBlockDataSubmission": true,
  "passwordBlockPicturePasswordAndPin": true,
  "passwordExpirationDays": 1024,
  "passwordMinimumLength": 1024,
  "passwordMinutesOfInactivityBeforeScreenTimeout": 1024,
  "passwordMinimumCharacterSetCount": 1024,
  "passwordPreviousPasswordBlockCount": 1024,
  "passwordRequiredType": "String",
  "passwordSignInFailureCountBeforeFactoryReset": 1024,
  "storageRequireDeviceEncryption": true,
  "updatesRequireAutomaticUpdates": true,
  "userAccountControlSettings": "String",
  "workFoldersUrl": "String"
}
```
