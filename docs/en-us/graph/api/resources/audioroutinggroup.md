<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/audioroutinggroup?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# audioRoutingGroup resource type

Namespace: microsoft.graph

The audio routing group stores a private audio route between participants in a multiparty conversation. Source is the participant itself and the receivers are a subset of other participants in the multiparty conversation.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/audioroutinggroup-get?view=graph-rest-1.0) | [audioRoutingGroup](https://learn.microsoft.com/en-us/graph/api/resources/audioroutinggroup?view=graph-rest-1.0) | Create audioRoutingGroup object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/audioroutinggroup-get?view=graph-rest-1.0) | [audioRoutingGroup](https://learn.microsoft.com/en-us/graph/api/resources/audioroutinggroup?view=graph-rest-1.0) | Read properties and relationships of audioRoutingGroup object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/audioroutinggroup-update?view=graph-rest-1.0) | [audioRoutingGroup](https://learn.microsoft.com/en-us/graph/api/resources/audioroutinggroup?view=graph-rest-1.0) | Update receivers list. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/audioroutinggroup-delete?view=graph-rest-1.0) | None | Delete the audio routing group. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | string | Read-only. |
| receivers | collection\(string\) | List of receiving participant ids. |
| routingMode | string | Routing group mode. The possible values are: `oneToOne`, `multicast`. |
| sources | collection\(string\) | List of source participant ids. |

> **Note:** Routing mode determines the restrictions on the sources and receivers. Only the following routing groups are supported.
> 
> - `oneToOne` - sources and receivers have only one participant each.
> - `multicast` - source has one participant but there are multiple receivers. Receivers list may be updated.

> **Note:** If you create many audio routing groups \(e.g., a bot per participant\), only the audio of the top 4 dominant speakers is forwarded. For example, if the speaker is not loud enough in the main mixer of a customized audio routing group, the bot will not hear it, even if there is a private audio group just for this speaker and the bot.

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string (identifier)",
  "receivers": [ "string" ],
  "routingMode": "oneToOne | multicast",
  "sources": [ "string" ]
}
```
