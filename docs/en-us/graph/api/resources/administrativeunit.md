<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-20 -->

# administrativeUnit resource type

Namespace: microsoft.graph

An administrative unit provides a conceptual container for user, group, and device directory objects. With administrative units, a company administrator can now delegate administrative responsibilities to manage the users, groups, and devices contained within or scoped to an administrative unit to a regional or departmental administrator. For more information about administrative units, see [Administrative units in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/administrative-units).

This resource is an open type that allows additional properties beyond those documented here.

This resource supports:

- Adding your own data to custom properties as [extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview).
- Using [delta query](https://learn.microsoft.com/en-us/graph/delta-query-overview) to track incremental additions, deletions, and updates, by providing a [delta](https://learn.microsoft.com/en-us/graph/api/user-delta?view=graph-rest-1.0) function.
- [OData query capabilities](https://learn.microsoft.com/en-us/graph/query-parameters) including `$select`, `$filter`, `$search`, and `$top`. Specific usages are supported only with [Advanced query capabilities](https://learn.microsoft.com/en-us/graph/aad-advanced-queries#group-properties).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/directory-post-administrativeunits?view=graph-rest-1.0) | [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) | Create a new administrative unit. |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-list-administrativeunits?view=graph-rest-1.0) | [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) collection | List properties of all administrativeUnits. |
| [Get](https://learn.microsoft.com/en-us/graph/api/administrativeunit-get?view=graph-rest-1.0) | [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) | Read properties and relationships of a specific administrativeUnit object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/administrativeunit-update?view=graph-rest-1.0) | [administrativeUnit](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) | Update administrativeUnit object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/administrativeunit-delete?view=graph-rest-1.0) | None | Delete administrativeUnit object. |
| **Memberships** |  |  |
| [Add member](https://learn.microsoft.com/en-us/graph/api/administrativeunit-post-members?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Add a member \(user, group, or device\). |
| [List members](https://learn.microsoft.com/en-us/graph/api/administrativeunit-list-members?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Get the list of \(user, group, or device\) members. |
| [Get member](https://learn.microsoft.com/en-us/graph/api/administrativeunit-get-members?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Get a specific member. |
| [Remove member](https://learn.microsoft.com/en-us/graph/api/administrativeunit-delete-members?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Remove a member. |
| **Role assignments** |  |  |
| [List role assignments with scope](https://learn.microsoft.com/en-us/graph/api/administrativeunit-list-scopedrolemembers?view=graph-rest-1.0) | [scopedRoleMembership](https://learn.microsoft.com/en-us/graph/api/resources/scopedrolemembership?view=graph-rest-1.0) collection | List Microsoft Entra role assignments with administrative unit scope. |
| [Assign role with scope](https://learn.microsoft.com/en-us/graph/api/administrativeunit-post-scopedrolemembers?view=graph-rest-1.0) | [scopedRoleMembership](https://learn.microsoft.com/en-us/graph/api/resources/scopedrolemembership?view=graph-rest-1.0) | Assign a Microsoft Entra role with administrative unit scope. |
| [Get role assignment with scope](https://learn.microsoft.com/en-us/graph/api/administrativeunit-get-scopedrolemembers?view=graph-rest-1.0) | [scopedRoleMembership](https://learn.microsoft.com/en-us/graph/api/resources/scopedrolemembership?view=graph-rest-1.0) | Get a Microsoft Entra role assignment with administrative unit scope. |
| [Remove role assignment with scope](https://learn.microsoft.com/en-us/graph/api/administrativeunit-delete-scopedrolemembers?view=graph-rest-1.0) | [scopedRoleMembership](https://learn.microsoft.com/en-us/graph/api/resources/scopedrolemembership?view=graph-rest-1.0) | Remove a Microsoft Entra role assignment with administrative unit scope. |
| **Deleted items** |  |  |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-list?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Retrieve a list of recently deleted administrative units from a collection of directory objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-get?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Retrieve the properties of a recently deleted administrative unit object. |
| [Restore](https://learn.microsoft.com/en-us/graph/api/directory-deleteditems-restore?view=graph-rest-1.0) | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Restore a recently deleted administrative unit object. |

## Properties

Important

Specific usage of `$filter` and the `$search` query parameter is supported only when you use the **ConsistencyLevel** header set to `eventual` and `$count`. For more information, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries#administrative-unit-properties).

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | An optional description for the administrative unit. Supports `$filter` \(`eq`, `ne`, `in`, `startsWith`\), `$search`. |
| displayName | String | Display name for the administrative unit. Maximum length is 256 characters. Supports `$filter` \(`eq`, `ne`, `not`, `ge`, `le`, `in`, `startsWith`, and `eq` on `null` values\), `$search`, and `$orderby`. |
| id | String | Unique identifier for the administrative unit. Read-only. Supports `$filter` \(`eq`\). |
| isMemberManagementRestricted | Boolean | `true` if members of this administrative unit should be treated as sensitive, which requires specific permissions to manage. If not set, the default value is `null` and the default behavior is false. Use this property to define administrative units with roles that don't inherit from tenant-level administrators, and where the management of individual member objects is limited to administrators scoped to a restricted management administrative unit. This property is immutable and can't be changed later.  <br>  <br>For more information on how to work with restricted management administrative units, see [Restricted management administrative units in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-restricted-management). |
| membershipRule | String | The dynamic membership rule for the administrative unit. For more information about the rules you can use for dynamic administrative units and dynamic groups, see [Manage rules for dynamic membership groups in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/users/groups-dynamic-membership). |
| membershipRuleProcessingState | String | Controls whether the dynamic membership rule is actively processed. Set to `On` to activate the dynamic membership rule, or `Paused` to stop updating membership dynamically. |
| membershipType | String | Indicates the membership type for the administrative unit. The possible values are: `dynamic`, `assigned`. If not set, the default value is `null` and the default behavior is assigned. |
| visibility | String | Controls whether the administrative unit and its members are hidden or public. Can be set to `HiddenMembership`. If not set, the default value is `null` and the default behavior is public. When set to `HiddenMembership`, only members of the administrative unit can list other members of the administrative unit. |

Tip

Directory extensions and associated data are returned by default while schema extensions and associated data require `$select` to retrieve.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| members | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | Users and groups that are members of this administrative unit. Supports `$expand`. |
| extensions | [extension](https://learn.microsoft.com/en-us/graph/api/resources/extension?view=graph-rest-1.0) collection | The collection of open extensions defined for this administrative unit. Nullable. |
| scopedRoleMembers | [scopedRoleMembership](https://learn.microsoft.com/en-us/graph/api/resources/scopedrolemembership?view=graph-rest-1.0) collection | Scoped-role members of this administrative unit. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "isMemberManagementRestricted": "Boolean",
  "membershipRule": "String",
  "membershipRuleProcessingState": "String",
  "membershipType": "String",
  "visibility": "String"
}
```

## Related content

- [Add custom data to resources using extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview)
- [Add custom data to users using open extensions](https://learn.microsoft.com/en-us/graph/extensibility-open-users)
- [Add custom data to groups using schema extensions](https://learn.microsoft.com/en-us/graph/extensibility-schema-groups)
