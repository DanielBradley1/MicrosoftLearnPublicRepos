<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationrubricoutcome?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# educationRubricOutcome resource type

Namespace: microsoft.graph

An [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0) that provides a graded rubric.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Update outcome](https://learn.microsoft.com/en-us/graph/api/educationoutcome-update?view=graph-rest-1.0) | [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0) | Update educationOutcome object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the educationRubricOutcome. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The last user to modify the resource. |
| lastModifiedDateTime | DateTimeOffset | Moment in time when the resource was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| publishedRubricQualityFeedback | [rubricQualityFeedbackModel](https://learn.microsoft.com/en-us/graph/api/resources/rubricqualityfeedbackmodel?view=graph-rest-1.0) collection | A copy of the rubricQualityFeedback property that is made when the grade is released to the student. |
| publishedRubricQualitySelectedLevels | [rubricQualitySelectedColumnModel](https://learn.microsoft.com/en-us/graph/api/resources/rubricqualityselectedcolumnmodel?view=graph-rest-1.0) collection | A copy of the rubricQualitySelectedLevels property that is made when the grade is released to the student. |
| rubricQualityFeedback | [rubricQualityFeedbackModel](https://learn.microsoft.com/en-us/graph/api/resources/rubricqualityfeedbackmodel?view=graph-rest-1.0) collection | A collection of specific feedback for each quality of this rubric. |
| rubricQualitySelectedLevels | [rubricQualitySelectedColumnModel](https://learn.microsoft.com/en-us/graph/api/resources/rubricqualityselectedcolumnmodel?view=graph-rest-1.0) collection | The level that the teacher has selected for each quality while grading this assignment. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "publishedRubricQualityFeedback": [{"@odata.type": "microsoft.graph.rubricQualityFeedbackModel"}],
  "publishedRubricQualitySelectedLevels": [{"@odata.type": "microsoft.graph.rubricQualitySelectedColumnModel"}],
  "rubricQualityFeedback": [{"@odata.type": "microsoft.graph.rubricQualityFeedbackModel"}],
  "rubricQualitySelectedLevels": [{"@odata.type": "microsoft.graph.rubricQualitySelectedColumnModel"}]
}
```
