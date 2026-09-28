<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatrenamedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# chatRenamedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about a renamed [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0). This message is generated when a group or a meeting **chat** topic is updated.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| chatDisplayName | String | The updated name of the **chat**. |
| chatId | String | Unique identifier of the **chat**. |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.chatRenamedEventMessageDetail",
  "chatDisplayName": "String",
  "chatId": "String",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about a renamed **chat**](https://learn.microsoft.com/en-us/graph/system-messages/#chat-renamed)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
