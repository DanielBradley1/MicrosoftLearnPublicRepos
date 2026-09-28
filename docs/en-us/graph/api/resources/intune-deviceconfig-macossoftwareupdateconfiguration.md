<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# macOSSoftwareUpdateConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

MacOS Software Update Configuration

Inherits from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List macOSSoftwareUpdateConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdateconfiguration-list?view=graph-rest-beta) | [macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateconfiguration?view=graph-rest-beta) objects. |
| [Get macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdateconfiguration-get?view=graph-rest-beta) | [macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateconfiguration?view=graph-rest-beta) | Read properties and relationships of the [macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateconfiguration?view=graph-rest-beta) object. |
| [Create macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdateconfiguration-create?view=graph-rest-beta) | [macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateconfiguration?view=graph-rest-beta) | Create a new [macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateconfiguration?view=graph-rest-beta) object. |
| [Delete macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdateconfiguration-delete?view=graph-rest-beta) | None | Deletes a [macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateconfiguration?view=graph-rest-beta). |
| [Update macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-macossoftwareupdateconfiguration-update?view=graph-rest-beta) | [macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateconfiguration?view=graph-rest-beta) | Update the properties of a [macOSSoftwareUpdateConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdateconfiguration?view=graph-rest-beta) object. |

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
| criticalUpdateBehavior | [macOSSoftwareUpdateBehavior](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatebehavior?view=graph-rest-beta) | Update behavior for critical updates. Possible values are: `notConfigured`, `default`, `downloadOnly`, `installASAP`, `notifyOnly`, `installLater`. |
| configDataUpdateBehavior | [macOSSoftwareUpdateBehavior](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatebehavior?view=graph-rest-beta) | Update behavior for configuration data file updates. Possible values are: `notConfigured`, `default`, `downloadOnly`, `installASAP`, `notifyOnly`, `installLater`. |
| firmwareUpdateBehavior | [macOSSoftwareUpdateBehavior](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatebehavior?view=graph-rest-beta) | Update behavior for firmware updates. Possible values are: `notConfigured`, `default`, `downloadOnly`, `installASAP`, `notifyOnly`, `installLater`. |
| allOtherUpdateBehavior | [macOSSoftwareUpdateBehavior](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatebehavior?view=graph-rest-beta) | Update behavior for all other updates. Possible values are: `notConfigured`, `default`, `downloadOnly`, `installASAP`, `notifyOnly`, `installLater`. |
| updateScheduleType | [macOSSoftwareUpdateScheduleType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macossoftwareupdatescheduletype?view=graph-rest-beta) | Update schedule type. Possible values are: `alwaysUpdate`, `updateDuringTimeWindows`, `updateOutsideOfTimeWindows`. |
| customUpdateTimeWindows | [customUpdateTimeWindow](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-customupdatetimewindow?view=graph-rest-beta) collection | Custom Time windows when updates will be allowed or blocked. This collection can contain a maximum of 20 elements. |
| updateTimeWindowUtcOffsetInMinutes | Int32 | Minutes indicating UTC offset for each update time window |
| maxUserDeferralsCount | Int32 | The maximum number of times the system allows the user to postpone an update before it’s installed. Supported values: 0 - 366. Valid values 0 to 365 |
| priority | [macOSPriority](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-macospriority?view=graph-rest-beta) | The scheduling priority for downloading and preparing the requested update. Default: Low. Possible values: Null, Low, High. Possible values are: `low`, `high`, `unknownFutureValue`. |

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
  "@odata.type": "#microsoft.graph.macOSSoftwareUpdateConfiguration",
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
  "criticalUpdateBehavior": "String",
  "configDataUpdateBehavior": "String",
  "firmwareUpdateBehavior": "String",
  "allOtherUpdateBehavior": "String",
  "updateScheduleType": "String",
  "customUpdateTimeWindows": [
    {
      "@odata.type": "microsoft.graph.customUpdateTimeWindow",
      "startDay": "String",
      "endDay": "String",
      "startTime": "String (time of day)",
      "endTime": "String (time of day)"
    }
  ],
  "updateTimeWindowUtcOffsetInMinutes": 1024,
  "maxUserDeferralsCount": 1024,
  "priority": "String"
}
```
