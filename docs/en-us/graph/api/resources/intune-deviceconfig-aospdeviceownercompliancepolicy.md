<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownercompliancepolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# aospDeviceOwnerCompliancePolicy resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This topic provides descriptions of the declared methods, properties and relationships exposed by the AndroidDeviceOwnerAOSPCompliancePolicy resource.

Inherits from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List aospDeviceOwnerCompliancePolicies](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-aospdeviceownercompliancepolicy-list?view=graph-rest-beta) | [aospDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownercompliancepolicy?view=graph-rest-beta) collection | List properties and relationships of the [aospDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownercompliancepolicy?view=graph-rest-beta) objects. |
| [Get aospDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-aospdeviceownercompliancepolicy-get?view=graph-rest-beta) | [aospDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownercompliancepolicy?view=graph-rest-beta) | Read properties and relationships of the [aospDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownercompliancepolicy?view=graph-rest-beta) object. |
| [Create aospDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-aospdeviceownercompliancepolicy-create?view=graph-rest-beta) | [aospDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownercompliancepolicy?view=graph-rest-beta) | Create a new [aospDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownercompliancepolicy?view=graph-rest-beta) object. |
| [Delete aospDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-aospdeviceownercompliancepolicy-delete?view=graph-rest-beta) | None | Deletes a [aospDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownercompliancepolicy?view=graph-rest-beta). |
| [Update aospDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-aospdeviceownercompliancepolicy-update?view=graph-rest-beta) | [aospDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownercompliancepolicy?view=graph-rest-beta) | Update the properties of a [aospDeviceOwnerCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-aospdeviceownercompliancepolicy?view=graph-rest-beta) object. |

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
| osMinimumVersion | String | Minimum Android version. |
| osMaximumVersion | String | Maximum Android version. |
| minAndroidSecurityPatchLevel | String | Minimum Android security patch level. |
| securityBlockJailbrokenDevices | Boolean | Indicates the device should not be rooted. When TRUE, if the device is detected as rooted it will be reported non-compliant. When FALSE, the device is not reported as non-compliant regardless of device rooted state. Default is FALSE. |
| passwordRequired | Boolean | Require a password to unlock device. |
| passwordRequiredType | [androidDeviceOwnerRequiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-androiddeviceownerrequiredpasswordtype?view=graph-rest-beta) | Type of characters in password. Possible values are: `deviceDefault`, `required`, `numeric`, `numericComplex`, `alphabetic`, `alphanumeric`, `alphanumericWithSymbols`, `lowSecurityBiometric`, `customPassword`. |
| passwordMinutesOfInactivityBeforeLock | Int32 | Minutes of inactivity before a password is required. Valid values 1 to 8640 |
| passwordMinimumLength | Int32 | Minimum password length. Valid values 4 to 16 |
| storageRequireEncryption | Boolean | Require encryption on Android devices. |

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
  "@odata.type": "#microsoft.graph.aospDeviceOwnerCompliancePolicy",
  "roleScopeTagIds": [
    "String"
  ],
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "version": 1024,
  "osMinimumVersion": "String",
  "osMaximumVersion": "String",
  "minAndroidSecurityPatchLevel": "String",
  "securityBlockJailbrokenDevices": true,
  "passwordRequired": true,
  "passwordRequiredType": "String",
  "passwordMinutesOfInactivityBeforeLock": 1024,
  "passwordMinimumLength": 1024,
  "storageRequireEncryption": true
}
```
