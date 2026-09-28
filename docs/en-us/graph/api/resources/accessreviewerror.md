<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewerror?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# accessReviewError resource type

Namespace: microsoft.graph

In an [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0), the **errors** property contains errors that occurred in the access review instance lifecycle. This resource is read-only.

Inherits from [genericError](https://learn.microsoft.com/en-us/graph/api/resources/genericerror?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | Represents the error type. Inherited from [genericError](https://learn.microsoft.com/en-us/graph/api/resources/genericerror?view=graph-rest-1.0). Read-only. |
| message | String | Represents the error details. Inherited from [genericError](https://learn.microsoft.com/en-us/graph/api/resources/genericerror?view=graph-rest-1.0). Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewError",
  "code": "String",
  "message": "String"
}
```
