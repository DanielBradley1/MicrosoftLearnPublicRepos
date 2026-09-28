<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/updaterecordingstatusoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# updateRecordingStatusOperation resource type

Namespace: microsoft.graph

Describes the response format of an update recording status action.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientContext | String | Unique client context string. Max limit is 256 chars. |
| id | String | Read-only. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | The result information. Read-only. |
| status | String | The possible values are: `notStarted`, `running`, `completed`, `failed`. |

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
