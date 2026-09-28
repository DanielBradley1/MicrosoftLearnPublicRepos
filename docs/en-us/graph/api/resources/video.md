<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/video?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# video resource type

Namespace: microsoft.graph

The **video** resource groups video-related data items into a single structure.

If a [**driveItem**](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) has a non-null **video** facet, the item represents a video file. The properties of the **video** resource are populated by extracting metadata from the file.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "audioBitsPerSample": 16,
  "audioChannels": 1,
  "audioFormat": "AAC",
  "audioSamplesPerSecond": 44100,
  "bitrate": 39101896,
  "duration": 8053,
  "fourCC": "H264",
  "frameRate": 239.877,
  "height": 1280,
  "width": 720
}
```

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| **audioBitsPerSample** | Int32 | Number of audio bits per sample. |
| **audioChannels** | Int32 | Number of audio channels. |
| **audioFormat** | string | Name of the audio format \(AAC, MP3, etc.\). |
| **audioSamplesPerSecond** | Int32 | Number of audio samples per second. |
| **bitrate** | Int32 | Bit rate of the video in bits per second. |
| **duration** | Int64 | Duration of the file in milliseconds. |
| **fourCC** | string | "Four character code" name of the video format. |
| **frameRate** | double | Frame rate of the video. |
| **height** | Int32 | Height of the video, in pixels. |
| **width** | Int32 | Width of the video, in pixels. |

## Remarks

For more information about the facets on a driveItem, see [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
