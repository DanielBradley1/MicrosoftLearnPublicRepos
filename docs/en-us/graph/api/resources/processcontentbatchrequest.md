<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/processcontentbatchrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# processContentBatchRequest resource type

Namespace: microsoft.graph

Represents a single entry within a request submitted to the [processContentAsync](https://learn.microsoft.com/en-us/graph/api/tenantdatasecurityandgovernance-processcontentasync?view=graph-rest-1.0) action.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentToProcess | [processContentRequest](https://learn.microsoft.com/en-us/graph/api/resources/processcontentrequest?view=graph-rest-1.0) | The actual content processing request details, including content metadata, activity, device, and app info. |
| requestId | String | A unique identifier provided by the client to correlate this specific request item within the batch. |
| userId | String | The unique identifier \(Object ID or UPN\) of the user in whose context the content should be processed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.processContentBatchRequest",
  "requestId": "String",
  "userId": "String",
  "contentToProcess": {
    "@odata.type": "microsoft.graph.processContentRequest"
  }
}
```
