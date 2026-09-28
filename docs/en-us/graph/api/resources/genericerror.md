<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/genericerror?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# genericError resource type

Namespace: microsoft.graph

A general-purpose error.

The **genericError** resource is the base type for the following resource:

- [accessReviewError](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewerror?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The error code. |
| message | String | The error message. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.genericError",
  "code": "String",
  "message": "String"
}
```
