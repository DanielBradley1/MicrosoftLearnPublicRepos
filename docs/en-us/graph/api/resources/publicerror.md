<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# publicError resource type

Namespace: microsoft.graph

Represents a generic error and its details.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | string | Represents the error code. |
| details | [publicErrorDetail](https://learn.microsoft.com/en-us/graph/api/resources/publicerrordetail?view=graph-rest-1.0) collection | Details of the error. |
| innerError | [publicInnerError](https://learn.microsoft.com/en-us/graph/api/resources/publicinnererror?view=graph-rest-1.0) | Details of the inner error. |
| message | string | A non-localized message for the developer. |
| target | String | The target of the error. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.publicError",
  "code": "String",
  "message": "String",
  "target": "String",
  "details": [
    {
      "@odata.type": "microsoft.graph.publicErrorDetail"
    }
  ],
  "innerError": {
    "@odata.type": "microsoft.graph.publicInnerError"
  }
}
```
