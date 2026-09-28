<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamwork?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-28 -->

# teamwork resource type

Namespace: microsoft.graph

A container for the range of Microsoft Teams functionalities that are available for the organization.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/teamwork-list-deletedteams?view=graph-rest-1.0) | [deletedTeam](https://learn.microsoft.com/en-us/graph/api/resources/deletedteam?view=graph-rest-1.0) collection | Get a list of the [deletedTeam](https://learn.microsoft.com/en-us/graph/api/resources/deletedteam?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/teamwork-get?view=graph-rest-1.0) | [teamwork](https://learn.microsoft.com/en-us/graph/api/resources/teamwork?view=graph-rest-1.0) | Get the properties and relationships of a teamwork object, such as the region of the organization and whether Microsoft Teams is enabled. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | The default teamwork identifier. |
| isTeamsEnabled | Boolean | Indicates whether Microsoft Teams is enabled for the organization. |
| region | string | Represents the region of the organization or the tenant. The **region** value can be any region supported by the Teams payload. The possible values are: `Americas`, `Europe and MiddleEast`, `Asia Pacific`, `UAE`, `Australia`, `Brazil`, `Canada`, `Switzerland`, `Germany`, `France`, `India`, `Japan`, `South Korea`, `Norway`, `Singapore`, `United Kingdom`, `South Africa`, `Sweden`, `Qatar`, `Poland`, `Italy`, `Israel`, `Spain`, `Mexico`, `USGov Community Cloud`, `USGov Community Cloud High`, `USGov Department of Defense`, and `China`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| deletedTeams | [deletedTeam](https://learn.microsoft.com/en-us/graph/api/resources/deletedteam?view=graph-rest-1.0) collection | The deleted team. |
| deletedChats | [deletedChat](https://learn.microsoft.com/en-us/graph/api/resources/deletedchat?view=graph-rest-1.0) collection | A collection of deleted chats. |
| teamsAppSettings | [teamsAppSettings](https://learn.microsoft.com/en-us/graph/api/resources/teamsappsettings?view=graph-rest-1.0) | Represents tenant-wide settings for all [Teams apps](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) in the tenant. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.teamwork",
    "id": "String",
    "isTeamsEnabled": "boolean",
    "region": "String"
}
```

## Related content

- [userTeamwork resource](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-1.0)
