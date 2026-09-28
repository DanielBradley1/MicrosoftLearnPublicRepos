<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/rubriclevel?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# rubricLevel resource type

Namespace: microsoft.graph

A level of a rubric.

See [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) for a description of the relationship between rubric *qualities*, *levels*, and *criteria*.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The description of this rubric level. |
| displayName | String | The name of this rubric level. |
| grading | [educationAssignmentGradeType](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentgradetype?view=graph-rest-1.0) | Null if this is a no-points rubric; [educationAssignmentPointsGradeType](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentpointsgradetype?view=graph-rest-1.0) if it's a points rubric. |
| levelId | String | The ID of this resource. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": {"@odata.type": "microsoft.graph.itemBody"},
  "displayName": "String",
  "grading": {"@odata.type": "microsoft.graph.educationAssignmentGradeType"},
  "levelId": "String"
}
```
