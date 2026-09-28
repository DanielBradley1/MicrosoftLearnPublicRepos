<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/allallowedscopes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# allAllowedScopes resource type

Namespace: microsoft.graph

Represents the broadest inheritance pattern for delegated permission scopes. When an [inheritablePermission](https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-1.0) entry uses `allAllowedScopes`, every scope published by the referenced resource application is considered inheritable and may appear on agent identities without requiring explicit user or admin consent. Newly introduced scopes become inheritable automatically, reducing maintenance overhead for trusted applications.

Inherits from [inheritableScopes](https://learn.microsoft.com/en-us/graph/api/resources/inheritablescopes?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| kind | scopeCollectionKind | Always `allAllowed` for this derived type. Inherited from [inheritableScopes](https://learn.microsoft.com/en-us/graph/api/resources/inheritablescopes?view=graph-rest-1.0). Other possible discriminator values on the base type include: `enumerated`, `none`, `scopeKindNotSet`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.allAllowedScopes",
  "kind": "String"
}
```
