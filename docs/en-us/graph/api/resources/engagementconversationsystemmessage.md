<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationsystemmessage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-25 -->

# engagementConversationSystemMessage resource type

Namespace: microsoft.graph

Represents an individual system message in a Viva Engage conversation.

Inherits from [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| body | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | The main content of the message. Inherited from [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time when the message was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0). |
| creationMode | [engagementCreationMode](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0#engagementcreationmode-values) | Indicates how the message was created. The possible values are: `none`, `migration`, `unknownFutureValue`. Inherited from [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0). |
| from | [engagementIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/engagementidentityset?view=graph-rest-1.0) | Identity of the sender of the message. Inherited from [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0). |
| id | String | Unique ID of a Viva Engage conversation message. Inherited from [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time when message was last modified. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0). |
| replyToId | String | The ID of the parent message to which this message is a reply, if applicable. Inherited from [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| conversation | [engagementConversation](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversation?view=graph-rest-1.0) | The Viva Engage conversation to which this message belongs. This relationship establishes the thread context for the message. Inherited from [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0). |
| reactions | [engagementConversationMessageReaction](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessagereaction?view=graph-rest-1.0) collection | A collection of reactions \(such as like and smile\) that users have applied to this message. Inherited from [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0). |
| replies | [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0) collection | A collection of messages that are replies to this message and form a threaded discussion. Inherited from [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0). |
| replyTo | [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0) | The parent message to which this message is a reply, if it is part of a reply chain. Inherited from [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.engagementConversationDiscussionMessage",
  "body": {"@odata.type": "microsoft.graph.itemBody"},
  "createdDateTime": "String (timestamp)",
  "creationMode": "String",
  "from": {"@odata.type": "microsoft.graph.engagementIdentitySet"},
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "replyToId": "String"
}
```
