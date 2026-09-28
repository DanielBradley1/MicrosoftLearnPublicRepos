<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmessageinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-25 -->

# chatMessageInfo resource type

Namespace: microsoft.graph

Represents a preview of a [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0) resource. This object can only be fetched as part of a list of [chats](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| body | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | Body of the [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). This will still contain markers for @mentions and attachments even though the object doesn't return @mentions and attachments. |
| createdDateTime | DateTimeOffset | Date time object representing the time at which message was created. |
| eventDetail | [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0) | Read-only. If present, represents details of an event that happened in a chat, a channel, or a team, for example, members were added, and so on. For event messages, the **messageType** property is set to `systemEventMessage`. |
| from | [chatMessageFromIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagefromidentityset?view=graph-rest-1.0) | Information about the sender of the message. |
| id | String | ID of the [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). |
| isDeleted | Boolean | If set to `true`, the original message has been deleted. |
| messageType | chatMessageType | The type of chat message. The possible values are: `message`, `unknownFutureValue`, `systemEventMessage`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.chatMessageInfo",
  "body": {
    "@odata.type": "microsoft.graph.itemBody"
  },
  "createdDateTime": "String (timestamp)",
  "eventDetail": {
    "@odata.type": "microsoft.graph.eventMessageDetail"
  },
  "from": {
    "@odata.type": "microsoft.graph.chatMessageFromIdentitySet"
  },
  "id": "String (identifier)",
  "isDeleted": "Boolean",
  "messageType": "String"
}
```

## Related content

- [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0)
- [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0)
