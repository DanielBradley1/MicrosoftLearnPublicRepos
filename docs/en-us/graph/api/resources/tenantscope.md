<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# tenantScope resource type

Namespace: microsoft.graph

Represents the entire tenant \('All users'\) as a scope within policy bindings.

inherits from [scopeBase](https://learn.microsoft.com/en-us/graph/api/resources/scopebase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identity | String | The identifier for the scope. This could be a keyword like "All" for the tenant scope. Inherited properties from [scopeBase](https://learn.microsoft.com/en-us/graph/api/resources/scopebase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tenantScope",
  "identity": "String"
}
```
