<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/membersaddedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# membersAddedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about [members](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) added. This message is generated when **members** are added to a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0), a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0), or a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). The **visibleHistoryStartDateTime** property for an event about **members** added to a **channel** is always set to `0001-01-01T00:00:00Z`, which indicates that all history is shared.

> **Note**: The **visibleHistoryStartDateTime** property for a [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) and the **membersAddedEventMessageDetail** message might have different values if the selected **shareHistoryTime** value for **members** in a **chat** is earlier than the initiator’s visible history time.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |
| members | [teamworkUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkuseridentity?view=graph-rest-1.0) collection | List of **members** added. |
| visibleHistoryStartDateTime | DateTimeOffset | The timestamp that denotes how far back a conversation's history is shared with the conversation members. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.membersAddedEventMessageDetail",
  "members": [
    {
      "@odata.type": "microsoft.graph.teamworkUserIdentity"
    }
  ],
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "visibleHistoryStartDateTime": "String (timestamp)"
}
```

## Related content

- [Example response for an event message about **members** added](https://learn.microsoft.com/en-us/graph/system-messages/#members-added)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
