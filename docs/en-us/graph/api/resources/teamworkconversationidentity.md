<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkconversationidentity?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# teamworkConversationIdentity resource type

Namespace: microsoft.graph

Represents a **conversation** \(chat, team, or channel\) in Microsoft Teams.

Inherits from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| conversationIdentityType | teamworkConversationIdentityType | Type of conversation. The possible values are: `team`, `channel`, `chat`, and `unknownFutureValue`. |
| displayName | String | Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0). Display name of the conversation. Optional. |
| id | String | Inherited from [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0). ID of the conversation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkConversationIdentity",
  "id": "String (identifier)",
  "displayName": "String",
  "conversationIdentityType": "String"
}
```
