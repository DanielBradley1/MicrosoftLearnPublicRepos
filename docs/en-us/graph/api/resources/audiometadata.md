<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/audiometadata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# audioMetadata resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents audio-specific encoding details supplied alongside a synthetic media detection report. Set on [mediaMetadata](https://learn.microsoft.com/en-us/graph/api/resources/mediametadata?view=graph-rest-beta) when the analyzed content is audio or multimodal.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bitDepth | Int32 | Bit depth of the audio samples \(for example, `16`, `24`\). |
| channels | Int32 | Number of audio channels \(for example, `1` for mono, `2` for stereo\). |
| sampleRateHz | Int32 | Sample rate in Hertz \(for example, `16000`, `48000`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.audioMetadata",
  "sampleRateHz": "Int32",
  "bitDepth": "Int32",
  "channels": "Int32"
}
```
