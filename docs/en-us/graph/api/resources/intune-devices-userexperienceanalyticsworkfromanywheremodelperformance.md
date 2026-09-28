<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# userExperienceAnalyticsWorkFromAnywhereModelPerformance resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The user experience analytics work from anywhere model performance.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List userExperienceAnalyticsWorkFromAnywhereModelPerformances](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance-list?view=graph-rest-1.0) | [userExperienceAnalyticsWorkFromAnywhereModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance?view=graph-rest-1.0) collection | List properties and relationships of the [userExperienceAnalyticsWorkFromAnywhereModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance?view=graph-rest-1.0) objects. |
| [Get userExperienceAnalyticsWorkFromAnywhereModelPerformance](https://learn.microsoft.com/en-us/graph/api/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance-get?view=graph-rest-1.0) | [userExperienceAnalyticsWorkFromAnywhereModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance?view=graph-rest-1.0) | Read properties and relationships of the [userExperienceAnalyticsWorkFromAnywhereModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance?view=graph-rest-1.0) object. |
| [Create userExperienceAnalyticsWorkFromAnywhereModelPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance-create.md?view=graph-rest-1.0) | [userExperienceAnalyticsWorkFromAnywhereModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance?view=graph-rest-1.0) | Create a new [userExperienceAnalyticsWorkFromAnywhereModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance?view=graph-rest-1.0) object. |
| [Delete userExperienceAnalyticsWorkFromAnywhereModelPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance-delete.md?view=graph-rest-1.0) | None | Deletes a [userExperienceAnalyticsWorkFromAnywhereModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance?view=graph-rest-1.0). |
| [Update userExperienceAnalyticsWorkFromAnywhereModelPerformance](https://learn.microsoft.com/en-us/graph/api/api/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance-update.md?view=graph-rest-1.0) | [userExperienceAnalyticsWorkFromAnywhereModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance?view=graph-rest-1.0) | Update the properties of a [userExperienceAnalyticsWorkFromAnywhereModelPerformance](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticsworkfromanywheremodelperformance?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the work from anywhere model performance object. Supports: $select, $OrderBy. Read-only. |
| model | String | The model name of the device. Supports: $select, $OrderBy. Read-only. |
| manufacturer | String | The manufacturer name of the device. Supports: $select, $OrderBy. Read-only. |
| modelDeviceCount | Int32 | The devices count for the model. Supports: $select, $OrderBy. Read-only. Valid values -2147483648 to 2147483647 |
| workFromAnywhereScore | Double | The work from anywhere score of the device model. Valid values 0 to 100. Value -1 means associated score is unavailable. Supports: $select, $OrderBy. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| windowsScore | Double | The window score of the device model. Valid values 0 to 100. Value -1 means associated score is unavailable. Supports: $select, $OrderBy. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| cloudManagementScore | Double | The cloud management score of the device model. Valid values 0 to 100. Value -1 means associated score is unavailable. Supports: $select, $OrderBy. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| cloudIdentityScore | Double | The cloud identity score of the device model. Valid values 0 to 100. Value -1 means associated score is unavailable. Supports: $select, $OrderBy. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| cloudProvisioningScore | Double | The cloud provisioning score of the device model. Valid values 0 to 100. Value -1 means associated score is unavailable. Supports: $select, $OrderBy. Read-only. Valid values -1.79769313486232E+308 to 1.79769313486232E+308 |
| healthStatus | [userExperienceAnalyticsHealthState](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-userexperienceanalyticshealthstate?view=graph-rest-1.0) | The health state of the user experience analytics work from anywhere device model. The possible values are: unknown, insufficientData, needsAttention, meetingGoals. Unknown by default. Supports: $select, $OrderBy. Read-only. The possible values are: `unknown`, `insufficientData`, `needsAttention`, `meetingGoals`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.userExperienceAnalyticsWorkFromAnywhereModelPerformance",
  "id": "String (identifier)",
  "model": "String",
  "manufacturer": "String",
  "modelDeviceCount": 1024,
  "workFromAnywhereScore": "4.2",
  "windowsScore": "4.2",
  "cloudManagementScore": "4.2",
  "cloudIdentityScore": "4.2",
  "cloudProvisioningScore": "4.2",
  "healthStatus": "String"
}
```
