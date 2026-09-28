<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentgrade?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# educationAssignmentGrade resource type

Namespace: microsoft.graph

Represents the **Grade** object on a Submission.

This is an abstract type that will never be instantiated; however, all types of grading \(points, pass/fail, and so on\) are subclasses of this resource type. This object also tracks who is doing the grading. This is used in the **submission.grade** property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| gradedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | User who did the grading. |
| gradedDateTime | DateTimeOffset | Moment in time when the grade was applied to this submission object. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "gradedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "gradedDateTime": "String (timestamp)"
}
```
