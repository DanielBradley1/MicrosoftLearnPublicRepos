<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationaifeedbackdeliverysettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-19 -->

# educationAiFeedbackDeliverySettings resource type

Namespace: microsoft.graph

Represents the delivery-related feedback types that students should receive from the AI feedback.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| areRhetoricalTechniquesEnabled | Boolean | Indicates whether the student should receive feedback on their rhetorical techniques from the AI feedback. |
| isLanguageUseEnabled | Boolean | Indicates whether the student should receive feedback on their language use from the AI feedback. |
| isStyleEnabled | Boolean | Indicates whether the student should receive feedback on their style from the AI feedback. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.educationAiFeedbackDeliverySettings",
  "areRhetoricalTechniquesEnabled": "Boolean",
  "isLanguageUseEnabled": "Boolean",
  "isStyleEnabled": "Boolean"
}
```
