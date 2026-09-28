<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/phoneuserconversationmember?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-06-21 -->

# phoneUserConversationMember resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a phone user in a chat.

Inherits from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name. Always set to `null`. Inherited from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-beta). |
| id | String | The membership ID that represents this resource. Inherited from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-beta). |
| phoneNumber | String | The phone number of the conversation member. |
| roles | String collection | Special roles assigned to this conversation member. Inherited from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-beta). |
| visibleHistoryStartDateTime | DateTimeOffset | The timestamp that indicates how far back the conversation history is shared with the conversation member. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.phoneUserConversationMember",
  "displayName": "String",
  "id": "String (identifier)",
  "phoneNumber": "String",
  "roles": ["String"],
  "visibleHistoryStartDateTime": "String (timestamp)"
}
```
