<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/aaduserconversationmember?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-09 -->

# aadUserConversationMember resource type

Namespace: microsoft.graph

Represents a Microsoft Entra user in a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0), a [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0), or a [chat](https://learn.microsoft.com/en-us/graph/api/resources/chat?view=graph-rest-1.0). This type inherits from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0).

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
| email | string | The email address of the user. |
| id | String | Read-only. Unique ID of the user. |
| roles | string collection | The roles of the user such as owner, member, or guest. |
| tenantId | string | The tenant ID of the Microsoft Entra user. |
| userId | string | The user ID of the Microsoft Entra user. |
| visibleHistoryStartDateTime | DateTimeOffset | The timestamp that denotes how far back a conversation's history is shared with the conversation member. This property is settable only for members of a chat. |

### Instance attributes

Instance attributes are properties with special behaviors. These properties are temporary and either a\) define behavior the service should perform or b\) provide short-term property values, like a download URL for an item that expires.

| Property name | Type | Description |
| :--- | :--- | :--- |
| @microsoft.graph.originalSourceMembershipUrl | String | This annotation represents the URL of the original source membership that distinguishes between direct and indirect members. Use this annotation with the [List allMembers](https://learn.microsoft.com/en-us/graph/api/channel-list-allmembers?view=graph-rest-1.0) API. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.aadUserConversationMember",
  "displayName" : "string",
  "email" : "string",
  "id": "string (identifier)",
  "roles" : ["string"],
  "tenantId": "string",
  "userId" : "string",
  "visibleHistoryStartDateTime": "string (timestamp)"
}
```
