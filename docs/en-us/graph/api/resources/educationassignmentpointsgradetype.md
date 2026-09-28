<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentpointsgradetype?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# educationAssignmentPointsGradeType resource type

Namespace: microsoft.graph

Resource type that is used with the **assignments.grading** property. This is a subclass of [educationAssignmentGradeType](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentgradetype?view=graph-rest-1.0).

This indicates that the assignment is graded and stores the maximum number of points each student can achieve on this work item. When this is set on an assignment, each submission will get an [educationAssignmentPointsGrade](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentpointsgrade?view=graph-rest-1.0) property associated with it for the storage of each student's points.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| maxPoints | Single | Max points possible for this assignment. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "maxPoints": "Double"
}
```
