<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-23 -->

# conversationMember resource type

Namespace: microsoft.graph

Represents a user in a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0), a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0), or a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0).

Base type for the following supported conversation member types:

- [aadUserConversationMember](https://learn.microsoft.com/en-us/graph/api/resources/aaduserconversationmember?view=graph-rest-1.0)
- [anonymousGuestConversationMember](https://learn.microsoft.com/en-us/graph/api/resources/anonymousguestconversationmember?view=graph-rest-1.0)
- [azureCommunicationServicesUserConversationMember](https://learn.microsoft.com/en-us/graph/api/resources/azurecommunicationservicesuserconversationmember?view=graph-rest-1.0)
- [microsoftAccountUserConversationMember](https://learn.microsoft.com/en-us/graph/api/resources/microsoftaccountuserconversationmember?view=graph-rest-1.0)
- [skypeForBusinessUserConversationMember](https://learn.microsoft.com/en-us/graph/api/resources/skypeforbusinessuserconversationmember?view=graph-rest-1.0)
- [skypeUserConversationMember](https://learn.microsoft.com/en-us/graph/api/resources/skypeuserconversationmember?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List team members](https://learn.microsoft.com/en-us/graph/api/team-list-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | Get the list of members in the team. |
| [Add team member](https://learn.microsoft.com/en-us/graph/api/team-post-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) | Add a new member to the team. |
| [Get team member](https://learn.microsoft.com/en-us/graph/api/team-get-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | Get a member in the team. |
| [Update team member's role](https://learn.microsoft.com/en-us/graph/api/team-update-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) | Change a member to an owner or back to a regular member. |
| [Remove team member](https://learn.microsoft.com/en-us/graph/api/team-delete-members?view=graph-rest-1.0) | None | Remove an existing member from the team. |
| [Remove team members in bulk](https://learn.microsoft.com/en-us/graph/api/conversationmember-remove?view=graph-rest-1.0) | [actionResultPart](https://learn.microsoft.com/en-us/graph/api/resources/actionresultpart?view=graph-rest-1.0) collection | Remove multiple members from a team in a single request. |
| [List channel members](https://learn.microsoft.com/en-us/graph/api/channel-list-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | Get the list of all members in a channel. |
| [Add channel member](https://learn.microsoft.com/en-us/graph/api/channel-post-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) | Add a member to a channel. Only supported for `channel` with membershipType of `private`. |
| [Get channel member](https://learn.microsoft.com/en-us/graph/api/channel-get-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | Get a member in a channel. |
| [Update channel member's role](https://learn.microsoft.com/en-us/graph/api/channel-update-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) | Update the properties of a member of the channel. Only supported for channel with membershipType of `private`. |
| [Remove channel member](https://learn.microsoft.com/en-us/graph/api/channel-delete-members?view=graph-rest-1.0) | None | Delete a member from a channel. Only supported for `channelType` of `private`. |
| [List chat members](https://learn.microsoft.com/en-us/graph/api/chat-list-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) collection | Get the list of all members in a chat. |
| [Add chat member](https://learn.microsoft.com/en-us/graph/api/chat-post-members?view=graph-rest-1.0) | Location header | Add a member to a chat. |
| [Get chat member](https://learn.microsoft.com/en-us/graph/api/chat-get-members?view=graph-rest-1.0) | [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0) | Get a member in a chat. |
| [Remove chat member](https://learn.microsoft.com/en-us/graph/api/chat-delete-members?view=graph-rest-1.0) | None | Remove a member from a chat. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | string | The display name of the user. |
| id | String | Read-only. Unique ID of the user. |
| roles | string collection | The roles for that user. This property contains more qualifiers only when relevant - for example, if the member has `owner` privileges, the **roles** property contains `owner` as one of the values. Similarly, if the member is an in-tenant guest, the **roles** property contains `guest` as one of the values. A basic member shouldn't have any values specified in the **roles** property. An Out-of-tenant external member is assigned the `owner` role. |
| visibleHistoryStartDateTime | DateTimeOffset | The timestamp denoting how far back a conversation's history is shared with the conversation member. This property is settable only for members of a chat. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conversationMember",
  "displayName": "String",
  "id": "String (identifier)",
  "roles": [
    "String"
  ],
  "visibleHistoryStartDateTime": "String (timestamp)"
}
```

## Related content

- [aadUserConversationMember](https://learn.microsoft.com/en-us/graph/api/resources/aaduserconversationmember?view=graph-rest-1.0)
- [skypeForBusinessUserConversationMember](https://learn.microsoft.com/en-us/graph/api/resources/skypeforbusinessuserconversationmember?view=graph-rest-1.0)
- [anonymousGuestConversationMember](https://learn.microsoft.com/en-us/graph/api/resources/anonymousguestconversationmember?view=graph-rest-1.0)
- [skypeUserConversationMember](https://learn.microsoft.com/en-us/graph/api/resources/skypeuserconversationmember?view=graph-rest-1.0)
- [microsoftAccountUserConversationMember](https://learn.microsoft.com/en-us/graph/api/resources/microsoftaccountuserconversationmember?view=graph-rest-1.0)
- [azureCommunicationServicesUserConversationMember](https://learn.microsoft.com/en-us/graph/api/resources/azurecommunicationservicesuserconversationmember?view=graph-rest-1.0)
