<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceCompliancePolicy resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This is the base class for Compliance policy. Compliance policies are platform specific and individual per-platform compliance policies inherit from here.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceCompliancePolicies](https://learn.microsoft.com/en-us/graph/api/intune-shared-devicecompliancepolicy-list?view=graph-rest-beta) | [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) collection | List properties and relationships of the [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) objects. |
| [Get deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/intune-shared-devicecompliancepolicy-get?view=graph-rest-beta) | [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) | Read properties and relationships of the [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicecompliancepolicy?view=graph-rest-beta) object. |
| **Device configuration** |  |  |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-shared-devicecompliancepolicy-assign?view=graph-rest-beta) | [deviceCompliancePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicyassignment?view=graph-rest-beta) collection |  |
| scheduleActionsForRules action | None |  |
| refreshDeviceComplianceReportSummarization action\]\(../api/intune-shared-devicecompliancepolicy-refreshdevicecompliancereportsummarization.md\) | None |  |
| **Policy Set** |  |  |
| [hasPayloadLinks action](https://learn.microsoft.com/en-us/graph/api/intune-shared-devicecompliancepolicy-haspayloadlinks?view=graph-rest-beta) | [hasPayloadLinkResultItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-haspayloadlinkresultitem?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. |
| createdDateTime | DateTimeOffset | DateTime the object was created. |
| description | String | Admin provided description of the Device Configuration. |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. |
| displayName | String | Admin provided name of the device configuration. |
| version | Int32 | Version of the device configuration. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| **Device configuration** |  |  |
| scheduledActionsForRule | [deviceComplianceScheduledActionForRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancescheduledactionforrule?view=graph-rest-beta) collection | The list of scheduled action for this rule |
| deviceStatuses | [deviceComplianceDeviceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancedevicestatus?view=graph-rest-beta) collection | List of DeviceComplianceDeviceStatus. |
| userStatuses | [deviceComplianceUserStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuserstatus?view=graph-rest-beta) collection | List of DeviceComplianceUserStatus. |
| deviceStatusOverview | [deviceComplianceDeviceOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancedeviceoverview?view=graph-rest-beta) | Device compliance devices status overview |
| userStatusOverview | [deviceComplianceUserOverview](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecomplianceuseroverview?view=graph-rest-beta) | Device compliance users status overview |
| deviceSettingStateSummaries | [settingStateDeviceSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingstatedevicesummary?view=graph-rest-beta) collection | Compliance Setting State Device Summary |
| assignments | [deviceCompliancePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicyassignment?view=graph-rest-beta) collection | The collection of assignments for this compliance policy. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceCompliancePolicy",
  "roleScopeTagIds": [
    "String"
  ],
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "version": 1024
}
```
