<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/membersjoinedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# membersJoinedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about [members](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) joined. This message is generated when **members** join a meeting [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0).

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |
| members | [teamworkUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkuseridentity?view=graph-rest-1.0) collection | List of **members** who joined the **chat**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.membersJoinedEventMessageDetail",
  "members": [
    {
      "@odata.type": "microsoft.graph.teamworkUserIdentity"
    }
  ],
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about **members** joined](https://learn.microsoft.com/en-us/graph/system-messages/#members-joined)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
