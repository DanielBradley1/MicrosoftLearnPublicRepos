<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/streamingmetadata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# streamingMetadata resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents network and real-time streaming quality metrics that accompany a synthetic media detection report. Used by [mediaMetadata](https://learn.microsoft.com/en-us/graph/api/resources/mediametadata?view=graph-rest-beta) when the analyzed content was streamed in real time.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| frameDropRate | Double | Percentage of frames dropped during streaming, expressed as a value between `0.0` and `1.0`. |
| latencyMs | Int32 | Network latency in milliseconds. |
| networkJitterMs | Int32 | Network jitter in milliseconds. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.streamingMetadata",
  "latencyMs": "Int32",
  "frameDropRate": "Double",
  "networkJitterMs": "Int32"
}
```
