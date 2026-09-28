<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationaifeedbackcriteria?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-19 -->

# educationAiFeedbackCriteria resource type

Namespace: microsoft.graph

Represents the settings for the AI feedback that students should receive.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| aiFeedbackSettings | [educationAiFeedbackSettings](https://learn.microsoft.com/en-us/graph/api/resources/educationaifeedbacksettings?view=graph-rest-1.0) | The feedback types that students should receive from AI feedback. |
| speechType | educationSpeechType | The type of speech the student provides. The possible values are: `informative`, `personal`, `persuasive`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationAiFeedbackCriteria",
  "aiFeedbackSettings": {"@odata.type": "microsoft.graph.educationAiFeedbackSettings"},
  "speechType": "String"
}
```
