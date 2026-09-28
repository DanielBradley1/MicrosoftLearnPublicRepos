<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingsource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# attributeMappingSource resource type

Namespace: microsoft.graph

Defines how a value should be extracted \(or transformed\) from the source object. For example, it can be a value taken from a given attribute on the source object, or it can be a more complex expression of string concatenation/extraction/replacement based on several source attributes. This object is configured in the **source** property of [attributeMapping](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemapping?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expression | String | Equivalent expression representation of this **attributeMappingSource** object. |
| name | String | Name parameter of the mapping source. Depending on the **type** property value, this can be the name of the function, the name of the source attribute, or a constant value to be used. |
| parameters | [stringKeyAttributeMappingSourceValuePair](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-stringkeyattributemappingsourcevaluepair?view=graph-rest-1.0) collection | If this object represents a function, lists function parameters. Parameters consist of **attributeMappingSource** objects themselves, allowing for complex expressions. If **type** isn't `Function`, this property is null/empty array. |
| type | attributeMappingSourceType | The type of this attribute mapping source. The possible values are: `Attribute`, `Constant`, `Function`. Default is `Attribute`. |

### Sample syntaxes

Simple attribute to attribute mapping.

```json
{
    "expression": "[mail]",
    "name": "mail",
    "type": "Attribute"
}
```

Expression extracting first eight characters from the source attribute.

```json
 {
    "expression": "Mid([userPrincipalName], 1, 8)",
    "name": "Mid",
    "parameters": [
        {
            "key": "source",
            "value": {
                "expression": "[userPrincipalName]",
                "name": "userPrincipalName",
                "parameters": [],
                "type": "Attribute"
            }
        },
        {
            "key": "start",
            "value": {
                "expression": "\"1\"",
                "name": "1",
                "parameters": [],
                "type": "Constant"
            }
        },
        {
            "key": "length",
            "value": {
                "expression": "\"8\"",
                "name": "8",
                "parameters": [],
                "type": "Constant"
            }
        }
    ],
    "type": "Function"
}
```

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.attributeMappingSource",
  "expression": "String",
  "name": "String",
  "parameters": [
    {
      "@odata.type": "microsoft.graph.stringKeyAttributeMappingSourceValuePair"
    }
  ],
  "type": "String"
}
```
