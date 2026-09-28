<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/directoryrole?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-19 -->

# directoryRole resource type

Namespace: microsoft.graph

Note

Microsoft recommends that you use the unified RBAC API instead of this API. The unified RBAC API provides more functionality and flexibility. For more information, see [unifiedRoleDefinition resource type](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0).

Represents a Microsoft Entra directory role. Microsoft Entra directory roles are also known as *administrator roles*. For more information about directory \(administrator\) roles, see [Assigning Microsoft Entra administrator roles](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-assign-admin-roles). With the Microsoft Graph, you can assign users to directory roles to grant them the permissions of the target role. To read a directory role or update its members, it must first be activated in the tenant. Only the Company Administrators directory role is activated by default. To activate other available directory roles you send a POST request with the ID of the [directoryRoleTemplate](https://learn.microsoft.com/en-us/graph/api/resources/directoryroletemplate?view=graph-rest-1.0) on which the directory role is based. [List directory role templates](https://learn.microsoft.com/en-us/graph/api/directoryroletemplate-list?view=graph-rest-1.0) to get all the other available directory roles. Inherits from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0).

This resource supports:

- Using [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview) to track incremental additions, deletions, and updates, by providing a [delta](https://learn.microsoft.com/en-us/graph/api/directoryrole-delta?view=graph-rest-1.0) function.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get directory role](https://learn.microsoft.com/en-us/graph/api/directoryrole-get?view=graph-rest-1.0) | [directoryRole](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole?view=graph-rest-1.0) | Read properties and relationships of directoryRole object. |
| [List directory roles](https://learn.microsoft.com/en-us/graph/api/directoryrole-list?view=graph-rest-1.0) | [directoryRole](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole?view=graph-rest-1.0) collection | List the directory roles that are activated in the tenant. |
| [Add member](https://learn.microsoft.com/en-us/graph/api/directoryrole-post-members?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Add a user to the directory role by posting to the members navigation property. |
| [List members](https://learn.microsoft.com/en-us/graph/api/directoryrole-list-members?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the users that are members of the directory role from the members navigation property. |
| [Remove member](https://learn.microsoft.com/en-us/graph/api/directoryrole-delete-member?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Remove a user from the directory role. |
| [Activate directory role](https://learn.microsoft.com/en-us/graph/api/directoryrole-post-directoryroles?view=graph-rest-1.0) | [directoryRole](https://learn.microsoft.com/en-us/graph/api/resources/directoryrole?view=graph-rest-1.0) | Activate a directory role. |
| [List scoped members](https://learn.microsoft.com/en-us/graph/api/directoryrole-list-scopedmembers?view=graph-rest-1.0) | [scopedRoleMembership](https://learn.microsoft.com/en-us/graph/api/resources/scopedrolemembership?view=graph-rest-1.0) collection | List the members of this directory role that are scoped to [administrative units](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0), through the scopedRoleMembership resource collection. |
| [Get delta](https://learn.microsoft.com/en-us/graph/api/directoryrole-delta?view=graph-rest-1.0) | directoryRole collection | Get incremental changes for directory roles. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description for the directory role. Read-only. Supports `$filter` \(`eq`\), `$search`, `$select`. |
| displayName | String | The display name for the directory role. Read-only. Supports `$filter` \(`eq`\), `$search`, `$select`. |
| id | String | The unique identifier for the directory role. Inherited from [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0). Key, Not nullable, Read-only. Supports `$filter` \(`eq`\), `$select`. |
| roleTemplateId | String | The **id** of the [directoryRoleTemplate](https://learn.microsoft.com/en-us/graph/api/resources/directoryroletemplate?view=graph-rest-1.0) that this role is based on. The property must be specified when activating a directory role in a tenant with a POST operation. After the directory role has been activated, the property is read-only. Supports `$filter` \(`eq`\), `$select`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| members | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Users that are members of this directory role. HTTP Methods: GET, POST, DELETE. Read-only. Nullable. Supports `$expand`. |
| scopedMembers | [scopedRoleMembership](https://learn.microsoft.com/en-us/graph/api/resources/scopedrolemembership?view=graph-rest-1.0) collection | Members of this directory role that are scoped to [administrative units](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0). Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "string",
  "displayName": "string",
  "id": "string (identifier)",
  "roleTemplateId": "string"
}
```
