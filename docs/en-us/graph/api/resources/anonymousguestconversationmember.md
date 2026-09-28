<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/anonymousguestconversationmember?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# anonymousGuestConversationMember resource type

Namespace: microsoft.graph

Represents an anonymous guest in a chat.

Anonymous users don't have a Microsoft Teams identity and can join meetings using meeting join links. For more information, see [Anonymous users](https://learn.microsoft.com/en-us/microsoftteams/non-standard-users#anonymous-users).

Inherits from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| anonymousGuestId | String | Unique ID that represents the user. **Note:** This ID can change if the user leaves and rejoins the meeting, or joins from a different device. |
| displayName | String | Name provided by the user when joining the meeting. Inherited from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0). |
| id | String | Membership ID that represents this resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| roles | String collection | Special roles for this user. Inherited from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0). |
| visibleHistoryStartDateTime | DateTimeOffset | The timestamp denoting how far back a conversation's history is shared with the conversation member. Inherited from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.anonymousGuestConversationMember",
  "id": "String (identifier)",
  "roles": [
    "String"
  ],
  "displayName": "String",
  "visibleHistoryStartDateTime": "String (timestamp)",
  "anonymousGuestId": "String"
}
```
