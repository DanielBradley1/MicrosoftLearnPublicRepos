<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatreactionevent?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-19 -->

# plannerTaskChatReactionEvent resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a user's reaction event on a [plannerTaskChatMessage](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskchatmessage?view=graph-rest-beta). This resource captures the user who added the reaction and the timestamp when the reaction was added.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the reaction was added. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| user | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | The identity of the user who added the reaction. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.plannerTaskChatReactionEvent",
  "createdDateTime": "String (timestamp)",
  "user": {"@odata.type": "microsoft.graph.identitySet"}
}
```
