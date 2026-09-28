<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatmessage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# plannerTaskChatMessage resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a chat message associated with a [plannerTask](https://learn.microsoft.com/en-us/graph/api/resources/plannertask?view=graph-rest-beta). Task chat messages allow users to communicate and collaborate directly within the context of a task.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List messages](https://learn.microsoft.com/en-us/graph/api/plannertask-list-messages?view=graph-rest-beta) | [plannerTaskChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatmessage?view=graph-rest-beta) collection | Get the chat messages associated with a Planner task. |
| [Create message](https://learn.microsoft.com/en-us/graph/api/plannertask-post-messages?view=graph-rest-beta) | [plannerTaskChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatmessage?view=graph-rest-beta) | Create a new chat message on a Planner task. |
| [Update message](https://learn.microsoft.com/en-us/graph/api/plannertaskchatmessage-update?view=graph-rest-beta) | [plannerTaskChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatmessage?view=graph-rest-beta) | Update the properties of a chat message. |
| [Delete message](https://learn.microsoft.com/en-us/graph/api/plannertaskchatmessage-delete?view=graph-rest-beta) | None | Delete a chat message from a Planner task. |
| [Set reaction](https://learn.microsoft.com/en-us/graph/api/plannertaskchatmessage-setreaction?view=graph-rest-beta) | None | Set a reaction to a chat message. |
| [Unset reaction](https://learn.microsoft.com/en-us/graph/api/plannertaskchatmessage-unsetreaction?view=graph-rest-beta) | None | Remove a reaction from a chat message. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | The content of the chat message. Supports plain text and sanitized HTML. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the user who created the message. |
| createdDateTime | DateTimeOffset | The date and time when the message was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| deletedTime | DateTimeOffset | The date and time when the message was deleted. `null` if the message hasn't been deleted. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. |
| editedTime | DateTimeOffset | The date and time when the message was last edited. `null` if the message hasn't been edited. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. |
| id | String | Read-only. The unique identifier of the message. |
| mentions | [plannerTaskChatMention](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatmention?view=graph-rest-beta) collection | The list of mentions in the message. |
| messageType | plannerTaskChatMessageType | The type of message. The possible values are: `richTextHtml`, `unknownFutureValue`. |
| parentEntityId | String | The ID of the parent plannerTask that this message belongs to. |
| reactions | [plannerTaskChatReaction](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatreaction?view=graph-rest-beta) collection | The reactions on the message. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerTaskChatMessage",
  "content": "String",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "deletedTime": "String (timestamp)",
  "editedTime": "String (timestamp)",
  "id": "String (identifier)",
  "mentions": [{"@odata.type": "microsoft.graph.plannerTaskChatMention"}],
  "messageType": "String",
  "parentEntityId": "String",
  "reactions": [{"@odata.type": "microsoft.graph.plannerTaskChatReaction"}]
}
```
