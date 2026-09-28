<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/classificationinnererror?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# classificationInnerError resource type

Namespace: microsoft.graph

Contains more specific, potentially internal, details about an error that occurred during data classification, label evaluation, or policy processing.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityId | String | The activity ID associated with the request that generated the error. |
| clientRequestId | String | The client request ID, if provided by the caller. |
| code | String | A more specific, potentially internal, error code string. |
| errorDateTime | DateTimeOffset | The date and time the inner error occurred. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.classificationInnerError",
  "errorDateTime": "String (timestamp)",
  "code": "String",
  "clientRequestId": "String",
  "activityId": "String"
}
```
