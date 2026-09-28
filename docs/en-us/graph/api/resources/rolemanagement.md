<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/rolemanagement?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-21 -->

# roleManagement resource type

Namespace: microsoft.graph

Represents a Microsoft 365 role-based access control \(RBAC\) role management entity. This resource provides access to role definitions and role assignments surfaced from RBAC providers. **directory** \(Microsoft Entra ID\), **entitlementManagement**, and **deviceManagement** \(Intune\) providers are currently supported.

For more information, see:

- [Administrator role permissions in Microsoft Entra](https://learn.microsoft.com/en-us/azure/active-directory/roles/custom-overview).
- [Delegation and roles in Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/azure/active-directory/governance/entitlement-management-delegate).
- [Role-based access control \(RBAC\) with Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/fundamentals/role-based-access-control)

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| directory | [rbacApplication](https://learn.microsoft.com/en-us/graph/api/resources/rbacapplication?view=graph-rest-1.0) | Read-only. Nullable. |
| entitlementManagement | [rbacApplication](https://learn.microsoft.com/en-us/graph/api/resources/rbacapplication?view=graph-rest-1.0) | Container for roles and assignments for [entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement?view=graph-rest-1.0) resources. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.roleManagement"
}
```
