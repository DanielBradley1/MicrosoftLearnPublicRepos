<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/azurecommunicationservicesuserconversationmember?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# azureCommunicationServicesUserConversationMember resource type

Namespace: microsoft.graph

Represents an Azure Communication Services user in a chat.

Azure Communication Services users can join Teams meetings and Teams chats as an external user.

Inherits from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| azureCommunicationServicesId | String | Azure Communication Services ID of the user. |
| displayName | String | Display name of the user. Inherited from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0). |
| id | String | Membership ID that represents this resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| roles | String collection | Special roles for this user. Inherited from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0). |
| visibleHistoryStartDateTime | DateTimeOffset | The timestamp denoting how far back a conversation's history is shared with the conversation member. Inherited from [conversationMember](https://learn.microsoft.com/en-us/graph/api/resources/conversationmember?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.azureCommunicationServicesUserConversationMember",
  "id": "String (identifier)",
  "roles": [
    "String"
  ],
  "displayName": "String",
  "visibleHistoryStartDateTime": "String (timestamp)",
  "azureCommunicationServicesId": "String"
}
```
