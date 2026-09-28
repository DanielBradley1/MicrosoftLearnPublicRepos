<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-expressioninputobject?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# expressionInputObject resource type

Namespace: microsoft.graph

Represents an object to be used as input test data when the [parseExpression](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationschema-parseexpression?view=graph-rest-1.0) action performs an expression evaluation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| definition | [objectDefinition](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-objectdefinition?view=graph-rest-1.0) | Definition of the test object. |
| properties | [stringKeyObjectValuePair](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-stringkeyobjectvaluepair?view=graph-rest-1.0) collection | Property values of the test object. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "definition": {
    "@odata.type": "microsoft.graph.objectDefinition"
  },
  "properties": [
    {
      "@odata.type": "microsoft.graph.stringKeyObjectValuePair"
    }
  ]
}
```
