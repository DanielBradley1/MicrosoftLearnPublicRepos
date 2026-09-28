<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationspeakercoachcontentsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-19 -->

# educationSpeakerCoachContentSettings resource type

Namespace: microsoft.graph

Represents the content-related feedback types that students should receive from the Speaker Coach.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isInclusivenessEnabled | Boolean | Indicates whether the student should receive feedback on their inclusiveness from the Speaker Coach. |
| isRepetitiveLanguageEnabled | Boolean | Indicates whether the student should receive feedback on their repetitive language from the Speaker Coach. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationSpeakerCoachContentSettings",
  "isInclusivenessEnabled": "Boolean",
  "isRepetitiveLanguageEnabled": "Boolean"
}
```
