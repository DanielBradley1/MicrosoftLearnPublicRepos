<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/groupscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# groupScope resource type

Namespace: microsoft.graph

Represents a Microsoft 365 group or distribution list as a scope within policy bindings.

Inherits from [scopeBase](https://learn.microsoft.com/en-us/graph/api/resources/scopebase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identity | String | The identifier for the scope. This is the group ID of the group. Inherited from [scopeBase](https://learn.microsoft.com/en-us/graph/api/resources/scopebase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.groupScope",
  "identity": "String"
}
```
