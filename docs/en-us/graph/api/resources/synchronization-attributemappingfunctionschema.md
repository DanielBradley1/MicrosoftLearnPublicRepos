<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingfunctionschema?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# attributeMappingFunctionSchema resource type

Namespace: microsoft.graph

Describes a function that can be used in an [attribute mapping](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemapping?view=graph-rest-1.0) to transform values during synchronization.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get schema functions](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationschema-functions?view=graph-rest-1.0) | [attributeMappingFunctionSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingfunctionschema?view=graph-rest-1.0) collection | List supported attribute mapping functions. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key. Read-only. |
| parameters | [attributeMappingParameterSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingparameterschema?view=graph-rest-1.0) collection | Collection of function parameters. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "parameters": [
    {
      "@odata.type": "microsoft.graph.attributeMappingParameterSchema"
    }
  ]
}
```
