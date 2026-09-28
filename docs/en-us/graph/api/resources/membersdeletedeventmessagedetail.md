<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/membersdeletedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# membersDeletedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about [members](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) deleted. This message is generated when **members** are removed from a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0), a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0), or a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0).

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |
| members | [teamworkUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkuseridentity?view=graph-rest-1.0) collection | List of **members** deleted. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.membersDeletedEventMessageDetail",
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

- [Example response for an event message about **members** deleted](https://learn.microsoft.com/en-us/graph/system-messages/#members-deleted)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
