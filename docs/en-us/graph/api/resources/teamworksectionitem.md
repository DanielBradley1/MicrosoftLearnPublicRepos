<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# teamworkSectionItem resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an item, such as a chat, channel, meeting, or community, that is organized within a [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) in a user's Microsoft Teams chat list. Each item belongs to exactly one section at a time. Use the [move](https://learn.microsoft.com/en-us/graph/api/teamworksectionitem-move?view=graph-rest-beta) action to relocate an item to a different section.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/teamworksection-list-items?view=graph-rest-beta) | [teamworkSectionItem](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) collection | Get the list of [items](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) in a [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) of a user's [teamwork](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-beta). |
| [Add](https://learn.microsoft.com/en-us/graph/api/teamworksection-post-items?view=graph-rest-beta) | [teamworkSectionItem](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) | Add an [item](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta), such as a chat, channel, meeting, or community, to a user-defined [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) in a user's [teamwork](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-beta). |
| [Remove](https://learn.microsoft.com/en-us/graph/api/teamworksectionitem-delete?view=graph-rest-beta) | None | Remove an [item](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) from a user-defined [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) in a user's [teamwork](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-beta). |
| [Move](https://learn.microsoft.com/en-us/graph/api/teamworksectionitem-move?view=graph-rest-beta) | [teamworkSectionItem](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) | Move an [item](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) from one user-defined [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) to another user-defined section in a user's [teamwork](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-beta). |
| [Reorder](https://learn.microsoft.com/en-us/graph/api/teamworksectionitem-reorder?view=graph-rest-beta) | [teamworkSectionItem](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) collection | Reorder all [items](https://learn.microsoft.com/en-us/graph/api/resources/teamworksectionitem?view=graph-rest-beta) in a user-defined [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) in a user's [teamwork](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Date and time when the item was added to the section. Read-only. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. |
| id | String | The unique identifier for the item. This corresponds to the conversation ID of the underlying chat, channel, meeting, or community. For community items, the service automatically normalizes the ID to the `19:{id}@EngageCommunity` format. Read-only. |
| itemType | [sectionItemType](#sectionitemtype-values) | The type of the item. The possible values are: `chat`, `channel`, `meeting`, `community`, `unknownFutureValue`. Read-only. |
| lastModifiedDateTime | DateTimeOffset | Date and time when the item was last modified. Read-only. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2024, is `2024-01-01T00:00:00Z`. |

### sectionItemType values

| Member | Description |
| :--- | :--- |
| chat | A one-on-one or group chat conversation. |
| channel | A channel in a team. |
| meeting | A meeting chat. |
| community | A community conversation. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkSectionItem",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "itemType": "String",
  "lastModifiedDateTime": "String (timestamp)"
}
```

## Related content

- [teamworkSection resource type](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta)
- [userTeamwork resource type](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-beta)
