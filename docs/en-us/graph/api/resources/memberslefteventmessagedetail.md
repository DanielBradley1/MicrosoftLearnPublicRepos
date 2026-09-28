<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/memberslefteventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# membersLeftEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about [members](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) left. This message is generated when **members** leave a meeting [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0).

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |
| members | [teamworkUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkuseridentity?view=graph-rest-1.0) collection | List of **members** who left the **chat**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.membersLeftEventMessageDetail",
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

- [Example response for an event message about **members** left](https://learn.microsoft.com/en-us/graph/system-messages/#members-left)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
