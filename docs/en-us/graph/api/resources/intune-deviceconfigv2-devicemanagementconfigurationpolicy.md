<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementConfigurationPolicy resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device Management Configuration Policy

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementConfigurationPolicies](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicy-list?view=graph-rest-beta) | [deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicy?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicy?view=graph-rest-beta) objects. |
| [Get deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicy-get?view=graph-rest-beta) | [deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicy?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicy?view=graph-rest-beta) object. |
| [Create deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicy-create?view=graph-rest-beta) | [deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicy?view=graph-rest-beta) | Create a new [deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicy?view=graph-rest-beta) object. |
| [Delete deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicy-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicy?view=graph-rest-beta). |
| [Update deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicy-update?view=graph-rest-beta) | [deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicy?view=graph-rest-beta) | Update the properties of a [deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicy?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/api/intune-deviceconfigv2-devicemanagementconfigurationpolicy-assign.md?view=graph-rest-beta) | [deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment?view=graph-rest-beta) collection |  |
| [createCopy action](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicy-createcopy?view=graph-rest-beta) | [deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicy?view=graph-rest-beta) |  |
| [reorder action](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicy-reorder?view=graph-rest-beta) | None |  |
| [retrieveLatestUpgradeDefaultBaselinePolicy function](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicy-retrievelatestupgradedefaultbaselinepolicy?view=graph-rest-beta) | [deviceManagementConfigurationPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicy?view=graph-rest-beta) |  |
| [retrieveJustInTimeConfiguration action](https://learn.microsoft.com/en-us/graph/api/api/intune-deviceconfigv2-devicemanagementconfigurationpolicy-retrievejustintimeconfiguration.md?view=graph-rest-beta) | [deviceManagementConfigurationJustInTimeAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationjustintimeassignmentpolicy.md?view=graph-rest-beta) |  |
| [assignJustInTimeConfiguration action](https://learn.microsoft.com/en-us/graph/api/api/intune-deviceconfigv2-devicemanagementconfigurationpolicy-assignjustintimeconfiguration.md?view=graph-rest-beta) | Boolean |  |
| [retrieveEnrollmentTimeDeviceMembershipTarget action](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicy-retrieveenrollmenttimedevicemembershiptarget?view=graph-rest-beta) | [enrollmentTimeDeviceMembershipTargetResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enrollmenttimedevicemembershiptargetresult?view=graph-rest-beta) |  |
| [setEnrollmentTimeDeviceMembershipTarget action](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicy-setenrollmenttimedevicemembershiptarget?view=graph-rest-beta) | [enrollmentTimeDeviceMembershipTargetResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-enrollmenttimedevicemembershiptargetresult?view=graph-rest-beta) |  |
| [clearEnrollmentTimeDeviceMembershipTarget action](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationpolicy-clearenrollmenttimedevicemembershiptarget?view=graph-rest-beta) | Boolean |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the policy document. Automatically generated. |
| name | String | Policy name |
| description | String | Policy description |
| platforms | [deviceManagementConfigurationPlatforms](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationplatforms?view=graph-rest-beta) | Platforms for this policy. The possible values are: `none`, `android`, `iOS`, `macOS`, `windows10X`, `windows10`, `linux`, `unknownFutureValue`, `androidEnterprise`, `aosp`, `visionOS`, `tvOS`. |
| technologies | [deviceManagementConfigurationTechnologies](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationtechnologies?view=graph-rest-beta) | Technologies for this policy. The possible values are: `none`, `mdm`, `windows10XManagement`, `configManager`, `appleRemoteManagement`, `microsoftSense`, `exchangeOnline`, `mobileApplicationManagement`, `linuxMdm`, `extensibility`, `enrollment`, `endpointPrivilegeManagement`, `unknownFutureValue`, `windowsOsRecovery`, `android`. |
| createdDateTime | DateTimeOffset | Policy creation date and time |
| lastModifiedDateTime | DateTimeOffset | Policy last modification date and time |
| settingCount | Int32 | Number of settings |
| creationSource | String | Policy creation source |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. |
| isAssigned | Boolean | Policy assignment status. This property is read-only. |
| templateReference | [deviceManagementConfigurationPolicyTemplateReference](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicytemplatereference?view=graph-rest-beta) | Template reference information |
| priorityMetaData | [deviceManagementPriorityMetaData](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementprioritymetadata?view=graph-rest-beta) | Indicates the priority of each policies that are selected by the admin during enrollment process |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| settings | [deviceManagementConfigurationSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsetting?view=graph-rest-beta) collection | Policy settings |
| assignments | [deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment?view=graph-rest-beta) collection | Policy assignments |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationPolicy",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "platforms": "String",
  "technologies": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "settingCount": 1024,
  "creationSource": "String",
  "roleScopeTagIds": [
    "String"
  ],
  "isAssigned": true,
  "templateReference": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationPolicyTemplateReference",
    "templateId": "String",
    "templateFamily": "String",
    "templateDisplayName": "String",
    "templateDisplayVersion": "String"
  },
  "priorityMetaData": {
    "@odata.type": "microsoft.graph.deviceManagementPriorityMetaData",
    "priority": 1024
  }
}
```
