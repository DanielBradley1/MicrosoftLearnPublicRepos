<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/videometadata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# videoMetadata resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents video-specific encoding and quality details supplied alongside a synthetic media detection report. Set on [mediaMetadata](https://learn.microsoft.com/en-us/graph/api/resources/mediametadata?view=graph-rest-beta) when the analyzed content is video or multimodal.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| bitrateKbps | Int32 | Video bitrate in kilobits per second. |
| codec | String | The video codec used \(for example, `H.264` or `VP9`\). |
| frameRate | Double | Frame rate in frames per second. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.videoMetadata",
  "codec": "String",
  "frameRate": "Double",
  "bitrateKbps": "Int32"
}
```
