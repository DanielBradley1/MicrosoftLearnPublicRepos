<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmention?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# chatMention resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **mentions** property of the [chatMessageProperties](https://learn.microsoft.com/en-us/graph/api/resources/chatmessageproperties?view=graph-rest-beta) resource uses this type.

An @mention of a user or an application within a [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| index | Int32 | Character position of the mention within the message content. |
| mentioned | String | Identifier of the mentioned user or application. |
| type | chatMentionType | Type of the mentioned entity. The possible values are: `user`, `application`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.chatMention",
  "mentioned": "String",
  "index": "Int32",
  "type": "String"
}
```
