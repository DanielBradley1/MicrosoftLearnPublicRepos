<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/rbacapplicationmultiple?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# rbacApplicationMultiple resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Role management container for unified role definitions and role assignments for Microsoft 365 RBAC providers that support multiple principals and multiple scopes in a single role assignment. This is different from the [rbacApplication](https://learn.microsoft.com/en-us/graph/api/resources/rbacapplication?view=graph-rest-beta) resource type.

Cloud PC and Microsoft Intune are examples of such RBAC providers. A role assignment in these providers can have an array of principals and an array of scope groups.

For role definitions, the cloud PC provider currently supports the [list](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roledefinitions?view=graph-rest-beta) operation but not the [create](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roledefinitions?view=graph-rest-beta).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create role definition](https://learn.microsoft.com/en-us/graph/api/rbacapplication-post-roledefinitions?view=graph-rest-beta) | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) | Create a new unifiedRoleDefinition by posting to the roleDefinitions collection. |
| [List role definitions](https://learn.microsoft.com/en-us/graph/api/rbacapplication-list-roledefinitions?view=graph-rest-beta) | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) collection | Get a unifiedRoleDefinition object collection. |
| [Create](https://learn.microsoft.com/en-us/graph/api/rbacapplicationmultiple-post-roleassignments?view=graph-rest-beta) | [unifiedRoleAssignmentMultiple](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentmultiple?view=graph-rest-beta) | Create a new unifiedRoleAssignmentMultiple by posting to the roleAssignments collection. |
| [List](https://learn.microsoft.com/en-us/graph/api/rbacapplicationmultiple-list-roleassignments?view=graph-rest-beta) | [unifiedRoleAssignmentMultiple](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentmultiple?view=graph-rest-beta) collection | Get unifiedRoleAssignmentMultiple object collection. |

## Properties

None

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| resourceNamespaces | [unifiedRbacResourceNamespace](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacresourcenamespace?view=graph-rest-beta) collection | Resource that represents a collection of related actions. |
| roleAssignments | [unifiedRoleAssignmentMultiple](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentmultiple?view=graph-rest-beta) collection | Resource to grant access to users or groups. |
| roleDefinitions | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) collection | Resource representing the roles allowed by RBAC providers and the permissions assigned to the roles. |

## JSON representation

None
