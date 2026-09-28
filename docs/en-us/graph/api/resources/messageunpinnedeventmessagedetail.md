<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/messageunpinnedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# messageUnpinnedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about an unpinned [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). This message is generated when a chat message is unpinned.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| eventDateTime | DateTimeOffset | Date and time when the event occurred. |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.messageUnpinnedEventMessageDetail",
  "eventDateTime": "String (timestamp)",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about an unpinned chat message](https://learn.microsoft.com/en-us/graph/system-messages/#message-unpinned)
- [System messages](https://learn.microsoft.com/en-us/graph/system-messages)
