<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationfeedbackoutcome?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# educationFeedbackOutcome resource type

Namespace: microsoft.graph

Represents feedback on an [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0) object in the form of text.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Update outcome](https://learn.microsoft.com/en-us/graph/api/educationoutcome-update?view=graph-rest-1.0) | [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0) | Update educationOutcome object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| feedback | [educationFeedback](https://learn.microsoft.com/en-us/graph/api/resources/educationfeedback?view=graph-rest-1.0) | Teacher's written feedback to the student. |
| id | String | Unique identifier for the educationFeedbackOutcome. |
| publishedFeedback | [educationFeedback](https://learn.microsoft.com/en-us/graph/api/resources/educationfeedback?view=graph-rest-1.0) | A copy of the feedback property that is made when the grade is released to the student. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "feedback": {"@odata.type": "microsoft.graph.educationFeedback"},
  "id": "String (identifier)",
  "publishedFeedback": {"@odata.type": "microsoft.graph.educationFeedback"}
}
```
