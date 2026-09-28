<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetag?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# roleScopeTag resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Role Scope Tag

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List roleScopeTags](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolescopetag-list?view=graph-rest-beta) | [roleScopeTag](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetag?view=graph-rest-beta) collection | List properties and relationships of the [roleScopeTag](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetag?view=graph-rest-beta) objects. |
| [Get roleScopeTag](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolescopetag-get?view=graph-rest-beta) | [roleScopeTag](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetag?view=graph-rest-beta) | Read properties and relationships of the [roleScopeTag](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetag?view=graph-rest-beta) object. |
| [Create roleScopeTag](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolescopetag-create?view=graph-rest-beta) | [roleScopeTag](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetag?view=graph-rest-beta) | Create a new [roleScopeTag](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetag?view=graph-rest-beta) object. |
| [Delete roleScopeTag](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolescopetag-delete?view=graph-rest-beta) | None | Deletes a [roleScopeTag](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetag?view=graph-rest-beta). |
| [Update roleScopeTag](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolescopetag-update?view=graph-rest-beta) | [roleScopeTag](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetag?view=graph-rest-beta) | Update the properties of a [roleScopeTag](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetag?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolescopetag-assign?view=graph-rest-beta) | [roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetagautoassignment?view=graph-rest-beta) collection |  |
| [getRoleScopeTagsById action](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolescopetag-getrolescopetagsbyid?view=graph-rest-beta) | [roleScopeTag](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetag?view=graph-rest-beta) collection |  |
| [hasCustomRoleScopeTag function](https://learn.microsoft.com/en-us/graph/api/intune-rbac-rolescopetag-hascustomrolescopetag?view=graph-rest-beta) | Boolean |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This is read-only and automatically generated. This property is read-only. |
| displayName | String | The display or friendly name of the Role Scope Tag. |
| description | String | Description of the Role Scope Tag. |
| isBuiltIn | Boolean | Description of the Role Scope Tag. This property is read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [roleScopeTagAutoAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-rolescopetagautoassignment?view=graph-rest-beta) collection | The list of assignments for this Role Scope Tag. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.roleScopeTag",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "isBuiltIn": true
}
```
