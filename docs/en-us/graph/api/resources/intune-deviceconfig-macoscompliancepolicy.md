<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscompliancepolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# macOSCompliancePolicy resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This class contains compliance settings for Mac OS.

Inherits from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOSCompliancePolicies](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macoscompliancepolicy-list?view=graph-rest-1.0) | [macOSCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscompliancepolicy?view=graph-rest-1.0) collection | List properties and relationships of the [macOSCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscompliancepolicy?view=graph-rest-1.0) objects. |
| [Get macOSCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macoscompliancepolicy-get?view=graph-rest-1.0) | [macOSCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscompliancepolicy?view=graph-rest-1.0) | Read properties and relationships of the [macOSCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscompliancepolicy?view=graph-rest-1.0) object. |
| [Create macOSCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macoscompliancepolicy-create?view=graph-rest-1.0) | [macOSCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscompliancepolicy?view=graph-rest-1.0) | Create a new [macOSCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscompliancepolicy?view=graph-rest-1.0) object. |
| [Delete macOSCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macoscompliancepolicy-delete?view=graph-rest-1.0) | None | Deletes a [macOSCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscompliancepolicy?view=graph-rest-1.0). |
| [Update macOSCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macoscompliancepolicy-update?view=graph-rest-1.0) | [macOSCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscompliancepolicy?view=graph-rest-1.0) | Update the properties of a [macOSCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macoscompliancepolicy?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| passwordRequired | Boolean | Whether or not to require a password. |
| passwordBlockSimple | Boolean | Indicates whether or not to block simple passwords. |
| passwordExpirationDays | Int32 | Number of days before the password expires. Valid values 1 to 65535 |
| passwordMinimumLength | Int32 | Minimum length of password. Valid values 4 to 14 |
| passwordMinutesOfInactivityBeforeLock | Int32 | Minutes of inactivity before a password is required. |
| passwordPreviousPasswordBlockCount | Int32 | Number of previous passwords to block. Valid values 1 to 24 |
| passwordMinimumCharacterSetCount | Int32 | The number of character sets required in the password. |
| passwordRequiredType | [requiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-requiredpasswordtype?view=graph-rest-1.0) | The required password type. The possible values are: `deviceDefault`, `alphanumeric`, `numeric`. |
| osMinimumVersion | String | Minimum MacOS version. |
| osMaximumVersion | String | Maximum MacOS version. |
| systemIntegrityProtectionEnabled | Boolean | Require that devices have enabled system integrity protection. |
| deviceThreatProtectionEnabled | Boolean | Require that devices have enabled device threat protection. |
| deviceThreatProtectionRequiredSecurityLevel | [deviceThreatProtectionLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicethreatprotectionlevel?view=graph-rest-1.0) | Require Mobile Threat Protection minimum risk level to report noncompliance. The possible values are: `unavailable`, `secured`, `low`, `medium`, `high`, `notSet`. |
| storageRequireEncryption | Boolean | Require encryption on Mac OS devices. |
| firewallEnabled | Boolean | Whether the firewall should be enabled or not. |
| firewallBlockAllIncoming | Boolean | Corresponds to the “Block all incoming connections” option. |
| firewallEnableStealthMode | Boolean | Corresponds to “Enable stealth mode.” |

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
  "@odata.type": "#microsoft.graph.macOSCompliancePolicy",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "version": 1024,
  "passwordRequired": true,
  "passwordBlockSimple": true,
  "passwordExpirationDays": 1024,
  "passwordMinimumLength": 1024,
  "passwordMinutesOfInactivityBeforeLock": 1024,
  "passwordPreviousPasswordBlockCount": 1024,
  "passwordMinimumCharacterSetCount": 1024,
  "passwordRequiredType": "String",
  "osMinimumVersion": "String",
  "osMaximumVersion": "String",
  "systemIntegrityProtectionEnabled": true,
  "deviceThreatProtectionEnabled": true,
  "deviceThreatProtectionRequiredSecurityLevel": "String",
  "storageRequireEncryption": true,
  "firewallEnabled": true,
  "firewallBlockAllIncoming": true,
  "firewallEnableStealthMode": true
}
```
