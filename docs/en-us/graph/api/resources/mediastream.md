<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mediastream?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# mediaStream resource type

Namespace: microsoft.graph

This contains information about the media channel.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| direction | String | The direction. The possible values are `inactive`, `sendOnly`, `receiveOnly`, `sendReceive`. |
| label | String | The media stream label. |
| mediaType | String | The media type. The possible values are `unknown`, `audio`, `video`, `videoBasedScreenSharing`, `data`. |
| serverMuted | Boolean | If the media is muted by the server. |
| sourceId | String | The source ID. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "direction": "inactive | sendOnly | receiveOnly | sendReceive",
  "label": "String",
  "mediaType": "unknown | audio | video | videoBasedScreenSharing | data",
  "serverMuted": true,
  "sourceId": "String"
}
```
