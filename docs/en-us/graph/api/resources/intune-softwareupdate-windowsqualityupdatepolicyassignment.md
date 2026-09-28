<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicyassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsQualityUpdatePolicyAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This entity contains the properties used to assign a Windows quality update policy to a group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsQualityUpdatePolicyAssignments](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatepolicyassignment-list?view=graph-rest-beta) | [windowsQualityUpdatePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicyassignment?view=graph-rest-beta) collection | List properties and relationships of the [windowsQualityUpdatePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicyassignment?view=graph-rest-beta) objects. |
| [Get windowsQualityUpdatePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatepolicyassignment-get?view=graph-rest-beta) | [windowsQualityUpdatePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicyassignment?view=graph-rest-beta) | Read properties and relationships of the [windowsQualityUpdatePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicyassignment?view=graph-rest-beta) object. |
| [Create windowsQualityUpdatePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatepolicyassignment-create?view=graph-rest-beta) | [windowsQualityUpdatePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicyassignment?view=graph-rest-beta) | Create a new [windowsQualityUpdatePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicyassignment?view=graph-rest-beta) object. |
| [Delete windowsQualityUpdatePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatepolicyassignment-delete?view=graph-rest-beta) | None | Deletes a [windowsQualityUpdatePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicyassignment?view=graph-rest-beta). |
| [Update windowsQualityUpdatePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatepolicyassignment-update?view=graph-rest-beta) | [windowsQualityUpdatePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicyassignment?view=graph-rest-beta) | Update the properties of a [windowsQualityUpdatePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicyassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The id for CloudQualityUpdateProfileAssignment entity. This id is assigned when assigning the profile to a group. Read-only |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The assignment target that the Windows quality update policy is assigned to. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsQualityUpdatePolicyAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.deviceAndAppManagementAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String"
  }
}
```
