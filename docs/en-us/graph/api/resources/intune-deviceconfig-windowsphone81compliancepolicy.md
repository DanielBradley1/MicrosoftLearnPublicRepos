<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81compliancepolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsPhone81CompliancePolicy resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This class contains compliance settings for Windows 8.1 Mobile.

Inherits from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsPhone81CompliancePolicies](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81compliancepolicy-list?view=graph-rest-1.0) | [windowsPhone81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81compliancepolicy?view=graph-rest-1.0) collection | List properties and relationships of the [windowsPhone81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81compliancepolicy?view=graph-rest-1.0) objects. |
| [Get windowsPhone81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81compliancepolicy-get?view=graph-rest-1.0) | [windowsPhone81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81compliancepolicy?view=graph-rest-1.0) | Read properties and relationships of the [windowsPhone81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81compliancepolicy?view=graph-rest-1.0) object. |
| [Create windowsPhone81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81compliancepolicy-create?view=graph-rest-1.0) | [windowsPhone81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81compliancepolicy?view=graph-rest-1.0) | Create a new [windowsPhone81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81compliancepolicy?view=graph-rest-1.0) object. |
| [Delete windowsPhone81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81compliancepolicy-delete?view=graph-rest-1.0) | None | Deletes a [windowsPhone81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81compliancepolicy?view=graph-rest-1.0). |
| [Update windowsPhone81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsphone81compliancepolicy-update?view=graph-rest-1.0) | [windowsPhone81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81compliancepolicy?view=graph-rest-1.0) | Update the properties of a [windowsPhone81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsphone81compliancepolicy?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| passwordBlockSimple | Boolean | Whether or not to block syncing the calendar. |
| passwordExpirationDays | Int32 | Number of days before the password expires. |
| passwordMinimumLength | Int32 | Minimum length of passwords. |
| passwordMinutesOfInactivityBeforeLock | Int32 | Minutes of inactivity before a password is required. |
| passwordMinimumCharacterSetCount | Int32 | The number of character sets required in the password. |
| passwordRequiredType | [requiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-requiredpasswordtype?view=graph-rest-1.0) | The required password type. The possible values are: `deviceDefault`, `alphanumeric`, `numeric`. |
| passwordPreviousPasswordBlockCount | Int32 | Number of previous passwords to block. Valid values 0 to 24 |
| passwordRequired | Boolean | Whether or not to require a password. |
| osMinimumVersion | String | Minimum Windows Phone version. |
| osMaximumVersion | String | Maximum Windows Phone version. |
| storageRequireEncryption | Boolean | Require encryption on windows phone devices. |

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
  "@odata.type": "#microsoft.graph.windowsPhone81CompliancePolicy",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "version": 1024,
  "passwordBlockSimple": true,
  "passwordExpirationDays": 1024,
  "passwordMinimumLength": 1024,
  "passwordMinutesOfInactivityBeforeLock": 1024,
  "passwordMinimumCharacterSetCount": 1024,
  "passwordRequiredType": "String",
  "passwordPreviousPasswordBlockCount": 1024,
  "passwordRequired": true,
  "osMinimumVersion": "String",
  "osMaximumVersion": "String",
  "storageRequireEncryption": true
}
```
