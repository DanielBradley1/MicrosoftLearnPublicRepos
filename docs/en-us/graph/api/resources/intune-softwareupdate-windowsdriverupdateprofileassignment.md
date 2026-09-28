<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofileassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsDriverUpdateProfileAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

This entity contains the properties used to assign a windows driver update profile to a group.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsDriverUpdateProfileAssignments](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateprofileassignment-list?view=graph-rest-beta) | [windowsDriverUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofileassignment?view=graph-rest-beta) collection | List properties and relationships of the [windowsDriverUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofileassignment?view=graph-rest-beta) objects. |
| [Get windowsDriverUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateprofileassignment-get?view=graph-rest-beta) | [windowsDriverUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofileassignment?view=graph-rest-beta) | Read properties and relationships of the [windowsDriverUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofileassignment?view=graph-rest-beta) object. |
| [Create windowsDriverUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateprofileassignment-create?view=graph-rest-beta) | [windowsDriverUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofileassignment?view=graph-rest-beta) | Create a new [windowsDriverUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofileassignment?view=graph-rest-beta) object. |
| [Delete windowsDriverUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateprofileassignment-delete?view=graph-rest-beta) | None | Deletes a [windowsDriverUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofileassignment?view=graph-rest-beta). |
| [Update windowsDriverUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsdriverupdateprofileassignment-update?view=graph-rest-beta) | [windowsDriverUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofileassignment?view=graph-rest-beta) | Update the properties of a [windowsDriverUpdateProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsdriverupdateprofileassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The Identifier of the entity |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The assignment target that the driver update profile is assigned to. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsDriverUpdateProfileAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.deviceAndAppManagementAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String"
  }
}
```
