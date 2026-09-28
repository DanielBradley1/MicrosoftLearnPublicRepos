<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharedwithchannelteaminfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# sharedWithChannelTeamInfo resource type

Namespace: microsoft.graph

Represents information for a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) with which a channel is shared. A [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) can be shared multiple channels.

Inherits from [teamInfo](https://learn.microsoft.com/en-us/graph/api/resources/teaminfo?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List teams sharing a channel](https://learn.microsoft.com/en-us/graph/api/sharedwithchannelteaminfo-list?view=graph-rest-1.0) | [sharedWithChannelTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/sharedwithchannelteaminfo?view=graph-rest-1.0) collection | Get the list of [teams](https://learn.microsoft.com/en-us/graph/api/resources/sharedwithchannelteaminfo?view=graph-rest-1.0) that has been shared a specified [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0). |
| [Get team sharing a channel](https://learn.microsoft.com/en-us/graph/api/sharedwithchannelteaminfo-get?view=graph-rest-1.0) | [sharedWithChannelTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/sharedwithchannelteaminfo?view=graph-rest-1.0) | Get a [team](https://learn.microsoft.com/en-us/graph/api/resources/sharedwithchannelteaminfo?view=graph-rest-1.0) which has been shared a specified [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0). |
| [Unshare channel with team](https://learn.microsoft.com/en-us/graph/api/sharedwithchannelteaminfo-delete?view=graph-rest-1.0) | None | Unshare a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) with a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) by deleting the corresponding [sharedWithChannelTeamInfo](https://learn.microsoft.com/en-us/graph/api/resources/sharedwithchannelteaminfo?view=graph-rest-1.0) resource. |
| [List allowed members](https://learn.microsoft.com/en-us/graph/api/sharedwithchannelteaminfo-list-allowedmembers?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | Get the list of [conversationMembers](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) who can access a shared [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). Inherited from [teamInfo](https://learn.microsoft.com/en-us/graph/api/resources/teaminfo?view=graph-rest-1.0). |
| id | String | The unique identifier for the [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). Read-only. |
| isHostTeam | Boolean | Indicates whether the [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0) is the host of the [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0). |
| tenantId | String | The ID of the Microsoft Entra tenant. Inherited from [teamInfo](https://learn.microsoft.com/en-us/graph/api/resources/teaminfo?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| allowedMembers | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | A collection of team members who have access to the shared channel. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharedWithChannelTeamInfo",
  "displayName": "String",
  "id": "String (identifier)",
  "isHostTeam": "Boolean",
  "tenantId": "String"
}
```
