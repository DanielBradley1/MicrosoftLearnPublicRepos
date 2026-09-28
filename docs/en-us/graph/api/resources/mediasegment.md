<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mediasegment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# mediaSegment resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a contiguous time range of media analyzed by a synthetic media detection model and, for video, specific frames. Used by [syntheticMediaDetectionDetail](https://learn.microsoft.com/en-us/graph/api/resources/syntheticmediadetectiondetail?view=graph-rest-beta).

For real-time analysis of a live stream, **startTimeSec** and **endTimeSec** are measured in seconds from the start of the analyzed stream, which serves as the zero point. For recorded or offline analysis, where a stream-relative time base doesn't apply, set both values to `0`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endTimeSec | Int32 | End time of the segment, in seconds from the start of the analyzed live stream. Set to `0` for recorded or offline analysis, where a stream-relative time base doesn't apply. |
| frameIndices | Int32 collection | Frame indices that identify the video frames in the segment. Applies only to video analysis; pass an empty array for audio-only segments. |
| startTimeSec | Int32 | Start time of the segment, in seconds from the start of the analyzed live stream. Set to `0` for recorded or offline analysis, where a stream-relative time base doesn't apply. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mediaSegment",
  "startTimeSec": "Int32",
  "endTimeSec": "Int32",
  "frameIndices": [
    "Int32"
  ]
}
```
