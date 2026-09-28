<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetagautoassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# roleScopeTagAutoAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains the properties for auto-assigning a Role Scope Tag to a group to be applied to Devices.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List roleScopeTagAutoAssignments](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolescopetagautoassignment-list?view=graph-rest-beta) | [roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetagautoassignment?view=graph-rest-beta) collection | List properties and relationships of the [roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetagautoassignment?view=graph-rest-beta) objects. |
| [Get roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolescopetagautoassignment-get?view=graph-rest-beta) | [roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetagautoassignment?view=graph-rest-beta) | Read properties and relationships of the [roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetagautoassignment?view=graph-rest-beta) object. |
| [Create roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolescopetagautoassignment-create?view=graph-rest-beta) | [roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetagautoassignment?view=graph-rest-beta) | Create a new [roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetagautoassignment?view=graph-rest-beta) object. |
| [Delete roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolescopetagautoassignment-delete?view=graph-rest-beta) | None | Deletes a [roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetagautoassignment?view=graph-rest-beta). |
| [Update roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolescopetagautoassignment-update?view=graph-rest-beta) | [roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetagautoassignment?view=graph-rest-beta) | Update the properties of a [roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetagautoassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This property is read-only. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The auto-assignment target for the specific Role Scope Tag. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.roleScopeTagAutoAssignment",
  "id": "String (identifier)",
  "target": {
    "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String",
    "targetType": "String",
    "entraObjectId": "String"
  }
}
```
