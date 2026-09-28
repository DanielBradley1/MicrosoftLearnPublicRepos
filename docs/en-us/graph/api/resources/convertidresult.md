<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/convertidresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# convertIdResult resource type

Namespace: microsoft.graph

The result of an ID format conversion performed by the [translateExchangeIds](https://learn.microsoft.com/en-us/graph/api/user-translateexchangeids?view=graph-rest-1.0) function.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| errorDetails | [genericError](https://learn.microsoft.com/en-us/graph/api/resources/genericerror?view=graph-rest-1.0) | An error object indicating the reason for the conversion failure. This value isn't present if the conversion succeeded. |
| sourceId | String | The identifier that was converted. This value is the original, un-converted identifier. |
| targetId | String | The converted identifier. This value isn't present if the conversion failed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "errorDetails": {
    "@odata.type": "microsoft.graph.genericError"
  },
  "sourceId": "String",
  "targetId": "String"
}
```
