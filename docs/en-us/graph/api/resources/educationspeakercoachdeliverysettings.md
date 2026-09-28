<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationspeakercoachdeliverysettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-19 -->

# educationSpeakerCoachDeliverySettings resource type

Namespace: microsoft.graph

Represents the delivery-related feedback types that students should receive from the Speaker Coach.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| areFillerWordsEnabled | Boolean | Indicates whether the student should receive feedback on their filler words from the Speaker Coach. |
| isPaceEnabled | Boolean | Indicates whether the student should receive feedback on their pace from the Speaker Coach. |
| isPitchEnabled | Boolean | Indicates whether the student should receive feedback on their pitch from the Speaker Coach. |
| isPronunciationEnabled | Boolean | Indicates whether the student should receive feedback on their pronunciation from the Speaker Coach. This is automatically enabled if `isAiFeedbackEnabled` is set to true on the `educationSpeakerProgressResource`, or if `spokenLanguageLocale` is set to a value besides `en-US` on the `educationSpeakerProgressResource`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationSpeakerCoachDeliverySettings",
  "areFillerWordsEnabled": "Boolean",
  "isPaceEnabled": "Boolean",
  "isPitchEnabled": "Boolean",
  "isPronunciationEnabled": "Boolean"
}
```
