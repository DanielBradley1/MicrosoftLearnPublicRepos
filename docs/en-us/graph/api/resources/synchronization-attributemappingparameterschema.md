<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingparameterschema?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# attributeMappingParameterSchema resource type

Namespace: microsoft.graph

Describes a single parameter \(**parameters** property\) used in an [attributeMappingFunctionSchema](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingfunctionschema?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowMultipleOccurrences | Boolean | The given parameter can be provided multiple times \(for example, multiple input strings in the `Concatenate(string,string,...)` function\). |
| name | String | Parameter name. |
| required | Boolean | `true` if the parameter is required; otherwise `false`. |
| type | attributeType | The possible values are: `String`, `Integer`, `Reference`, `Binary`, `Boolean`, `DateTime`. Default is `String`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "allowMultipleOccurrences": "Boolean",
  "name": "String",
  "required": "Boolean",
  "type": "String"
}
```
