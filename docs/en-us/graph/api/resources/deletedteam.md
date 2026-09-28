<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/deletedteam?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# deletedTeam resource type

Namespace: microsoft.graph

A deleted team in Microsoft Teams is a collection of [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) objects. A channel represents a topic, and therefore a logical isolation of discussion, within a deleted team.

Every deleted team is associated with a [Microsoft 365 group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0). For more information about working with groups and members in teams, see [Use the Microsoft Graph REST API to work with Microsoft Teams](https://learn.microsoft.com/en-us/graph/api/resources/teams-api-overview?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get all messages](https://learn.microsoft.com/en-us/graph/api/deletedteam-getallmessages?view=graph-rest-1.0) | [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) collection | Get all messages in the deleted team. |
| [List](https://learn.microsoft.com/en-us/graph/api/teamwork-list-deletedteams?view=graph-rest-1.0) | [deletedTeam](https://learn.microsoft.com/en-us/graph/api/resources/deletedteam?view=graph-rest-1.0) collection | Get a list of the [deletedTeam](https://learn.microsoft.com/en-us/graph/api/resources/deletedteam?view=graph-rest-1.0) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID of a deleted team. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| channels | [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) collection | The channels that are either shared with this deleted team or created in this deleted team. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deletedTeam",
  "id": "String (identifier)"
}
```
