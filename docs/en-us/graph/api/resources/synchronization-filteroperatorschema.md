<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-filteroperatorschema?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# filterOperatorSchema resource type

Namespace: microsoft.graph

Describes an operator that can be used in a [filter](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-filter?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| arity | scopeOperatorType | Arity of the operator. The possible values are: `Binary`, `Unary`. The default is `Binary`. |
| multivaluedComparisonType | scopeOperatorMultiValuedComparisonType | The possible values are: `All`, `Any`. Applies only to multivalued attributes. `All` means that all values must satisfy the condition. `Any` means that at least one value has to satisfy the condition. The default is `All`. |
| name | String | Operator name. |
| supportedAttributeTypes | attributeType collection | Attribute types supported by the operator. The possible values are: `Boolean`, `Binary`, `Reference`, `Integer`, `String`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "arity": "String",
  "multivaluedComparisonType": "String",
  "name": "String",
  "supportedAttributeTypes": ["String"]
}
```
