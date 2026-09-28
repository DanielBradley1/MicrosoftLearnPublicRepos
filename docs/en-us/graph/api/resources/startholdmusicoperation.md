<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/startholdmusicoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# startHoldMusicOperation resource type

Namespace: microsoft.graph

Represents the status of a [startHoldMusic](https://learn.microsoft.com/en-us/graph/api/participant-startholdmusic?view=graph-rest-1.0) operation, triggered by a call to the **startHoldMusic** API. Inherits from [commsOperation](https://learn.microsoft.com/en-us/graph/api/resources/commsoperation?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientContext | String | Inherited from **commsOperation**. Unique client context string. Can have a maximum of 256 characters. |
| id | String | Inherited from **commsOperation**. The server operation ID. Read-only. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | Inherited from **commsOperation**. The result information. Read-only. |
| status | String | Inherited from **commsOperation**. The possible values are: `notStarted`, `running`, `completed`, `failed`. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "clientContext": "String",
  "id": "String (identifier)",
  "resultInfo": { "@odata.type": "microsoft.graph.resultInfo" },
  "status": "notStarted | running | completed | failed"
}
```
