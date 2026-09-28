<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingpolicyupdatedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# meetingPolicyUpdatedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about an updated meeting policy. This message is generated when the meeting option **Allow meeting chat** is updated.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |
| meetingChatEnabled | Boolean | Represents whether the meeting [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0) is enabled or not. |
| meetingChatId | String | Unique identifier of the meeting **chat**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.meetingPolicyUpdatedEventMessageDetail",
  "meetingChatId": "String",
  "meetingChatEnabled": "Boolean",
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about an updated meeting policy](https://learn.microsoft.com/en-us/graph/system-messages/#meeting-policy-updated)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
