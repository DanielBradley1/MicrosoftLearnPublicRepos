<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/inviteparticipantsoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# inviteParticipantsOperation resource type

Namespace: microsoft.graph

Represents the status of a long-running participant invitation operation, triggered by a call to the participant-invite API.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientContext | String | The client context. |
| id | String | The server operation id. Read-only. |
| participants | [invitationParticipantInfo](https://learn.microsoft.com/en-us/graph/api/resources/invitationparticipantinfo?view=graph-rest-1.0) collection | The participants to invite. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | The result information. Read-only. |
| status | String | The possible values are: `notStarted`, `running`, `completed`, `failed`. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "clientContext": "String",
  "id": "String (identifier)",
  "participants": [{"@odata.type": "#microsoft.graph.invitationParticipantInfo"}],
  "resultInfo": {"@odata.type": "#microsoft.graph.resultInfo"},
  "status": "notStarted | running | completed | failed"
}
```
