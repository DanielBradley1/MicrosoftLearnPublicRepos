<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-24 -->

# educationRubric resource type

Namespace: microsoft.graph

Represents a grading rubric that can be attached to an assignment. A rubric is associated with an **educationUser** \(teacher\), and attached to one or more **educationAssignment** resources.

For more information, see [Education rubric overview](https://learn.microsoft.com/en-us/graph/education-rubric-overview).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/educationuser-list-rubrics?view=graph-rest-1.0) | [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) collection | Retrieve a list of **educationRubric** objects. |
| [Create](https://learn.microsoft.com/en-us/graph/api/educationuser-post-rubrics?view=graph-rest-1.0) | [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) | Create a new **educationRubric** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/educationrubric-get?view=graph-rest-1.0) | [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) | Read properties and relationships of an **educationRubric** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/educationrubric-update?view=graph-rest-1.0) | [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) | Update an **educationRubric** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/educationrubric-delete?view=graph-rest-1.0) | None | Delete an **educationRubric** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The user who created this resource. |
| createdDateTime | DateTimeOffset | The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| description | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The description of this rubric. |
| displayName | String | The name of this rubric. |
| grading | [educationAssignmentGradeType](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentgradetype?view=graph-rest-1.0) | The grading type of this rubric. You can use `null` for a no-points rubric or [educationAssignmentPointsGradeType](https://learn.microsoft.com/en-us/graph/api/resources/educationassignmentpointsgradetype?view=graph-rest-1.0) for a points rubric. |
| id | String | Unique identifier for the rubric. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The last user to modify the resource. |
| lastModifiedDateTime | DateTimeOffset | Moment in time when the resource was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| levels | [rubricLevel](https://learn.microsoft.com/en-us/graph/api/resources/rubriclevel?view=graph-rest-1.0) collection | The collection of levels making up this rubric. |
| qualities | [rubricQuality](https://learn.microsoft.com/en-us/graph/api/resources/rubricquality?view=graph-rest-1.0) collection | The collection of qualities making up this rubric. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "description": {"@odata.type": "microsoft.graph.itemBody"},
  "displayName": "String",
  "grading": {"@odata.type": "microsoft.graph.educationAssignmentGradeType"},
  "id": "String (identifier)",
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "levels": [{"@odata.type": "microsoft.graph.rubricLevel"}],
  "qualities": [{"@odata.type": "microsoft.graph.rubricQuality"}]
}
```
