<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/noscopes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# noScopes resource type

Namespace: microsoft.graph

Defines that no scopes of a resource application defined on the **agentIdentityBlueprint** are inheritable by agent identities through the [inheritablePermissions](https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-1.0) object. This configuration is the most restrictive inheritance configuration for delegated permission scopes. This configuration and can be used to create explicit security boundaries for sensitive resources or to override broader defaults.

Inherits from [inheritableScopes](https://learn.microsoft.com/en-us/graph/api/resources/inheritablescopes?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| kind | scopeCollectionKind | Always `none` for this derived type. Inherited from [inheritableScopes](https://learn.microsoft.com/en-us/graph/api/resources/inheritablescopes?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.noScopes",
  "kind": "String"
}
```
