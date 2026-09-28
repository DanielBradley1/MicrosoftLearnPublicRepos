<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownercompliancepolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-13 -->

# androidDeviceOwnerCompliancePolicy resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This topic provides descriptions of the declared methods, properties and relationships exposed by the AndroidDeviceOwnerCompliancePolicy resource.

Inherits from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List androidDeviceOwnerCompliancePolicies](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androiddeviceownercompliancepolicy-list?view=graph-rest-beta) | [androidDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownercompliancepolicy?view=graph-rest-beta) collection | List properties and relationships of the [androidDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownercompliancepolicy?view=graph-rest-beta) objects. |
| [Get androidDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androiddeviceownercompliancepolicy-get?view=graph-rest-beta) | [androidDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownercompliancepolicy?view=graph-rest-beta) | Read properties and relationships of the [androidDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownercompliancepolicy?view=graph-rest-beta) object. |
| [Create androidDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androiddeviceownercompliancepolicy-create?view=graph-rest-beta) | [androidDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownercompliancepolicy?view=graph-rest-beta) | Create a new [androidDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownercompliancepolicy?view=graph-rest-beta) object. |
| [Delete androidDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androiddeviceownercompliancepolicy-delete?view=graph-rest-beta) | None | Deletes a [androidDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownercompliancepolicy?view=graph-rest-beta). |
| [Update androidDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-androiddeviceownercompliancepolicy-update?view=graph-rest-beta) | [androidDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownercompliancepolicy?view=graph-rest-beta) | Update the properties of a [androidDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownercompliancepolicy?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| id | String | Key of the entity. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| version | Int32 | Version of the device configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| deviceThreatProtectionEnabled | Boolean | Indicates whether the policy requires devices have device threat protection enabled. When TRUE, threat protection is enabled. When FALSE, threat protection is not enabled. Default is FALSE. |
| deviceThreatProtectionRequiredSecurityLevel | [deviceThreatProtectionLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicethreatprotectionlevel?view=graph-rest-beta) | Indicates the minimum mobile threat protection risk level to that results in Intune reporting device noncompliance. Possible values are: `unavailable`, `secured`, `low`, `medium`, `high`, `notSet`. Possible values are: `unavailable`, `secured`, `low`, `medium`, `high`, `notSet`. |
| advancedThreatProtectionRequiredSecurityLevel | [deviceThreatProtectionLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicethreatprotectionlevel?view=graph-rest-beta) | Indicates the Microsoft Defender for Endpoint \(also referred to Microsoft Defender Advanced Threat Protection \(MDATP\)\) minimum risk level to report noncompliance. Possible values are: `unavailable`, `secured`, `low`, `medium`, `high`, `notSet`. Possible values are: `unavailable`, `secured`, `low`, `medium`, `high`, `notSet`. |
| securityBlockJailbrokenDevices | Boolean | Indicates the device should not be rooted. When TRUE, if the device is detected as rooted it will be reported non-compliant. When FALSE, the device is not reported as non-compliant regardless of device rooted state. Default is FALSE. |
| securityRequireSafetyNetAttestationBasicIntegrity | Boolean | Indicates whether the compliance check will validate the Google Play Integrity check. When TRUE, the Google Play integrity basic check must pass to consider the device compliant. When FALSE, the Google Play integrity basic check can pass or fail and the device will be considered compliant. Default is FALSE. |
| securityRequireSafetyNetAttestationCertifiedDevice | Boolean | Indicates whether the compliance check will validate the Google Play Integrity check. When TRUE, the Google Play integrity device check must pass to consider the device compliant. When FALSE, the Google Play integrity device check can pass or fail and the device will be considered compliant. Default is FALSE. |
| osMinimumVersion | String | Indicates the minimum Android version required to mark the device as compliant. For example: "14" |
| osMaximumVersion | String | Indicates the maximum Android version required to mark the device as compliant. For example: "15" |
| minAndroidSecurityPatchLevel | String | Indicates the minimum Android security patch level required to mark the device as compliant. For example: "February 1, 2025" |
| passwordRequired | Boolean | Indicates whether a password is required to unlock the device. When TRUE, there must be a password set that unlocks the device for the device to be marked as compliant. When FALSE, a device is marked as compliant whether or not a password is set as required to unlock the device. Default is FALSE. |
| passwordMinimumLength | Int32 | Indicates the minimum password length required to mark the device as compliant. Valid values are 4 to 16, inclusive. Valid values 4 to 16 |
| passwordMinimumLetterCharacters | Int32 | Indicates the minimum number of letter characters required for device password for the device to be marked compliant. Valid values 1 to 16. |
| passwordMinimumLowerCaseCharacters | Int32 | Indicates the minimum number of lower case characters required for device password for the device to be marked compliant. Valid values 1 to 16. |
| passwordMinimumNonLetterCharacters | Int32 | Indicates the minimum number of non-letter characters required for device password for the device to be marked compliant. Valid values 1 to 16. |
| passwordMinimumNumericCharacters | Int32 | Indicates the minimum number of numeric characters required for device password for the device to be marked compliant. Valid values 1 to 16. |
| passwordMinimumSymbolCharacters | Int32 | Indicates the minimum number of symbol characters required for device password for the device to be marked compliant. Valid values 1 to 16. |
| passwordMinimumUpperCaseCharacters | Int32 | Indicates the minimum number of upper case letter characters required for device password for the device to be marked compliant. Valid values 1 to 16. |
| passwordRequiredType | [androidDeviceOwnerRequiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownerrequiredpasswordtype?view=graph-rest-beta) | Indicates the password complexity requirement for the device to be marked compliant. Possible values are: `deviceDefault`, `required`, `numeric`, `numericComplex`, `alphabetic`, `alphanumeric`, `alphanumericWithSymbols`, `lowSecurityBiometric`, `customPassword`. Possible values are: `deviceDefault`, `required`, `numeric`, `numericComplex`, `alphabetic`, `alphanumeric`, `alphanumericWithSymbols`, `lowSecurityBiometric`, `customPassword`. |
| passwordMinutesOfInactivityBeforeLock | Int32 | Indicates the number of minutes of inactivity before a password is required. |
| passwordExpirationDays | Int32 | Indicates the number of days before the password expires. Valid values 1 to 365. |
| passwordPreviousPasswordCountToBlock | Int32 | Indicates the number of previous passwords to block. Valid values 1 to 24. |
| storageRequireEncryption | Boolean | Indicates whether encryption on Android devices is required to mark the device as compliant. |
| securityRequireIntuneAppIntegrity | Boolean | Indicates whether Intune application integrity is required to mark the device as compliant. When TRUE, Intune checks that the Intune app installed on fully managed, dedicated, or corporate-owned work profile Android Enterprise enrolled devices, is the one provided by Microsoft from the Managed Google Play store. If the check fails, the device will be reported as non-compliant. Default is FALSE. |
| requireNoPendingSystemUpdates | Boolean | Indicates whether the device has pending security or OS updates and sets the compliance state accordingly. When TRUE, checks if there are any pending system updates on each check in and if there are any pending security or OS version updates \(System Updates\), the device will be reported as non-compliant. If set to FALSE, then checks for any pending security or OS version updates \(System Updates\) are done without impact to device compliance state. Default is FALSE. |
| securityRequiredAndroidSafetyNetEvaluationType | [androidSafetyNetEvaluationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androidsafetynetevaluationtype?view=graph-rest-beta) | Indicates the types of measurements and reference data used to evaluate the device SafetyNet evaluation. Evaluation is completed on the device to assess device integrity based on checks defined by Android and built into the device hardware, for example, compromised OS version or root detection. Possible values are: `basic`, `hardwareBacked`, with default value of `basic`. Possible values are: `basic`, `hardwareBacked`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| scheduledActionsForRule | [deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescheduledactionforrule?view=graph-rest-beta) collection | The list of scheduled action per rule for this compliance policy. This is a required property when creating any individual per-platform compliance policies. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| deviceStatuses | [deviceComplianceDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancedevicestatus?view=graph-rest-beta) collection | List of DeviceComplianceDeviceStatus. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| userStatuses | [deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuserstatus?view=graph-rest-beta) collection | List of DeviceComplianceUserStatus. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| deviceStatusOverview | [deviceComplianceDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancedeviceoverview?view=graph-rest-beta) | Device compliance devices status overview Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| userStatusOverview | [deviceComplianceUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuseroverview?view=graph-rest-beta) | Device compliance users status overview Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| deviceSettingStateSummaries | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-beta) collection | Compliance Setting State Device Summary Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |
| assignments | [deviceCompliancePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicyassignment?view=graph-rest-beta) collection | The collection of assignments for this compliance policy. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidDeviceOwnerCompliancePolicy",
  "roleScopeTagIds": [
    "String"
  ],
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "version": 1024,
  "deviceThreatProtectionEnabled": true,
  "deviceThreatProtectionRequiredSecurityLevel": "String",
  "advancedThreatProtectionRequiredSecurityLevel": "String",
  "securityBlockJailbrokenDevices": true,
  "securityRequireSafetyNetAttestationBasicIntegrity": true,
  "securityRequireSafetyNetAttestationCertifiedDevice": true,
  "osMinimumVersion": "String",
  "osMaximumVersion": "String",
  "minAndroidSecurityPatchLevel": "String",
  "passwordRequired": true,
  "passwordMinimumLength": 1024,
  "passwordMinimumLetterCharacters": 1024,
  "passwordMinimumLowerCaseCharacters": 1024,
  "passwordMinimumNonLetterCharacters": 1024,
  "passwordMinimumNumericCharacters": 1024,
  "passwordMinimumSymbolCharacters": 1024,
  "passwordMinimumUpperCaseCharacters": 1024,
  "passwordRequiredType": "String",
  "passwordMinutesOfInactivityBeforeLock": 1024,
  "passwordExpirationDays": 1024,
  "passwordPreviousPasswordCountToBlock": 1024,
  "storageRequireEncryption": true,
  "securityRequireIntuneAppIntegrity": true,
  "requireNoPendingSystemUpdates": true,
  "securityRequiredAndroidSafetyNetEvaluationType": "String"
}
```
