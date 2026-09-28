<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/expressionevaluationdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# expressionEvaluationDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the expression details, result, and property details.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expression | String | Represents expression which has been evaluated. |
| expressionEvaluationDetails | expressionEvaluationDetails collection | Represents the details of the evaluation of the expression. |
| expressionResult | Boolean | Represents the value of the result of the current expression. |
| propertyToEvaluate | [propertyToEvaluate](https://learn.microsoft.com/en-us/graph/api/resources/propertytoevaluate?view=graph-rest-beta) | Defines the name of the property and the value of that property. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "expression": "String",
  "expressionEvaluationDetails": [
    { "@odata.type": "microsoft.graph.expressionEvaluationDetails" }
  ],
  "expressionResult": true,
  "propertyToEvaluate": { "@odata.type": "microsoft.graph.propertyToEvaluate" }
}
```
