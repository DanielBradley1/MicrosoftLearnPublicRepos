<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mediametadata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# mediaMetadata resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the audio, video, or streaming content that a detection bot analyzed when calling [reportSyntheticMedia](https://learn.microsoft.com/en-us/graph/api/participant-reportsyntheticmedia?view=graph-rest-beta). This resource combines high-level content attributes \(modality, MIME type, duration\) with optional modality-specific subobjects.

Which metadata subobjects to populate depends on the **modality** and whether the analysis is real time:

| modality | Metadata subobjects to set |
| :--- | :--- |
| `audio` | **audioMetadata**, plus **streamingMetadata** when **isRealTime** is `true`. |
| `video` | **videoMetadata**, plus **streamingMetadata** when **isRealTime** is `true`. |
| `multimodal` | **audioMetadata** and **videoMetadata**, plus **streamingMetadata** when **isRealTime** is `true`. |
| `image` | None. The metadata subobjects can be empty. |
| `text` | None. The metadata subobjects can be empty. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| audioMetadata | [audioMetadata](https://learn.microsoft.com/en-us/graph/api/resources/audiometadata?view=graph-rest-beta) | Audio-specific encoding details. Nullable. Set when the analyzed content is audio or multimodal. |
| byteSize | Int64 | Size of the content in bytes. Set this value to `0` for live streams where the total size is unknown; for recorded files, specify the actual size. |
| duration | Int32 | Duration of the analyzed content in whole seconds. Sub-second or millisecond windows are rounded to the nearest second. For a continuous live stream, set this value to the length of the analysis window. |
| isRealTime | Boolean | Indicates whether the analysis was performed in real time on a live stream. |
| mimeType | String | MIME type of the analyzed content. Common values for Teams media include `audio/pcm`, `video/mp4`, and `video/h264`. |
| modality | contentModality | Type of content to be analyzed. The possible values are: `audio`, `video`, `image`, `text`, `multimodal`, `unknownFutureValue`. |
| streamingMetadata | [streamingMetadata](https://learn.microsoft.com/en-us/graph/api/resources/streamingmetadata?view=graph-rest-beta) | Network and real-time streaming quality metrics. Nullable. Set when the analyzed content was streamed in real time. |
| videoMetadata | [videoMetadata](https://learn.microsoft.com/en-us/graph/api/resources/videometadata?view=graph-rest-beta) | Video-specific encoding and quality details. Nullable. Set when the analyzed content is video or multimodal. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mediaMetadata",
  "modality": "String",
  "isRealTime": "Boolean",
  "mimeType": "String",
  "byteSize": "Int64",
  "duration": "Int32",
  "videoMetadata": {
    "@odata.type": "microsoft.graph.videoMetadata"
  },
  "audioMetadata": {
    "@odata.type": "microsoft.graph.audioMetadata"
  },
  "streamingMetadata": {
    "@odata.type": "microsoft.graph.streamingMetadata"
  }
}
```
