<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/playpromptoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# playPromptOperation resource type

Namespace: microsoft.graph

The playPrompt operation to obtain the result of the playPrompt action.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientContext | String | Unique Client Context string. Max limit is 256 chars. |
| id | String | Read-only. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | The result information. Read-only. |
| status | String | The possible values are: `notStarted`, `running`, `completed`, `failed`. |

## Relationships

None

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
