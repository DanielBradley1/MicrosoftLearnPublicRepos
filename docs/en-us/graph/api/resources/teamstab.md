<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# teamsTab resource type

Namespace: microsoft.graph

Represents a tab pinned \(attached\) to a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) or a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0).

For more information about tabs, see [Build tabs for Teams](https://learn.microsoft.com/en-us/microsoftteams/platform/tabs/what-are-tabs).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List tabs in channel](https://learn.microsoft.com/en-us/graph/api/channel-list-tabs?view=graph-rest-1.0) | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) | List tabs pinned to a channel. |
| [Get tab in channel](https://learn.microsoft.com/en-us/graph/api/channel-get-tabs?view=graph-rest-1.0) | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) | Read a tab pinned to a channel. |
| [Add tab to channel](https://learn.microsoft.com/en-us/graph/api/channel-post-tabs?view=graph-rest-1.0) | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) | Add \(pin\) a tab to a channel. |
| [Update tab in channel](https://learn.microsoft.com/en-us/graph/api/channel-patch-tabs?view=graph-rest-1.0) | [teamsTab](https://learn.microsoft.com/en-us/graph/api/resources/teamstab?view=graph-rest-1.0) | Update the tab properties. |
| [Remove tab from channel](https://learn.microsoft.com/en-us/graph/api/channel-delete-tabs?view=graph-rest-1.0) | None | Remove \(unpin\) a tab from a channel. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| configuration | [teamsTabConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/teamstabconfiguration?view=graph-rest-1.0) | Container for custom settings applied to a tab. The tab is considered configured only once this property is set. |
| displayName | string | Name of the tab. |
| id | string | Identifier that uniquely identifies a specific instance of a channel tab. Read-only. |
| webUrl | string | Deep link URL of the tab instance. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| teamsApp | [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) | The application that is linked to the tab. This can't be changed after tab creation. |

## JSON representation

The following JSON representation shows the resource type.

```json
{  
  "id": "string",
  "displayName": "string",
  "webUrl": "string",
  "configuration" : "teamsTabConfiguration"
}
```

## Related content

[Configuring the built-in tab types](https://learn.microsoft.com/en-us/graph/teams-configuring-builtin-tabs)
