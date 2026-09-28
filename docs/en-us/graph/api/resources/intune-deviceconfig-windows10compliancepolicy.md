<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10compliancepolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-22 -->

# windows10CompliancePolicy resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This class contains compliance settings for Windows 10.

Inherits from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windows10CompliancePolicies](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10compliancepolicy-list?view=graph-rest-1.0) | [windows10CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10compliancepolicy?view=graph-rest-1.0) collection | List properties and relationships of the [windows10CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10compliancepolicy?view=graph-rest-1.0) objects. |
| [Get windows10CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10compliancepolicy-get?view=graph-rest-1.0) | [windows10CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10compliancepolicy?view=graph-rest-1.0) | Read properties and relationships of the [windows10CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10compliancepolicy?view=graph-rest-1.0) object. |
| [Create windows10CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10compliancepolicy-create?view=graph-rest-1.0) | [windows10CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10compliancepolicy?view=graph-rest-1.0) | Create a new [windows10CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10compliancepolicy?view=graph-rest-1.0) object. |
| [Delete windows10CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10compliancepolicy-delete?view=graph-rest-1.0) | None | Deletes a [windows10CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10compliancepolicy?view=graph-rest-1.0). |
| [Update windows10CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows10compliancepolicy-update?view=graph-rest-1.0) | [windows10CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10compliancepolicy?view=graph-rest-1.0) | Update the properties of a [windows10CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10compliancepolicy?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| passwordRequired | Boolean | Require a password to unlock Windows device. |
| passwordBlockSimple | Boolean | Indicates whether or not to block simple password. |
| passwordRequiredToUnlockFromIdle | Boolean | Require a password to unlock an idle device. |
| passwordMinutesOfInactivityBeforeLock | Int32 | Minutes of inactivity before a password is required. |
| passwordExpirationDays | Int32 | The password expiration in days. |
| passwordMinimumLength | Int32 | The minimum password length. |
| passwordMinimumCharacterSetCount | Int32 | The number of character sets required in the password. |
| passwordRequiredType | [requiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-requiredpasswordtype?view=graph-rest-1.0) | The required password type. The possible values are: `deviceDefault`, `alphanumeric`, `numeric`. |
| passwordPreviousPasswordBlockCount | Int32 | The number of previous passwords to prevent re-use of. |
| requireHealthyDeviceReport | Boolean | Require devices to be reported as healthy by Windows Device Health Attestation. |
| osMinimumVersion | String | Minimum Windows 10 version. |
| osMaximumVersion | String | Maximum Windows 10 version. |
| mobileOsMinimumVersion | String | Minimum Windows Phone version. |
| mobileOsMaximumVersion | String | Maximum Windows Phone version. |
| earlyLaunchAntiMalwareDriverEnabled | Boolean | Require devices to be reported as healthy by Windows Device Health Attestation - early launch antimalware driver is enabled. |
| bitLockerEnabled | Boolean | Require devices to be reported healthy by Windows Device Health Attestation - bit locker is enabled |
| secureBootEnabled | Boolean | Require devices to be reported as healthy by Windows Device Health Attestation - secure boot is enabled. |
| codeIntegrityEnabled | Boolean | Require devices to be reported as healthy by Windows Device Health Attestation. |
| storageRequireEncryption | Boolean | Require encryption on windows devices. |

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
  "@odata.type": "#microsoft.graph.windows10CompliancePolicy",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "version": 1024,
  "passwordRequired": true,
  "passwordBlockSimple": true,
  "passwordRequiredToUnlockFromIdle": true,
  "passwordMinutesOfInactivityBeforeLock": 1024,
  "passwordExpirationDays": 1024,
  "passwordMinimumLength": 1024,
  "passwordMinimumCharacterSetCount": 1024,
  "passwordRequiredType": "String",
  "passwordPreviousPasswordBlockCount": 1024,
  "requireHealthyDeviceReport": true,
  "osMinimumVersion": "String",
  "osMaximumVersion": "String",
  "mobileOsMinimumVersion": "String",
  "mobileOsMaximumVersion": "String",
  "earlyLaunchAntiMalwareDriverEnabled": true,
  "bitLockerEnabled": true,
  "secureBootEnabled": true,
  "codeIntegrityEnabled": true,
  "storageRequireEncryption": true
}
```
