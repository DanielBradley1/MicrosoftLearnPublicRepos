<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcompliancepolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# androidCompliancePolicy resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This class contains compliance settings for Android.

Inherits from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List androidCompliancePolicies](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidcompliancepolicy-list?view=graph-rest-1.0) | [androidCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcompliancepolicy?view=graph-rest-1.0) collection | List properties and relationships of the [androidCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcompliancepolicy?view=graph-rest-1.0) objects. |
| [Get androidCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidcompliancepolicy-get?view=graph-rest-1.0) | [androidCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcompliancepolicy?view=graph-rest-1.0) | Read properties and relationships of the [androidCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcompliancepolicy?view=graph-rest-1.0) object. |
| [Create androidCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidcompliancepolicy-create?view=graph-rest-1.0) | [androidCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcompliancepolicy?view=graph-rest-1.0) | Create a new [androidCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcompliancepolicy?view=graph-rest-1.0) object. |
| [Delete androidCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidcompliancepolicy-delete?view=graph-rest-1.0) | None | Deletes a [androidCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcompliancepolicy?view=graph-rest-1.0). |
| [Update androidCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androidcompliancepolicy-update?view=graph-rest-1.0) | [androidCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcompliancepolicy?view=graph-rest-1.0) | Update the properties of a [androidCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidcompliancepolicy?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| passwordRequired | Boolean | Require a password to unlock device. |
| passwordMinimumLength | Int32 | Minimum password length. Valid values 4 to 16 |
| passwordRequiredType | [androidRequiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidrequiredpasswordtype?view=graph-rest-1.0) | Type of characters in password. The possible values are: `deviceDefault`, `alphabetic`, `alphanumeric`, `alphanumericWithSymbols`, `lowSecurityBiometric`, `numeric`, `numericComplex`, `any`. |
| passwordMinutesOfInactivityBeforeLock | Int32 | Minutes of inactivity before a password is required. |
| passwordExpirationDays | Int32 | Number of days before the password expires. Valid values 1 to 365 |
| passwordPreviousPasswordBlockCount | Int32 | Number of previous passwords to block. Valid values 1 to 24 |
| securityPreventInstallAppsFromUnknownSources | Boolean | Require that devices disallow installation of apps from unknown sources. |
| securityDisableUsbDebugging | Boolean | Disable USB debugging on Android devices. |
| securityRequireVerifyApps | Boolean | Require the Android Verify apps feature is turned on. |
| deviceThreatProtectionEnabled | Boolean | Require that devices have enabled device threat protection. |
| deviceThreatProtectionRequiredSecurityLevel | [deviceThreatProtectionLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicethreatprotectionlevel?view=graph-rest-1.0) | Require Mobile Threat Protection minimum risk level to report noncompliance. The possible values are: `unavailable`, `secured`, `low`, `medium`, `high`, `notSet`. |
| securityBlockJailbrokenDevices | Boolean | Indicates the device should not be rooted. When TRUE, if the device is detected as rooted it will be reported non-compliant. When FALSE, the device is not reported as non-compliant regardless of device rooted state. Default is FALSE. |
| osMinimumVersion | String | Minimum Android version. |
| osMaximumVersion | String | Maximum Android version. |
| minAndroidSecurityPatchLevel | String | Minimum Android security patch level. |
| storageRequireEncryption | Boolean | Require encryption on Android devices. |
| securityRequireSafetyNetAttestationBasicIntegrity | Boolean | Require the device to pass the SafetyNet basic integrity check. |
| securityRequireSafetyNetAttestationCertifiedDevice | Boolean | Require the device to pass the SafetyNet certified device check. |
| securityRequireGooglePlayServices | Boolean | Require Google Play Services to be installed and enabled on the device. |
| securityRequireUpToDateSecurityProviders | Boolean | Require the device to have up to date security providers. The device will require Google Play Services to be enabled and up to date. |
| securityRequireCompanyPortalAppIntegrity | Boolean | Require the device to pass the Company Portal client app runtime integrity check. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| scheduledActionsForRule | [deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescheduledactionforrule?view=graph-rest-1.0) collection | The list of scheduled action per rule for this compliance policy. This is a required property when creating any individual per-platform compliance policies. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| deviceStatuses | [deviceComplianceDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancedevicestatus?view=graph-rest-1.0) collection | List of DeviceComplianceDeviceStatus. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| userStatuses | [deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuserstatus?view=graph-rest-1.0) collection | List of DeviceComplianceUserStatus. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| deviceStatusOverview | [deviceComplianceDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancedeviceoverview?view=graph-rest-1.0) | Device compliance devices status overview Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| userStatusOverview | [deviceComplianceUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuseroverview?view=graph-rest-1.0) | Device compliance users status overview Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| deviceSettingStateSummaries | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-1.0) collection | Compliance Setting State Device Summary Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| assignments | [deviceCompliancePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicyassignment?view=graph-rest-1.0) collection | The collection of assignments for this compliance policy. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidCompliancePolicy",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "version": 1024,
  "passwordRequired": true,
  "passwordMinimumLength": 1024,
  "passwordRequiredType": "String",
  "passwordMinutesOfInactivityBeforeLock": 1024,
  "passwordExpirationDays": 1024,
  "passwordPreviousPasswordBlockCount": 1024,
  "securityPreventInstallAppsFromUnknownSources": true,
  "securityDisableUsbDebugging": true,
  "securityRequireVerifyApps": true,
  "deviceThreatProtectionEnabled": true,
  "deviceThreatProtectionRequiredSecurityLevel": "String",
  "securityBlockJailbrokenDevices": true,
  "osMinimumVersion": "String",
  "osMaximumVersion": "String",
  "minAndroidSecurityPatchLevel": "String",
  "storageRequireEncryption": true,
  "securityRequireSafetyNetAttestationBasicIntegrity": true,
  "securityRequireSafetyNetAttestationCertifiedDevice": true,
  "securityRequireGooglePlayServices": true,
  "securityRequireUpToDateSecurityProviders": true,
  "securityRequireCompanyPortalAppIntegrity": true
}
```
