<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/media?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# media resource type

Contains metadata about the media \(audio or video\) drive item.

It is available on the media property of [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-beta) resources.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| **isTranscriptionShown** | Boolean | If a file has a transcript, this setting controls if the closed captions / transcription for the media file should be shown to people during viewing. Read-Write. |
| **mediaSource** | [mediaSource](https://learn.microsoft.com/en-us/graph/api/resources/mediasource?view=graph-rest-beta) | Information about the source of media. Read-only. |

## Relationships

None.

## JSON representation

```json
{
  "isTranscriptionShown" : true,
  "mediaSource": { "@odata.type": "microsoft.graph.mediaSource" }
}
```

## Related content

For more information about the facets on a driveItem, see [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-beta).
