<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentmultiple?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-13 -->

# unifiedRoleAssignmentMultiple resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A unifiedRoleAssignmentMultiple is used to grant access to resources, as part of Microsoft 365 role-based access control \(RBAC\). It represents a role definition assigned to an array of principals \(typically users\) over an array of scopes.

You can create a role assignment with multiple principals and multiple scopes.

You must provide either **directoryScopeIds** or **appScopeIds**.

The following RBAC providers are currently supported:

- Cloud PC
- Microsoft Intune

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/rbacapplicationmultiple-list-roleassignments?view=graph-rest-beta) | [unifiedRoleAssignmentMultiple](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentmultiple?view=graph-rest-beta) collection | Read a list of **unifiedRoleAssignmentMultiple** objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/rbacapplicationmultiple-post-roleassignments?view=graph-rest-beta) | [unifiedRoleAssignmentMultiple](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentmultiple?view=graph-rest-beta) | Create a new **unifiedRoleAssignmentMultiple** by posting to the **roleAssignment** collection. |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignmentmultiple-get?view=graph-rest-beta) | [unifiedRoleAssignmentMultiple](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentmultiple?view=graph-rest-beta) | Read properties and relationships of **unifiedRoleAssignmentMultiple** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignmentmultiple-update?view=graph-rest-beta) | [unifiedRoleAssignmentMultiple](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentmultiple?view=graph-rest-beta) | Update an existing **unifiedRoleAssignmentMultiple** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/unifiedroleassignmentmultiple-delete?view=graph-rest-beta) | None | Delete **unifiedRoleAssignmentMultiple** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appScopeIds | String collection | Ids of the app specific scopes when the assignment scopes are app specific. The scopes of an assignment determine the set of resources for which the principal has access. Directory scopes are shared scopes stored in the directory that are understood by multiple applications. Use `/` for tenant-wide scope. App scopes are scopes that are defined and understood by this application only. |
| description | String | Description of the role assignment. |
| directoryScopeIds | String collection | Ids of the directory objects that represent the scopes of the assignment. The scopes of an assignment determine the set of resources for which the principals have been granted access. Directory scopes are shared scopes stored in the directory that are understood by multiple applications. App scopes are scopes that are defined and understood by this application only. |
| displayName | String | Name of the role assignment. Required. |
| id | String | The unique identifier for the **unifiedRoleAssignmentMultiple** object. Key, not nullable, Read-only. |
| principalIds | String collection | Identifiers of the principals to which the assignment is granted. Supports `$filter` \(`any` operator only\). |
| roleDefinitionId | String | Identifier of the [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) the assignment is for. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| appScopes | [appScope](https://learn.microsoft.com/en-us/graph/api/resources/appscope?view=graph-rest-beta) collection | Read-only collection with details of the app specific scopes when the assignment scopes are app specific. Containment entity. Read-only. |
| directoryScopes | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) collection | Read-only collection that references the directory objects that are scope of the assignment. Provided so that callers can get the directory objects using `$expand` at the same time as getting the role assignment. Read-only. Supports `$expand`. |
| principals | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) collection | Read-only collection that references the assigned principals. Provided so that callers can get the principals using `$expand` at the same time as getting the role assignment. Read-only. Supports `$expand`. |
| roleDefinition | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) | Specifies the **roleDefinition** that the assignment is for. Provided so that callers can get the role definition using `$expand` at the same time as getting the role assignment. Supports `$filter` \(`eq` operator on **id**, **isBuiltIn**, and **displayName**, and `startsWith` operator on **displayName**\) and `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "appScopeIds": ["string"],
  "appScopes": [{"@odata.type": "microsoft.graph.appScope"}],
  "description": "String",
  "directoryScopeIds": ["String"],
  "directoryScopes": [{"@odata.type": "microsoft.graph.directoryObject"}],
  "displayName": "String",
  "id": "String (identifier)",
  "principalIds": ["String"],
  "principals": [{"@odata.type": "microsoft.graph.directoryObject"}],
  "roleDefinition": {"@odata.type": "microsoft.graph.unifiedRoleDefinition"},
  "roleDefinitionId": "String"
}
```
