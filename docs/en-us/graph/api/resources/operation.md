<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/operation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# operation resource type

Namespace: microsoft.graph

The status of a long-running operation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The start time of the operation. |
| lastActionDateTime | DateTimeOffset | The time of the last action of the operation. |
| status | operationStatus | The current status of the operation: `notStarted`, `running`, `completed`, `failed` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdDateTime": "String (timestamp)",
  "lastActionDateTime": "String (timestamp)",
  "status": "notStarted | running | completed | failed"
}
```
