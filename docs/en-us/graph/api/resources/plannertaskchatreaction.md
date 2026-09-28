<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatreaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# plannerTaskChatReaction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a reaction to a [plannerTaskChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatmessage?view=graph-rest-beta). Users can react to task chat messages to express feedback without adding a new message.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| reactionType | String | The type of reaction, such as `like`, `heart`, or emoji characters. |
| users | [plannerTaskChatReactionEvent](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatreactionevent?view=graph-rest-beta) collection | The list of users who added this reaction and when they reacted. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerTaskChatReaction",
  "reactionType": "String",
  "users": [{"@odata.type": "microsoft.graph.plannerTaskChatReactionEvent"}]
}
```
