<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetingengagementconversation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-25 -->

# onlineMeetingEngagementConversation resource type

Namespace: microsoft.graph

Represents a structured question-and-answer \(Q&A\) thread in Teams that is directly associated with an online meeting.

Inherits from [engagementConversation](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversation?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get all online meeting messages](https://learn.microsoft.com/en-us/graph/api/cloudcommunications-getallonlinemeetingmessages?view=graph-rest-1.0) | [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0) collection | Get all Teams question and answer \(Q&A\) conversation messages in a tenant. |
| [List reactions](https://learn.microsoft.com/en-us/graph/api/engagementconversationdiscussionmessage-list-reactions?view=graph-rest-1.0) | [engagementConversationMessageReaction](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessagereaction?view=graph-rest-1.0) collection | Get a list of the [engagementConversationMessageReaction](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessagereaction?view=graph-rest-1.0) objects and their properties for an [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0) in an online meeting. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| creationMode | [engagementCreationMode](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0#engagementcreationmode-values) | Don't use. This property is managed at [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0) level. Inherited from [engagementConversation](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversation?view=graph-rest-1.0). |
| id | String | The unique identifier for the conversation object. Inherited from [engagementConversation](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversation?view=graph-rest-1.0). |
| moderationState | [engagementConversationModerationState](#engagementconversationmoderationstate-values) | The moderation status of the conversation. The possible values are: `published`, `pendingReview`, `dismissed`, `unknownFutureValue`. |
| onlineMeetingId | String | The unique identifier of the online meeting associated with this conversation. The online meeting ID links the conversation to a specific meeting instance. |
| organizer | [engagementIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/engagementidentityset?view=graph-rest-1.0) | Unique identifier of the online meeting organizer. |
| starterId | String | The ID of the first message that initiated the Q&A conversation. Use this property to trace the origin of the thread. Inherited from [engagementConversation](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversation?view=graph-rest-1.0). |
| upvoteCount | Int32 | The number of upvotes the conversation received. |

### engagementConversationModerationState values

| Member | Description |
| :--- | :--- |
| published | The Q&A conversation is published and visible to all attendees. |
| pendingReview | The Q&A conversation awaits a moderator's review. |
| dismissed | A moderator reviewed and removed the Q&A conversation without publishing it to attendees. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| messages | [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0) collection | The collection of messages posted within the conversation. Inherited from [engagementConversation](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversation?view=graph-rest-1.0). |
| onlineMeeting | [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0) | The online meeting associated with the conversation. |
| starter | [engagementConversationMessage](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessage?view=graph-rest-1.0) | The initial message that started the conversation thread. Inherited from [engagementConversation](https://learn.microsoft.com/en-us/graph/api/resources/engagementconversation?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onlineMeetingEngagementConversation",
  "id": "String (identifier)",
  "moderationState": "String",
  "onlineMeetingId": "String",
  "organizer": {"@odata.type": "microsoft.graph.engagementIdentitySet"},
  "starterId": "String",
  "upvoteCount": "Int32"
}
```
