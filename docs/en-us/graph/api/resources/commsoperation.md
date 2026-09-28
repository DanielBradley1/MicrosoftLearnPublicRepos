<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/commsoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# commsOperation resource type

Namespace: microsoft.graph

Represents the status of certain long-running operations.

This resource can be returned as the response to an action, or as the content of a [commsNotification](https://learn.microsoft.com/en-us/graph/api/resources/commsnotification?view=graph-rest-1.0).

When it's returned as a response to an action, the status indicates whether there will be subsequent notifications. If for example, an operation with status of `completed` or `failed` is returned, there won't be any subsequent operation via the notification channel.

If an operation with a status of `notStarted`, `running` or `null` is returned, subsequent updates come via the notification channel.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientContext | String | Unique Client Context string. Max limit is 256 chars. |
| ID | String | The operation ID. Read-only. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | The result information. Read-only. |
| status | String | The possible values are: `notStarted`, `running`, `completed`, `failed`. Read-only. |

## Relationships

None

## JSON representation

The following example is a JSON representation of the resource.

```json
{
  "clientContext": "String",
  "id": "String (identifier)",
  "resultInfo": { "@odata.type": "microsoft.graph.resultInfo" },
  "status": "notStarted | running | completed | failed"
}
```
