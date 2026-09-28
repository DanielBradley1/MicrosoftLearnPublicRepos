<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/classificationerror?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# classificationError resource type

Namespace: microsoft.graph

Represents a detailed error object, potentially containing multiple nested errors, encountered during classification or policy evaluation.

Use [processingError](https://learn.microsoft.com/en-us/graph/api/resources/processingerror?view=graph-rest-1.0) for errors related to content processing or policy evaluation. Inherits from [classifcationErrorBase](https://learn.microsoft.com/en-us/graph/api/resources/classifcationerrorbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | A service-defined error code string. Inherited from [classifcationErrorBase](https://learn.microsoft.com/en-us/graph/api/resources/classifcationerrorbase?view=graph-rest-1.0). |
| details | [classifcationErrorBase](https://learn.microsoft.com/en-us/graph/api/resources/classifcationerrorbase?view=graph-rest-1.0) collection | A collection of more specific errors contributing to the overall error. |
| innerError | [classificationInnerError](https://learn.microsoft.com/en-us/graph/api/resources/classificationinnererror?view=graph-rest-1.0) | Contains more specific, potentially internal error details. Inherited from [classifcationErrorBase](https://learn.microsoft.com/en-us/graph/api/resources/classifcationerrorbase?view=graph-rest-1.0). |
| message | String | A human-readable representation of the error. Inherited from [classifcationErrorBase](https://learn.microsoft.com/en-us/graph/api/resources/classifcationerrorbase?view=graph-rest-1.0). |
| target | String | The target of the error \(for example, the specific property or item causing the issue\). Inherited from [classifcationErrorBase](https://learn.microsoft.com/en-us/graph/api/resources/classifcationerrorbase?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "code": "String",
  "message": "String",
  "target": "String",
  "innerError": {
    "@odata.type": "microsoft.graph.classificationInnerError"
  },
  "details": [
    {
      "@odata.type": "#microsoft.graph.classifcationErrorBase",
    }
  ]
}
```
