<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentpointsgrade?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-05-16 -->

# educationAssignmentPointsGrade resource type

Namespace: microsoft.graph

When an assignment is set to a points grade type, each submission has this object associated with the **submission.grade** property. This creates a subclass from [educationAssignmentGrade](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentgrade?view=graph-rest-1.0), which will add the who data to this property. The max points are stored in the **assignments.grading** property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| gradedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | User who did the grading. |
| gradedDateTime | DateTimeOffset | Moment in time when the grade was applied to this submission object. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| points | Single | Number of points a teacher is giving this submission object. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "gradedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "gradedDateTime": "String (timestamp)",
  "points": "Double"
}
```
