<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkbot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# teamworkBot resource type

Namespace: microsoft.graph

Represents a bot in the Microsoft Teams ecosystem.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get bot](https://learn.microsoft.com/en-us/graph/api/teamworkbot-get?view=graph-rest-1.0) | [teamworkBot](https://learn.microsoft.com/en-us/graph/api/resources/teamworkbot?view=graph-rest-1.0) | Read the properties and relationships of a [teamworkBot](https://learn.microsoft.com/en-us/graph/api/resources/teamworkbot?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of the bot associated with the specific [teamsAppDefinition](https://learn.microsoft.com/en-us/graph/api/resources/teamsappdefinition?view=graph-rest-1.0). This value is usually a GUID. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkBot",
  "id": "String (identifier)"
}
```

## Related content

- To get bots installed in a team, see example 2 in [List apps in team](https://learn.microsoft.com/en-us/graph/api/team-list-installedapps?view=graph-rest-1.0).
- To get bots installed in the personal scope of a user, see example 2 in [List apps installed for user](https://learn.microsoft.com/en-us/graph/api/userteamwork-list-installedapps?view=graph-rest-1.0).
