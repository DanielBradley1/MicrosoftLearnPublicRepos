<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-stringkeyattributemappingsourcevaluepair?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# stringKeyAttributeMappingSourceValuePair resource type

Namespace: microsoft.graph

Represents a key-value pair where the key is a string and the value is [attributeMappingSource](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingsource?view=graph-rest-1.0). This object is configured in the **parameters** property of [attributeMappingSource](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingsource?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| key | String | The name of the parameter. |
| value | [attributeMappingSource](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingsource?view=graph-rest-1.0) | The value of the parameter. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "key": "String",
  "value": {
    "@odata.type": "microsoft.graph.attributeMappingSource"
  }
}
```
