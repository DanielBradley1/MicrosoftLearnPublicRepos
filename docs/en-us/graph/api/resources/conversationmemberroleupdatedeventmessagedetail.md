<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conversationmemberroleupdatedeventmessagedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# conversationMemberRoleUpdatedEventMessageDetail resource type

Namespace: microsoft.graph

Represents the details of an event message about an updated role of a [conversation member](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) in a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) or a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). This message is generated when the role of a **member** in a **channel** or a **team** is updated.

Inherits from [eventMessageDetail](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagedetail?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| initiator | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Initiator of the event. |
| conversationMemberRoles | String collection | Roles for the **coversation member** user. |
| conversationMemberUser | [teamworkUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkuseridentity?view=graph-rest-1.0) | Identity of the **conversation member** user. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conversationMemberRoleUpdatedEventMessageDetail",
  "conversationMemberRoles": [
    "String"
  ],
  "conversationMemberUser": {
    "@odata.type": "microsoft.graph.teamworkUserIdentity"
  },
  "initiator": {
    "@odata.type": "microsoft.graph.identitySet"
  }
}
```

## Related content

- [Example response for an event message about an updated role of a **conversation member** in a **channel** or a **team**](https://learn.microsoft.com/en-us/graph/system-messages/#conversation-member-role-updated)
- For more information about other types of events, see [System messages](https://learn.microsoft.com/en-us/graph/system-messages).
