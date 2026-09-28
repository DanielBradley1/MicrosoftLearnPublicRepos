<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationspeakercoachsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-19 -->

# educationSpeakerCoachSettings resource type

Namespace: microsoft.graph

Represents the feedback types that students should receive from the Speaker Coach.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| audienceEngagementSettings | [educationSpeakerCoachAudienceEngagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationspeakercoachaudienceengagementsettings?view=graph-rest-1.0) | The audience engagement related feedback types that students should receive from the Speaker Coach. |
| contentSettings | [educationSpeakerCoachContentSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationspeakercoachcontentsettings?view=graph-rest-1.0) | The content related feedback types that students should receive from the Speaker Coach. |
| deliverySettings | [educationSpeakerCoachDeliverySettings](https://learn.microsoft.com/en-us/graph/api/resources/educationspeakercoachdeliverysettings?view=graph-rest-1.0) | The delivery related feedback types that students should receive from the Speaker Coach. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationSpeakerCoachSettings",
  "audienceEngagementSettings": {"@odata.type": "microsoft.graph.educationSpeakerCoachAudienceEngagementSettings"},
  "contentSettings": {"@odata.type": "microsoft.graph.educationSpeakerCoachContentSettings"},
  "deliverySettings": {"@odata.type": "microsoft.graph.educationSpeakerCoachDeliverySettings"}
}
```
