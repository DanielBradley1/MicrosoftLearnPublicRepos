<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/servicehostedmediaconfig?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# serviceHostedMediaConfig resource type

Namespace: microsoft.graph

The media that's hosted remotely and is inherited from [mediaConfig](https://learn.microsoft.com/en-us/graph/api/resources/mediaconfig?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| preFetchMedia | [mediaInfo](https://learn.microsoft.com/en-us/graph/api/resources/mediainfo?view=graph-rest-1.0) collection | The list of media to pre-fetch. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "preFetchMedia": [ { "@odata.type": "microsoft.graph.mediaInfo" } ]
}
```
