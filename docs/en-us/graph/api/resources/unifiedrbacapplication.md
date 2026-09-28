<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacapplication?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# unifiedRbacApplication resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a role management container for unified role definitions and role assignments for role-based access control \(RBAC\) providers in Microsoft 365. This is a shared entity meant to replace [rbacApplication](https://learn.microsoft.com/en-us/graph/api/resources/rbacapplication?view=graph-rest-beta). Currently only Exchange RBAC applications are supported.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create role assignment](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roleassignments?view=graph-rest-beta) | [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-beta) | Create a new [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-beta) object. |
| [List role assignment](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roleassignments?view=graph-rest-beta) | [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-beta) collection | Get a list of [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-beta) objects for an RBAC provider. You can only query specific instances by filtering on **roleDefinitionId**, **principalId** or **appScopeId**. |
| [List transitive role assignments](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-transitiveroleassignments?view=graph-rest-beta) | [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-beta) collection | Get the list of direct and transitive [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-beta) objects for a specific principal. This API requires the **principalId** in a request. |
| [Create role definition](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roledefinitions?view=graph-rest-beta) | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) | Create a new [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) object for an RBAC provider. |
| [List role definitions](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roledefinitions?view=graph-rest-beta) | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) collection | Get a list of [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) objects for an RBAC provider. |
| [List](https://learn.microsoft.com/en-us/graph/api/unifiedrbacapplication-list-customappscopes?view=graph-rest-beta) | [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) collection | Get a list of [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) objects for an RBAC provider. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customAppScopes | [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) collection | Workload-specific scope object that represents the resources for which the principal has been granted access. |
| resourceNamespaces | [unifiedRbacResourceNamespace](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacresourcenamespace?view=graph-rest-beta) collection | Resource that represents a collection of related actions. |
| roleAssignments | [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-beta) collection | Resource to grant access to users or groups. |
| roleDefinitions | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) collection | The roles allowed by RBAC providers and the permissions assigned to the roles. |
| transitiveRoleAssignments | [unifiedRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignment?view=graph-rest-beta) collection | Resource to grant access to users or groups that are transitive. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRbacApplication"
}
```
