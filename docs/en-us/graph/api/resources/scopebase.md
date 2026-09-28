<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/scopebase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# scopeBase resource type

Namespace: microsoft.graph

Abstract base type representing a scope identifier for users, groups, or the tenant within policy bindings.

Use [groupScope](https://learn.microsoft.com/en-us/graph/api/resources/groupscope?view=graph-rest-1.0) for groups, [userScope](https://learn.microsoft.com/en-us/graph/api/resources/userscope?view=graph-rest-1.0) for individual users or [tenantScope](https://learn.microsoft.com/en-us/graph/api/resources/tenantscope?view=graph-rest-1.0) for all users in the tenant.

> **Note**: This is an abstract type and won't be instantiated directly. It serves as a base for more specific scope types like `groupScope`, `userScope` and `tenantScope`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identity | String | The identifier for the scope. This could be a user ID, group ID, or a keyword like "All" for tenant scope. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

> **Note** This is an abstract type and won't be instantiated directly.

```json
{
  "@odata.type": "#microsoft.graph.scopeBase",
  "identity": "String"
}
```
