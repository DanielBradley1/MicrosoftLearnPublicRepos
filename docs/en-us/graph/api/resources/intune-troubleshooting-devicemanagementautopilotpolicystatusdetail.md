<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementAutopilotPolicyStatusDetail resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Policy status detail item contained by an autopilot event.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementAutopilotPolicyStatusDetails](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail-list?view=graph-rest-beta) | [deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail?view=graph-rest-beta) objects. |
| [Get deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail-get?view=graph-rest-beta) | [deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail?view=graph-rest-beta) object. |
| [Create deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail-create?view=graph-rest-beta) | [deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail?view=graph-rest-beta) | Create a new [deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail?view=graph-rest-beta) object. |
| [Delete deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail?view=graph-rest-beta). |
| [Update deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail-update?view=graph-rest-beta) | [deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail?view=graph-rest-beta) | Update the properties of a [deviceManagementAutopilotPolicyStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicystatusdetail?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | UUID for the object |
| displayName | String | The friendly name of the policy. |
| policyType | [deviceManagementAutopilotPolicyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicytype?view=graph-rest-beta) | The type of policy. The possible values are: `unknown`, `application`, `appModel`, `configurationPolicy`. |
| complianceStatus | [deviceManagementAutopilotPolicyComplianceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-troubleshooting-devicemanagementautopilotpolicycompliancestatus?view=graph-rest-beta) | The policy compliance or enforcement status. Enforcement status takes precedence if it exists. The possible values are: `unknown`, `compliant`, `installed`, `notCompliant`, `notInstalled`, `error`. |
| trackedOnEnrollmentStatus | Boolean | Indicates if this policy was tracked as part of the autopilot bootstrap enrollment sync session |
| lastReportedDateTime | DateTimeOffset | Timestamp of the reported policy status |
| errorCode | Int32 | The errorode associated with the compliance or enforcement status of the policy. Error code for enforcement status takes precedence if it exists. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementAutopilotPolicyStatusDetail",
  "id": "String (identifier)",
  "displayName": "String",
  "policyType": "String",
  "complianceStatus": "String",
  "trackedOnEnrollmentStatus": true,
  "lastReportedDateTime": "String (timestamp)",
  "errorCode": 1024
}
```
