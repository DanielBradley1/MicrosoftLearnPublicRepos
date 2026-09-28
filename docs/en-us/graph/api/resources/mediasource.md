<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mediasource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# mediaSource resource type

Contains metadata about the source of the media \(audio or video\) drive item.

It is available on the media property of the [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) resources.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentCategory | mediaSourceContentCategory | Enumeration value that indicates the media content category. |

### mediaSourceContentCategory values

| Value | Description |
| :--- | :--- |
| meeting | The media is a meeting. |
| liveStream | The media is a live stream. |
| presentation | The media is a presentation. |
| screenRecording | The media is a screen recording. |
| story | The media is a story. |
| profile | The media is a profile. |
| chat | The media is a chat. |
| note | The media is a note. |
| comment | The media is a comment. |
| unknownFutureValue | Marker value for future compatibility. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "contentCategory" : "string"
}
```

## See also

For more information about the facets on a driveItem, see [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
