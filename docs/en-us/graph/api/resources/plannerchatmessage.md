<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# plannerChatMessage resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A chat message associated with a [task](https://learn.microsoft.com/en-us/graph/api/resources/task?view=graph-rest-beta) or a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta), surfaced on the task through the `messages` navigation property.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/task-list-messages?view=graph-rest-beta) | [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta) collection | Get a list of the plannerChatMessage objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/task-post-messages?view=graph-rest-beta) | [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta) | Create a new plannerChatMessage object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/plannerchatmessage-get?view=graph-rest-beta) | [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta) | Read the properties and relationships of [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/plannerchatmessage-update?view=graph-rest-beta) | [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta) | Update the properties of a plannerChatMessage object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | String | Body content of the chat message. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user \(or application\) who created the entity. Read-only. |
| createdDateTime | DateTimeOffset | Date and time the entity was created. The value is represented in ISO 8601 format and is always in UTC time. Read-only. |
| deletedTime | DateTimeOffset | Date and time the message was deleted. |
| editedTime | DateTimeOffset | Date and time the message was last edited. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| isDeleted | Boolean | Indicates whether the message was deleted. |
| isEdited | Boolean | Indicates whether the message was edited after it was sent. |
| messageType | plannerChatMessageType | Format of the message content. The possible values are: `richTextHtml`, `plainText`, `unknownFutureValue`. |
| parentEntityId | String | ID of the task or plan the message belongs to. |
| properties | [chatMessageProperties](https://learn.microsoft.com/en-us/graph/api/resources/chatmessageproperties?view=graph-rest-beta) | @mentions and reactions associated with the message. |
| threadType | plannerChatThreadType | Indicates whether the message belongs to a task-level or plan-level conversation. The possible values are: `task`, `plan`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerChatMessage",
  "id": "String (identifier)",
  "messageType": "String",
  "content": "String",
  "properties": {
    "@odata.type": "microsoft.graph.chatMessageProperties"
  },
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "threadType": "String",
  "parentEntityId": "String",
  "isDeleted": "Boolean",
  "deletedTime": "String (timestamp)",
  "isEdited": "Boolean",
  "editedTime": "String (timestamp)"
}
```
