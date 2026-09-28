<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevice?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-13 -->

# userExperienceAnalyticsWorkFromAnywhereDevice resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics device for work from anywhere report.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsWorkFromAnywhereDevices](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsworkfromanywheredevice-list?view=graph-rest-1.0) | [userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevice?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevice?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsworkfromanywheredevice-get?view=graph-rest-1.0) | [userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevice?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevice?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsworkfromanywheredevice-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevice?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevice?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsworkfromanywheredevice-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevice?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsworkfromanywheredevice-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevice?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsWorkFromAnywhereDevice](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheredevice?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the user experience analytics work from anywhere device. Supports: $select, $OrderBy. Read-only. |
| deviceId | String | The Intune device id of the device. Supports: $select, $OrderBy. Read-only. |
| deviceName | String | The name of the device. Supports: $select, $OrderBy. Read-only. |
| serialNumber | String | The serial number of the device. Supports: $select, $OrderBy. Read-only. |
| manufacturer | String | The manufacturer name of the device. Supports: $select, $OrderBy. Read-only. |
| model | String | The model name of the device. Supports: $select, $OrderBy. Read-only. |
| ownership | String | Ownership of the device. Supports: $select, $OrderBy. Read-only. |
| managedBy | String | The management agent of the device. Supports: $select, $OrderBy. Read-only. |
| autoPilotRegistered | Boolean | When TRUE, indicates the intune device's autopilot is registered. When FALSE, indicates it's not registered. Supports: $select, $OrderBy. Read-only. |
| autoPilotProfileAssigned | Boolean | When TRUE, indicates the intune device's autopilot profile is assigned. When FALSE, indicates it's not Assigned. Supports: $select, $OrderBy. Read-only. |
| azureAdRegistered | Boolean | When TRUE, indicates the device's Azure Active Directory \(Azure AD\) is registered. When False, indicates it's not registered. Supports: $select, $OrderBy. Read-only. |
| azureAdDeviceId | String | The Azure Active Directory \(Azure AD\) device Id. Supports: $select, $OrderBy. Read-only. |
| azureAdJoinType | String | The work from anywhere device's Azure Active Directory \(Azure AD\) join type. Supports: $select, $OrderBy. Read-only. |
| osDescription | String | The OS description of the device. Supports: $select, $OrderBy. Read-only. |
| osVersion | String | The OS version of the device. Supports: $select, $OrderBy. Read-only. |
| tenantAttached | Boolean | When TRUE, indicates the device is Tenant Attached. When FALSE, indicates it's not Tenant Attached. Supports: $select, $OrderBy. Read-only. |
| compliancePolicySetToIntune | Boolean | When TRUE, indicates the device's compliance policy is set to intune. When FALSE, indicates it's not set to intune. Supports: $select, $OrderBy. Read-only. |
| otherWorkloadsSetToIntune | Boolean | When TRUE, indicates the device's other workloads is set to intune. When FALSE, indicates it's not set to intune. Supports: $select, $OrderBy. Read-only. |
| isCloudManagedGatewayEnabled | Boolean | When TRUE, indicates the device's Cloud Management Gateway for Configuration Manager is enabled. When FALSE, indicates it's not enabled. Supports: $select, $OrderBy. Read-only. |
| upgradeEligibility | [operatingSystemUpgradeEligibility](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-operatingsystemupgradeeligibility?view=graph-rest-1.0) | The windows upgrade eligibility status of device. The possible values are: upgraded, unknown, notCapable, capable. Unknown by default. Supports: $select, $OrderBy. Read-only. The possible values are: `upgraded`, `unknown`, `notCapable`, `capable`, `unknownFutureValue`. |
| ramCheckFailed | Boolean | When TRUE, indicates RAM hardware check failed for device to upgrade to the latest version of windows. When FALSE, indicates the check succeeded. Supports: $select, $OrderBy. Read-only. |
| storageCheckFailed | Boolean | When TRUE, indicates storage hardware check failed for device to upgrade to the latest version of windows. When FALSE, indicates the check succeeded. Supports: $select, $OrderBy. Read-only. |
| processorCoreCountCheckFailed | Boolean | When TRUE, indicates processor hardware core count check failed for device to upgrade to the latest version of windows. When FALSE, indicates the check succeeded. Supports: $select, $OrderBy. Read-only. |
| processorSpeedCheckFailed | Boolean | When TRUE, indicates processor hardware speed check failed for device to upgrade to the latest version of windows. When FALSE, indicates the check succeeded. Supports: $select, $OrderBy. Read-only. |
| tpmCheckFailed | Boolean | When TRUE, indicates Trusted Platform Module \(TPM\) hardware check failed for device to the latest version of upgrade to windows. When FALSE, indicates the check succeeded. Supports: $select, $OrderBy. Read-only. |
| secureBootCheckFailed | Boolean | When TRUE, indicates secure boot hardware check failed for device to upgrade to the latest version of windows. When FALSE, indicates the check succeeded. Supports: $select, $OrderBy. Read-only. |
| processorFamilyCheckFailed | Boolean | When TRUE, indicates processor hardware family check failed for device to upgrade to the latest version of windows. When FALSE, indicates the check succeeded. Supports: $select, $OrderBy. Read-only. |
| processor64BitCheckFailed | Boolean | When TRUE, indicates processor hardware 64-bit architecture check failed for device to upgrade to the latest version of windows. When FALSE, indicates the check succeeded. Supports: $select, $OrderBy. Read-only. |
| osCheckFailed | Boolean | When TRUE, indicates OS check failed for device to upgrade to the latest version of windows. When FALSE, indicates the check succeeded. Supports: $select, $OrderBy. Read-only. |
| workFromAnywhereScore | Double | Indicates work from anywhere per device overall score. Valid values 0 to 100. Value -1 means associated score is unavailable. Supports: $select, $OrderBy. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| windowsScore | Double | Indicates per device windows score. Valid values 0 to 100. Value -1 means associated score is unavailable. Supports: $select, $OrderBy. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| cloudManagementScore | Double | Indicates per device cloud management score. Valid values 0 to 100. Value -1 means associated score is unavailable. Supports: $select, $OrderBy. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| cloudIdentityScore | Double | Indicates per device cloud identity score. Valid values 0 to 100. Value -1 means associated score is unavailable. Supports: $select, $OrderBy. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| cloudProvisioningScore | Double | Indicates per device cloud provisioning score. Valid values 0 to 100. Value -1 means associated score is unavailable. Supports: $select, $OrderBy. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| healthStatus | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-1.0) | The health state of the user experience analytics work from anywhere device. The possible values are: unknown, insufficientData, needsAttention, meetingGoals. Unknown by default. Supports: $select, $OrderBy. Read-only. The possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsWorkFromAnywhereDevice",
  "id": "String (identifier)",
  "deviceId": "String",
  "deviceName": "String",
  "serialNumber": "String",
  "manufacturer": "String",
  "model": "String",
  "ownership": "String",
  "managedBy": "String",
  "autoPilotRegistered": true,
  "autoPilotProfileAssigned": true,
  "azureAdRegistered": true,
  "azureAdDeviceId": "String",
  "azureAdJoinType": "String",
  "osDescription": "String",
  "osVersion": "String",
  "tenantAttached": true,
  "compliancePolicySetToIntune": true,
  "otherWorkloadsSetToIntune": true,
  "isCloudManagedGatewayEnabled": true,
  "upgradeEligibility": "String",
  "ramCheckFailed": true,
  "storageCheckFailed": true,
  "processorCoreCountCheckFailed": true,
  "processorSpeedCheckFailed": true,
  "tpmCheckFailed": true,
  "secureBootCheckFailed": true,
  "processorFamilyCheckFailed": true,
  "processor64BitCheckFailed": true,
  "osCheckFailed": true,
  "workFromAnywhereScore": "4.2",
  "windowsScore": "4.2",
  "cloudManagementScore": "4.2",
  "cloudIdentityScore": "4.2",
  "cloudProvisioningScore": "4.2",
  "healthStatus": "String"
}
```
