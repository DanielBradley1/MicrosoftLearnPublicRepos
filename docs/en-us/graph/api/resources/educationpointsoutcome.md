<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationpointsoutcome?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# educationPointsOutcome resource type

Namespace: microsoft.graph

An [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0) that gives a numerical grade.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Update outcome](https://learn.microsoft.com/en-us/graph/api/educationoutcome-update?view=graph-rest-1.0) | [educationOutcome](https://learn.microsoft.com/en-us/graph/api/resources/educationoutcome?view=graph-rest-1.0) | Update educationOutcome object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the educationPointsOutcome. |
| points | [educationAssignmentPointsGrade](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentpointsgrade?view=graph-rest-1.0) | The numeric grade the teacher has given the student for this assignment. |
| publishedPoints | [educationAssignmentPointsGrade](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentpointsgrade?view=graph-rest-1.0) | A copy of the points property that is made when the grade is released to the student. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "points": {"@odata.type": "microsoft.graph.educationAssignmentPointsGrade"},
  "publishedPoints": {"@odata.type": "microsoft.graph.educationAssignmentPointsGrade"}
}
```
