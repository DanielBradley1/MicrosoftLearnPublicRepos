<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usersolutionroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# userSolutionRoot resource type

Namespace: microsoft.graph

Represents an identifier that relates a user to the working time schedule triggers.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the user's custom solution entity. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| workingTimeSchedule | [workingTimeSchedule](https://learn.microsoft.com/en-us/graph/api/resources/workingtimeschedule?view=graph-rest-1.0) | The working time schedule entity associated with the solution. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userSolutionRoot",
  "id": "String (identifier)"
}
```
