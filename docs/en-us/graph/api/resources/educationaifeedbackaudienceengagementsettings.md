<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationaifeedbackaudienceengagementsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-19 -->

# educationAiFeedbackAudienceEngagementSettings resource type

Namespace: microsoft.graph

Represents the audience engagement-related feedback types that students should receive from the AI feedback.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| areEngagementStrategiesEnabled | Boolean | Indicates whether the student should receive feedback on their engagement strategies from the AI feedback. |
| isCallToActionEnabled | Boolean | Indicates whether the student should receive feedback on their call to action from the AI feedback. |
| isEmotionalAndIntellectualAppealEnabled | Boolean | Indicates whether the student should receive feedback on their emotional and intellectual appeal from the AI feedback. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationAiFeedbackAudienceEngagementSettings",
  "areEngagementStrategiesEnabled": "Boolean",
  "isEmotionalAndIntellectualAppealEnabled": "Boolean",
  "isCallToActionEnabled": "Boolean"
}
```
