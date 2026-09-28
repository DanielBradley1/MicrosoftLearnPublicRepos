<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudvideointeropinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-23 -->

# cloudVideoInteropInfo resource type

Namespace: microsoft.graph

Represents the online meeting details for conferencing device integration and [Cloud Video Interop \(CVI\)](https://learn.microsoft.com/en-us/microsoftteams/cloud-video-interop).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| moreInfoWebUrl | String | Provides other video teleconferencing \(VTC\) dial-in options. Read-only. |
| tenantKey | String | The tenant key that is used to dial into the interactive voice response \(IVR\) of the partner CVI service. |
| videoTeleconferenceId | String | The video teleconferencing ID. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudVideoInteropInfo",
  "moreInfoWebUrl": "String",
  "tenantKey": "String",
  "videoTeleconferenceId": "String"
}
```
