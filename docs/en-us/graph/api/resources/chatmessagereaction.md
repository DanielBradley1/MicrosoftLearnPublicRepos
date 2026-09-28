<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmessagereaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# chatMessageReaction resource type

Namespace: microsoft.graph

Represents a reaction to a [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) entity.

An entity of type `chatMessageReaction` is returned as part of the [Get channel message](https://learn.microsoft.com/en-us/graph/api/chatmessage-get?view=graph-rest-1.0) API, as a part of the [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) entity.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayName | String | The name of the reaction. |
| reactionContentUrl | String | The hosted content URL for the custom reaction type. |
| reactionType | String | The reaction type. Supported values include Unicode characters, `custom`, and some backward-compatible reaction types, such as `like`, `angry`, `sad`, `laugh`, `heart`, and `surprised`. |
| user | [chatMessageReactionIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagereactionidentityset?view=graph-rest-1.0) | The user who reacted to the message. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "reactionContentUrl": "String",
  "reactionType": "String",
  "user": {"@odata.type": "microsoft.graph.chatMessageReactionIdentitySet"}
}
```
