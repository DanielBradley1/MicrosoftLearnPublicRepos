<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/classifcationerrorbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# classifcationErrorBase resource type

Namespace: microsoft.graph

Abstract base type for representing errors that occur during data classification, label evaluation, or policy processing.

Use [classificationError](https://learn.microsoft.com/en-us/graph/api/resources/classificationerror?view=graph-rest-1.0) for specific error details.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | A service-defined error code string. |
| innerError | [classificationInnerError](https://learn.microsoft.com/en-us/graph/api/resources/classificationinnererror?view=graph-rest-1.0) | Contains more specific, potentially internal error details. |
| message | String | A human-readable representation of the error. |
| target | String | The target of the error \(for example, the specific property or item causing the issue\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

> **Note:** This is an abstract type and won't be instantiated directly.

```json
{
  "@odata.type": "#microsoft.graph.classifcationErrorBase",
  "code": "String",
  "message": "String",
  "target": "String",
  "innerError": {
    "@odata.type": "microsoft.graph.classificationInnerError"
  }
}
```
