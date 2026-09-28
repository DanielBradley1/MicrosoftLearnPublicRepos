<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/learningassignment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# learningAssignment resource type

Namespace: microsoft.graph

Represents the details of a learning activity assigned to a user.

Inherits from [learningCourseActivity](https://learn.microsoft.com/en-us/graph/api/resources/learningcourseactivity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| @odata.type | String | Indicates whether this is a [learningAssignment](https://learn.microsoft.com/en-us/graph/api/resources/learningassignment?view=graph-rest-1.0) or [learningSelfInitiated](https://learn.microsoft.com/en-us/graph/api/resources/learningselfinitiatedcourse?view=graph-rest-1.0) course activity. Required. |
| assignedDateTime | DateTimeOffset | Assigned date for the course activity. Optional. |
| assignerUserId | String | The user ID of the assigner. Optional. |
| assignmentType | String | The assignment type for the course activity. The possible values are: `required`, `recommended`, `unknownFutureValue`, `peerRecommended`. Use the `Prefer: include-unknown-enum-members` request header to get the following value or values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `peerRecommended`. Required. |
| completedDateTime | DateTimeOffset | Date and time when the assignment was completed. Optional. |
| completionPercentage | Int32 | The percentage of the course completed by the user. If a value is provided, it must be between `0` and `100` \(inclusive\). Optional. |
| dueDateTime | DateTimeOffset | Due date for the course activity. Optional. |
| externalCourseActivityId | String | A course activity ID generated at provider. Optional. |
| id | String | The generated ID for a request that can be used to make further interactions to the course activity APIs. |
| learnerUserId | String | The user ID of the learner to whom the activity is assigned. Required. |
| learningContentId | String | The ID of the learning content in Viva Learning. Required. |
| learningProviderId | String | The registration ID of the provider. Required. |
| notes | String | Notes for the course activity. Optional. |
| startedDateTime | DateTimeOffset | The date and time when the self-initiated course was started by the learner. Optional. |
| status | courseStatus | The status of the course activity. The possible values are: `notStarted`, `inProgress`, `completed`. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.learningAssignment",
  "assignedDateTime": "String (timestamp)",
  "assignerUserId": "String",
  "assignmentType": "String",
  "completedDateTime": "String (timestamp)",
  "completionPercentage": "Int32",
  "dueDateTime": "String (timestamp)",
  "externalCourseActivityId": "String",
  "id": "String (identifier)",
  "learnerUserId": "String",
  "learningContentId": "String",
  "learningProviderId": "String",
  "notes": "String",
  "status": "String"
}
```
