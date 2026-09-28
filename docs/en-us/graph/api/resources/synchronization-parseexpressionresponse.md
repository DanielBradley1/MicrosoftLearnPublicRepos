<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-parseexpressionresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# parseExpressionResponse resource type

Namespace: microsoft.graph

Represents the response from the [parseExpression](https://learn.microsoft.com/en-us/graph/api/synchronization-synchronizationschema-parseexpression?view=graph-rest-1.0) action.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| error | publicError | Error details, if expression evaluation resulted in an error. |
| evaluationResult | String collection | A collection of values produced by the evaluation of the expression. |
| evaluationSucceeded | Boolean | `true` if the evaluation was successful. |
| parsedExpression | [attributeMappingSource](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingsource?view=graph-rest-1.0) | An [attributeMappingSource](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-attributemappingsource?view=graph-rest-1.0) object representing the parsed expression. |
| parsingSucceeded | Boolean | `true` if the expression was parsed successfully. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.parseExpressionResponse",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "evaluationSucceeded": "Boolean",
  "evaluationResult": [
    "String"
  ],
  "parsedExpression": {
    "@odata.type": "microsoft.graph.attributeMappingSource"
  },
  "parsingSucceeded": "Boolean"
}
```
