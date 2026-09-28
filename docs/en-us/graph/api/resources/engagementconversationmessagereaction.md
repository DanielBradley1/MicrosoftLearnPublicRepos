<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/engagementconversationmessagereaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-25 -->

# engagementConversationMessageReaction resource type

Namespace: microsoft.graph

Represents a reaction \(for example, like, love, or celebrate\) to a message in a Viva Engage conversation.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Date and time when the reaction was added. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | Unique identifier of a reaction posted to a Viva Engage conversation message. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| reactionBy | [engagementIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/engagementidentityset?view=graph-rest-1.0) | Identity of the user who added the reaction. |
| reactionType | engagementConversationMessageReactionType | The type of the reaction. The possible values are: `like`, `love`, `celebrate`, `thank`, `laugh`, `sad`, `happy`, `excited`, `smile`, `silly`, `intenseLaugh`, `starStruck`, `goofy`, `thinking`, `surprised`, `mindBlown`, `scared`, `crying`, `shocked`, `angry`, `agree`, `praise`, `takingNotes`, `heartBroken`, `support`, `confirmed`, `watching`, `brain`, `medal`, `bullseye`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.engagementConversationMessageReaction",
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "reactionBy": {"@odata.type": "microsoft.graph.engagementIdentitySet"},
  "reactionType": "String"
}
```
