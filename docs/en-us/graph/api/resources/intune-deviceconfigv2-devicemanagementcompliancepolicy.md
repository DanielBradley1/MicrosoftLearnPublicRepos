<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancepolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementCompliancePolicy resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device Management Compliance Policy

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementCompliancePolicies](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcompliancepolicy-list?view=graph-rest-beta) | [deviceManagementCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancepolicy?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancepolicy?view=graph-rest-beta) objects. |
| [Get deviceManagementCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcompliancepolicy-get?view=graph-rest-beta) | [deviceManagementCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancepolicy?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancepolicy?view=graph-rest-beta) object. |
| [Create deviceManagementCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcompliancepolicy-create?view=graph-rest-beta) | [deviceManagementCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancepolicy?view=graph-rest-beta) | Create a new [deviceManagementCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancepolicy?view=graph-rest-beta) object. |
| [Delete deviceManagementCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcompliancepolicy-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancepolicy?view=graph-rest-beta). |
| [Update deviceManagementCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcompliancepolicy-update?view=graph-rest-beta) | [deviceManagementCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancepolicy?view=graph-rest-beta) | Update the properties of a [deviceManagementCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancepolicy?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/api/intune-deviceconfigv2-devicemanagementcompliancepolicy-assign.md?view=graph-rest-beta) | [deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment?view=graph-rest-beta) collection |  |
| [setScheduledActions action](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementcompliancepolicy-setscheduledactions?view=graph-rest-beta) | [deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the policy document. Automatically generated. |
| name | String | Policy name |
| description | String | Policy description |
| platforms | [deviceManagementConfigurationPlatforms](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationplatforms?view=graph-rest-beta) | Platforms for this policy. Possible values are: `none`, `android`, `iOS`, `macOS`, `windows10X`, `windows10`, `linux`, `unknownFutureValue`, `androidEnterprise`, `aosp`, `visionOS`, `tvOS`. |
| technologies | [deviceManagementConfigurationTechnologies](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationtechnologies?view=graph-rest-beta) | Technologies for this policy. Possible values are: `none`, `mdm`, `windows10XManagement`, `configManager`, `appleRemoteManagement`, `microsoftSense`, `exchangeOnline`, `mobileApplicationManagement`, `linuxMdm`, `extensibility`, `enrollment`, `endpointPrivilegeManagement`, `unknownFutureValue`, `windowsOsRecovery`, `android`. |
| createdDateTime | DateTimeOffset | Policy creation date and time. This property is read-only. |
| lastModifiedDateTime | DateTimeOffset | Policy last modification date and time. This property is read-only. |
| settingCount | Int32 | Number of settings. This property is read-only. |
| creationSource | String | Policy creation source |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. |
| isAssigned | Boolean | Policy assignment status. This property is read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| settings | [deviceManagementConfigurationSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsetting?view=graph-rest-beta) collection | Policy settings |
| assignments | [deviceManagementConfigurationPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationpolicyassignment?view=graph-rest-beta) collection | Policy assignments |
| scheduledActionsForRule | [deviceManagementComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementcompliancescheduledactionforrule?view=graph-rest-beta) collection | The list of scheduled action for this rule |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementCompliancePolicy",
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
  "isAssigned": true
}
```
