<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/processcontentresponses?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# processContentResponses resource type

Namespace: microsoft.graph

Represents the response for a single request within a [batch content processing operation](https://learn.microsoft.com/en-us/graph/api/tenantdatasecurityandgovernance-processcontentasync?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| requestId | String | The unique identifier that matches the `requestId` provided in the corresponding `processContentBatchRequest`. |
| results | [microsoft.graph.processContentResponse](https://learn.microsoft.com/en-us/graph/api/resources/processcontentresponse?view=graph-rest-1.0) | The outcome of processing the content associated with this `requestId`. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.processContentResponses",
  "requestId": "String",
  "results": {
    "@odata.type": "microsoft.graph.processContentResponse"
  }
}
```
