<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/skypeuserconversationmember?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# skypeUserConversationMember resource type

Namespace: microsoft.graph

Represents a Skype \(consumer\) user in a chat.

For information about Teams and Skype for Business interoperability, see [Understand Microsoft Teams and Skype for Business coexistence and interoperability](https://learn.microsoft.com/en-us/microsoftteams/teams-and-skypeforbusiness-coexistence-and-interoperability).

Inherits from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the user. Inherited from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0). |
| id | String | Membership ID that represents this resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| roles | String collection | Special roles for this user. Inherited from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0). |
| skypeId | String | Skype ID of the user. |
| visibleHistoryStartDateTime | DateTimeOffset | The timestamp denoting how far back a conversation's history is shared with the conversation member. Inherited from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.skypeUserConversationMember",
  "id": "String (identifier)",
  "roles": [
    "String"
  ],
  "displayName": "String",
  "visibleHistoryStartDateTime": "String (timestamp)",
  "skypeId": "String"
}
```
