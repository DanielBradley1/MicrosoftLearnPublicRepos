<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/muteparticipantoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# MuteParticipantOperation resource type

Namespace: microsoft.graph

Describes the response format of a call participant mute operation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientContext | String | Unique client context string. Can have a maximum of 256 characters. |
| id | String | The server operation ID. Read-only. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | The result information. Read-only. |
| status | String | The possible values are: `notStarted`, `running`, `completed`, `failed`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "clientContext": "String",
  "id": "String (identifier)",
  "resultInfo": {"@odata.type": "#microsoft.graph.resultInfo"},
  "status": "notStarted | running | completed | failed"
}
```
