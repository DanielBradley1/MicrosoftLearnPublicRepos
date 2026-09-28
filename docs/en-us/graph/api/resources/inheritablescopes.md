<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/inheritablescopes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# inheritableScopes resource type

Namespace: microsoft.graph

Represents the inheritance pattern applied to delegated permission scopes published by a resource application and exposed on an [agent identity blueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-1.0) via its [inheritablePermissions](https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-1.0) collection. This abstract type is realized by the following derived types:

- [allAllowedScopes](https://learn.microsoft.com/en-us/graph/api/resources/allallowedscopes?view=graph-rest-1.0) – inherit all scopes currently defined for the resource application \(future scopes automatically become inheritable\).
- [enumeratedScopes](https://learn.microsoft.com/en-us/graph/api/resources/enumeratedscopes?view=graph-rest-1.0) – inherit only the explicitly listed scopes.
- [noScopes](https://learn.microsoft.com/en-us/graph/api/resources/noscopes?view=graph-rest-1.0) – inherit none of the scopes for the resource application.

Use the `kind` discriminator to identify the active inheritance pattern and to filter results.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| kind | scopeCollectionKind | Discriminator indicating which inheritance pattern is configured. The possible values are: `allAllowed` \(inherit all scopes\), `enumerated` \(inherit listed scopes only\), `none` \(inherit no scopes\), `scopeKindNotSet` \(unset; internal use\), `unknownFutureValue` \(reserved for future expansion\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.inheritableScopes",
  "kind": "String"
}
```
