<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/messagepinnedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# messagePinnedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about a pinned [chatMessage](https://learn.microsoft.com/en-us/graph/api/resources/chatmessage?view=graph-rest-1.0). This message is generated when a chat message is pinned.

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
  "@odata.type": "#microsoft.graph.messagePinnedEventMessageDetail",
  "eventDateTime": "String (timestamp)",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about a pinned chat message](https://learn.microsoft.com/en-us/graph/system-messages/#message-pinned)
- [System messages](https://learn.microsoft.com/en-us/graph/system-messages)
