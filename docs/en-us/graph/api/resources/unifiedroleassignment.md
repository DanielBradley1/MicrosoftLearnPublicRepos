<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-30 -->

# unifiedRoleAssignment resource type

Namespace: microsoft.graph

Represents a role definition assigned to a principal at a particular scope. Supported principals are users, role-assignable groups, and service principals.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roleassignments?view=graph-rest-1.0) | [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-1.0) collection | Get a list of the [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleassignments?view=graph-rest-1.0) | [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-1.0) | Create a new [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignment-get?view=graph-rest-1.0) | [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-1.0) | Read the properties and relationships of an [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignment-delete?view=graph-rest-1.0) | None | Deletes an [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appScopeId | String | Identifier of the app specific scope when the assignment scope is app specific. The scope of an assignment determines the set of resources for which the principal has been granted access. App scopes are scopes that are defined and understood by a resource application only. For the entitlement management provider, use this property to specify a catalog. For example, `/AccessPackageCatalog/beedadfe-01d5-4025-910b-84abb9369997`. Supports `$filter` \(`eq`, `in`\). For example, `/roleManagement/entitlementManagement/roleAssignments?$filter=appScopeId eq '/AccessPackageCatalog/{catalog id}'`. |
| directoryScopeId | String | Identifier of the [directory object](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) representing the scope of the assignment. The scope of an assignment determines the set of resources for which the principal has been granted access. Directory scopes are shared scopes stored in the directory that are understood by multiple applications, unlike app scopes that are defined and understood by a resource application only. Supports `$filter` \(`eq`, `in`\). |
| id | String | The unique identifier for the unifiedRoleAssignment. Key, not nullable, Read-only. |
| principalId | String | Identifier of the principal to which the assignment is granted. Supported principals are users, role-assignable groups, and service principals. Supports `$filter` \(`eq`, `in`\). |
| roleDefinitionId | String | Identifier of the unifiedRoleDefinition the assignment is for. Read-only. Supports `$filter` \(`eq`, `in`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appScope | [appScope](https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-1.0) | Read-only property with details of the app specific scope when the assignment scope is app specific. Containment entity. Supports `$expand` for the entitlement provider only. |
| directoryScope | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | The directory object that is the scope of the assignment. Read-only. Supports `$expand` for the directory provider. |
| principal | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) | Referencing the assigned principal. Read-only. Supports `$expand` except for the Exchange provider. |
| roleDefinition | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-1.0) | The roleDefinition the assignment is for. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoleAssignment",
  "id": "String (identifier)",
  "appScopeId": "String",
  "directoryScopeId": "String",
  "principalId": "String",
  "roleDefinitionId": "String"
}
```
