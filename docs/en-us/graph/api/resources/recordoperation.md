<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recordoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# recordOperation resource type

Namespace: microsoft.graph

This resource type contains information related to audio recording.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientContext | String | Unique Client Context string. Max limit is 256 chars. |
| id | String | The server operation id. Read-only. |
| recordingAccessToken | String | The access token required to retrieve the recording. |
| recordingLocation | String | The location where the recording is located. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | The result information. Read-only. |
| status | String | The possible values are: `notStarted`, `running`, `completed`, `failed`. Read-only. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "clientContext": "String",
  "id": "String (identifier)",
  "recordingAccessToken": "String",
  "recordingLocation": "String",
  "resultInfo": {"@odata.type": "#microsoft.graph.resultInfo"},
  "status": "notStarted | running | completed | failed"
}
```
