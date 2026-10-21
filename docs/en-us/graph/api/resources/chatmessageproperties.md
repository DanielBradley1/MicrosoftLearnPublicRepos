<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmessageproperties?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# chatMessageProperties resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **properties** property of the [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta) resource uses this type.

Formatting and metadata properties of a [plannerChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannerchatmessage?view=graph-rest-beta), including @mentions and reactions.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| mentions | [chatMention](https://learn.microsoft.com/en-us/graph/api/resources/chatmention?view=graph-rest-beta) collection | Collection of @mentions in the message. |
| reactions | [chatReaction](https://learn.microsoft.com/en-us/graph/api/resources/chatreaction?view=graph-rest-beta) collection | Collection of reactions applied to the message. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.chatMessageProperties",
  "mentions": [
    {
      "@odata.type": "microsoft.graph.chatMention"
    }
  ],
  "reactions": [
    {
      "@odata.type": "microsoft.graph.chatReaction"
    }
  ]
}
```
