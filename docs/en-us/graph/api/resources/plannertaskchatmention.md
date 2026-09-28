<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatmention?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# plannerTaskChatMention resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a mention in a [plannerTaskChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatmessage?view=graph-rest-beta). Mentions allow users to notify specific users within task chat messages.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| mentioned | String | The ID of the mentioned user. |
| mentionType | plannerTaskChatMentionType | The type of mention. The possible values are: `user`, `unknownFutureValue`. |
| position | Int32 | The zero-based position of the mention in the message content. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerTaskChatMention",
  "mentioned": "String",
  "mentionType": "String",
  "position": "Int32"
}
```
