<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationaifeedbacksettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-19 -->

# educationAiFeedbackSettings resource type

Namespace: microsoft.graph

Represents the feedback types that students should receive from AI feedback.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| audienceEngagementSettings | [educationAiFeedbackAudienceEngagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationaifeedbackaudienceengagementsettings?view=graph-rest-1.0) | The audience engagement related feedback types that students should receive from the AI feedback. |
| contentSettings | [educationAiFeedbackContentSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationaifeedbackcontentsettings?view=graph-rest-1.0) | The content related feedback types that students should receive from the AI feedback. |
| deliverySettings | [educationAiFeedbackDeliverySettings](https://learn.microsoft.com/en-us/graph/api/resources/educationaifeedbackdeliverysettings?view=graph-rest-1.0) | The delivery related feedback types that students should receive from the AI feedback. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationAiFeedbackSettings",
  "audienceEngagementSettings": {"@odata.type": "microsoft.graph.educationAiFeedbackAudienceEngagementSettings"},
  "contentSettings": {"@odata.type": "microsoft.graph.educationAiFeedbackContentSettings"},
  "deliverySettings": {"@odata.type": "microsoft.graph.educationAiFeedbackDeliverySettings"}  
}
```
