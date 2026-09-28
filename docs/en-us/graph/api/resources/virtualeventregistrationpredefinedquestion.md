<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationpredefinedquestion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-23 -->

# virtualEventRegistrationPredefinedQuestion resource type

Namespace: microsoft.graph

Represents a predefined registration question associated with a [virtualEventRegistration](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistration?view=graph-rest-1.0).

Inherits from [virtualEventRegistrationQuestionBase](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventregistrationquestionbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| label | virtualEventRegistrationPredefinedQuestionLabel | Label of the predefined registration question. It accepts a single line of text: `street`, `city`, `state`, `postalCode`, `countryOrRegion`, `industry`, `jobTitle`, `organization`, and `unknownFutureValue`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventRegistrationPredefinedQuestion",
  "label": "String",
  "displayName": "String",  
  "id": "String (identifier)",
  "isRequired": "Boolean"
}
```
