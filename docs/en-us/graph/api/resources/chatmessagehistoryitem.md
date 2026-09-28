<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmessagehistoryitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# chatMessageHistoryItem resource type

Namespace: microsoft.graph

Represents activity history information for a message in a chat or a channel.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actions | chatMessageActions | The modification actions of a message item.The possible values are: `reactionAdded`, `reactionRemoved`, `actionUndefined`, `unknownFutureValue`. |
| modifiedDateTime | DateTimeOffset | The date and time when the message was modified. |
| reaction | [chatMessageReaction](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagereaction?view=graph-rest-1.0) | The reaction in the modified message. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.chatMessageHistoryItem",
  "modifiedDateTime": "String (timestamp)",
  "actions": "String",
  "reaction": {
    "@odata.type": "microsoft.graph.chatMessageReaction"
  }
}
```
