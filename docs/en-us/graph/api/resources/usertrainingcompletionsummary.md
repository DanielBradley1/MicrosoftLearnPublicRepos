<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usertrainingcompletionsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# userTrainingCompletionSummary resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains aggregate data about userss training progress.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completedUsersCount | Int32 | The number of users who completed all the trainings before the due date. |
| inProgressUsersCount | Int32 | The number of users who started at least one training. |
| notCompletedUsersCount | Int32 | The number of users who didn't complete all the trainings before the due date. |
| notStartedUsersCount | Int32 | The number of users who didn't start any training. |
| previouslyAssignedUsersCount | Int32 | The number of users who are already assigned the same training. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userTrainingCompletionSummary",
  "notStartedUsersCount": "Integer",
  "completedUsersCount": "Integer",
  "inProgressUsersCount": "Integer",
  "notCompletedUsersCount": "Integer",
  "previouslyAssignedUsersCount": "Integer"
}
```
