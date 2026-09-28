<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacapplicationmultiple?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-21 -->

# unifiedRbacApplicationMultiple resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a role management container for unified role definitions and role assignments for role-based access control \(RBAC\) providers in the Microsoft cloud. Currently, only the Microsoft Defender XDR Unified RBAC provider consumes this resource.

Inherits from [rbacApplicationMultiple](https://learn.microsoft.com/en-us/graph/api/resources/rbacapplicationmultiple?view=graph-rest-beta).

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| customAppScopes | [customAppScope](https://learn.microsoft.com/en-us/graph/api/resources/customappscope?view=graph-rest-beta) collection | Represents the resources that the principal has been granted access. |
| resourceNamespaces | [unifiedRbacResourceNamespace](https://learn.microsoft.com/en-us/graph/api/resources/unifiedrbacresourcenamespace?view=graph-rest-beta) collection | Represents a service group and the collection of allowed actions. Inherits from [rbacApplicationMultiple](https://learn.microsoft.com/en-us/graph/api/resources/rbacapplicationmultiple?view=graph-rest-beta) |
| roleAssignments | [unifiedRoleAssignmentMultiple](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroleassignmentmultiple?view=graph-rest-beta) collection | Resource to grant access to users or groups. Inherits from [rbacApplicationMultiple](https://learn.microsoft.com/en-us/graph/api/resources/rbacapplicationmultiple?view=graph-rest-beta) |
| roleDefinitions | [unifiedRoleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/unifiedroledefinition?view=graph-rest-beta) collection | The roles allowed by RBAC providers and the permissions assigned to the roles. Inherits from [rbacApplicationMultiple](https://learn.microsoft.com/en-us/graph/api/resources/rbacapplicationmultiple?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRbacApplicationMultiple",
  "id": "String (identifier)"
}
```
