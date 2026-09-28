<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeploymentprofileassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsAutopilotDeploymentProfileAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

An assignment of a Windows Autopilot deployment profile to an AAD group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsAutopilotDeploymentProfileAssignments](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotdeploymentprofileassignment-list?view=graph-rest-beta) | [windowsAutopilotDeploymentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeploymentprofileassignment?view=graph-rest-beta) collection | List properties and relationships of the [windowsAutopilotDeploymentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeploymentprofileassignment?view=graph-rest-beta) objects. |
| [Get windowsAutopilotDeploymentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotdeploymentprofileassignment-get?view=graph-rest-beta) | [windowsAutopilotDeploymentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeploymentprofileassignment?view=graph-rest-beta) | Read properties and relationships of the [windowsAutopilotDeploymentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeploymentprofileassignment?view=graph-rest-beta) object. |
| [Create windowsAutopilotDeploymentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotdeploymentprofileassignment-create?view=graph-rest-beta) | [windowsAutopilotDeploymentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeploymentprofileassignment?view=graph-rest-beta) | Create a new [windowsAutopilotDeploymentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeploymentprofileassignment?view=graph-rest-beta) object. |
| [Delete windowsAutopilotDeploymentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotdeploymentprofileassignment-delete?view=graph-rest-beta) | None | Deletes a [windowsAutopilotDeploymentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeploymentprofileassignment?view=graph-rest-beta). |
| [Update windowsAutopilotDeploymentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotdeploymentprofileassignment-update?view=graph-rest-beta) | [windowsAutopilotDeploymentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeploymentprofileassignment?view=graph-rest-beta) | Update the properties of a [windowsAutopilotDeploymentProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotdeploymentprofileassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The key of the assignment. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The assignment target for the Windows Autopilot deployment profile. |
| source | [deviceAndAppManagementAssignmentSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmentsource?view=graph-rest-beta) | Type of resource used for deployment to a group, direct or parcel/policySet. Possible values are: `direct`, `policySets`. |
| sourceId | String | Identifier for resource used for deployment to a group |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsAutopilotDeploymentProfileAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.deviceAndAppManagementAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String"
  },
  "source": "String",
  "sourceId": "String"
}
```
