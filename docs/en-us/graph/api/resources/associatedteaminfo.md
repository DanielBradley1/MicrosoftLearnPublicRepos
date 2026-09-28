<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/associatedteaminfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# associatedTeamInfo resource type

Namespace: microsoft.graph

Represents a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) that is associated with a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0).

Currently, a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) can be associated with a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) in two different ways:

- A [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) can be a direct member of a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0).
- A [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) can be a member of a shared [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) that is hosted inside a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0).

Inherits from [teamInfo](https://learn.microsoft.com/en-us/graph/api/resources/teaminfo?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List your associated teams](https://learn.microsoft.com/en-us/graph/api/associatedteaminfo-list?view=graph-rest-1.0) | [associatedTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/associatedteaminfo?view=graph-rest-1.0) collection | Get the list of [teams](https://learn.microsoft.com/en-us/graph/api/resources/associatedteaminfo?view=graph-rest-1.0) in Microsoft Teams that a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) is associated with. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). Inherited from [teamInfo](https://learn.microsoft.com/en-us/graph/api/resources/teaminfo?view=graph-rest-1.0). |
| id | String | The unique identifier for the [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). Read-only. |
| tenantId | String | The ID of the Microsoft Entra tenant. Inherited from [teamInfo](https://learn.microsoft.com/en-us/graph/api/resources/teaminfo?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.associatedTeamInfo",
  "displayName": "String",
  "id": "String (identifier)",
  "tenantId": "String"
}
```

## Related content

- [Get team](https://learn.microsoft.com/en-us/graph/api/team-get?view=graph-rest-1.0)
