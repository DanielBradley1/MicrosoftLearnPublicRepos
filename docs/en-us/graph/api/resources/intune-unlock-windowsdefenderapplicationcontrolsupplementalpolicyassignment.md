<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsDefenderApplicationControlSupplementalPolicyAssignment resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A class containing the properties used for assignment of a WindowsDefenderApplicationControl supplemental policy to a group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsDefenderApplicationControlSupplementalPolicyAssignments](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment-list?view=graph-rest-1.0) | [windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment?view=graph-rest-1.0) collection | List properties and relationships of the [windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment?view=graph-rest-1.0) objects. |
| [Get windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment-get?view=graph-rest-1.0) | [windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment?view=graph-rest-1.0) | Read properties and relationships of the [windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment?view=graph-rest-1.0) object. |
| [Create windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment-create?view=graph-rest-1.0) | [windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment?view=graph-rest-1.0) | Create a new [windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment?view=graph-rest-1.0) object. |
| [Delete windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment-delete?view=graph-rest-1.0) | None | Deletes a [windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment?view=graph-rest-1.0). |
| [Update windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment-update?view=graph-rest-1.0) | [windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment?view=graph-rest-1.0) | Update the properties of a [windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-1.0) | The target group assignment defined by the admin. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsDefenderApplicationControlSupplementalPolicyAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.deviceAndAppManagementAssignmentTarget"
  }
}
```
