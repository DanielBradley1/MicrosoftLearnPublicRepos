<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/enumeratedscopes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# enumeratedScopes resource type

Namespace: microsoft.graph

Defines that an explicit list of scopes of a resource application defined on the **agentIdentityBlueprint** are inheritable by agent identities through the [inheritablePermissions](https://learn.microsoft.com/en-us/graph/api/resources/inheritablepermission?view=graph-rest-1.0) object. This constrained inheritance configuration for delegated permission scopes provides fine‑grained control and supports gradual permission expansion without broad elevation.

Inherits from [inheritableScopes](https://learn.microsoft.com/en-us/graph/api/resources/inheritablescopes?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| kind | scopeCollectionKind | Always `enumerated` for this derived type. Inherited from [inheritableScopes](https://learn.microsoft.com/en-us/graph/api/resources/inheritablescopes?view=graph-rest-1.0). |
| scopes | String collection | Required. Nonempty list of delegated permission scope identifiers published by the resource application to inherit. Entries must be unique and must not include any [globally blocked scopes](https://learn.microsoft.com/en-us/graph/api/resources/agentid-platform-overview?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.enumeratedScopes",
  "kind": "String",
  "scopes": [
    "String"
  ]
}
```
