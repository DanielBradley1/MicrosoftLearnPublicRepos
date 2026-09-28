<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/engagementconversation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-25 -->

# engagementConversation resource type

Namespace: microsoft.graph

An abstract type that represents a conversation in Viva Engage.

A Viva Engage conversation is a threaded discussion within a Viva Engage scope, such as a community or a storyline, that enables users to post messages, reply, react, and share content in a structured, persistent format for enterprise social collaboration.

Base type of [onlineMeetingEngagementConversation](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingengagementconversation?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| creationMode | [engagementCreationMode](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0#engagementcreationmode-values) | Don't use. This property is managed at [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0) level. |
| id | String | The unique ID of a conversation in Viva Engage. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| starterId | String | The unique ID of the first message in a Viva Engage conversation. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| messages | [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0) collection | The messages in a Viva Engage conversation. |
| starter | [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0) | The first message in a Viva Engage conversation. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.engagementConversation",
  "creationMode": "String",
  "id": "String (identifier)",
  "starterId": "String"
}
```
