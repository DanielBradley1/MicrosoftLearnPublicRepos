<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workingtimeschedule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# workingTimeSchedule resource type

Namespace: microsoft.graph

Contains triggers for policies associated with the start and end of working hours for users.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/workingtimeschedule-get?view=graph-rest-1.0) | [workingTimeSchedule](https://learn.microsoft.com/en-us/graph/api/resources/workingtimeschedule?view=graph-rest-1.0) | Read the properties and relationships of a [workingTimeSchedule](https://learn.microsoft.com/en-us/graph/api/resources/workingtimeschedule?view=graph-rest-1.0) object. |
| [Start working time](https://learn.microsoft.com/en-us/graph/api/workingtimeschedule-startworkingtime?view=graph-rest-1.0) | None | Trigger the policies associated with the start of working hours for a specific user. |
| [End working time](https://learn.microsoft.com/en-us/graph/api/workingtimeschedule-endworkingtime?view=graph-rest-1.0) | None | Trigger the policies associated with the end of working hours for a specific user. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the working time schedule. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.workingTimeSchedule",
  "id": "String (identifier)"
}
```
