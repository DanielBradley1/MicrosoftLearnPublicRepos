<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/processingerror?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# processingError resource type

Namespace: microsoft.graph

Represents an error encountered during content processing or policy evaluation, indicating if it's transient or permanent.

Inherits from [classificationError](https://learn.microsoft.com/en-us/graph/api/resources/classificationerror?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| errorType | microsoft.graph.security.contentProcessingErrorType | Indicates whether the error is considered transient \(potentially resolvable by retry\) or permanent. Possible values are `transient`, `permanent`, `unknownFutureValue`. Inherits from [classificationError](https://learn.microsoft.com/en-us/graph/api/resources/classificationerror?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.processingError",
  "code": "String",
  "message": "String",
  "target": "String",
  "innerError": {
    "@odata.type": "microsoft.graph.classificationInnerError"
  },
  "details": [
    { "@odata.type": "microsoft.graph.classifcationErrorBase" }
  ],
  "errorType": "String"
}
```
