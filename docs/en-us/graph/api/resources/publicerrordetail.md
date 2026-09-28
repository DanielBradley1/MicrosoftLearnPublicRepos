<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/publicerrordetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# publicErrorDetail resource type

Namespace: microsoft.graph

Represents the details of [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) or [publicInnerError](https://learn.microsoft.com/en-us/graph/api/resources/publicinnererror?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The error code. |
| message | String | The error message. |
| target | String | The target of the error. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.publicErrorDetail",
  "code": "String",
  "message": "String",
  "target": "String"
}
```
