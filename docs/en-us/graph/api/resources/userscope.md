<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# userScope resource type

Namespace: microsoft.graph

Represents an individual user as a scope within policy bindings.

Inherits from [scopeBase](https://learn.microsoft.com/en-us/graph/api/resources/scopebase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identity | String | The identifier for the scope. This could be a user ID, or group ID. Inherited properties from [scopeBase](https://learn.microsoft.com/en-us/graph/api/resources/scopebase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userScope",
  "identity": "String" 
}
```
