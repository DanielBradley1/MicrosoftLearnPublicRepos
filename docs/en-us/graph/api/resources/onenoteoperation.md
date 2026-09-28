<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onenoteoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# onenoteOperation resource type

Namespace: microsoft.graph

The status of certain long-running OneNote operations.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdDateTime": "String (timestamp)",
  "error": {"@odata.type": "microsoft.graph.onenoteOperationError"},
  "id": "string (identifier)",
  "lastActionDateTime": "String (timestamp)",
  "resourceId": "string",
  "resourceLocation": "string",
  "status": "string",
  "percentComplete": "string"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The start time of the operation. |
| error | [onenoteOperationError](https://learn.microsoft.com/en-us/graph/api/resources/onenoteoperationerror?view=graph-rest-1.0) | The error returned by the operation. |
| id | string | The operation id. Read-only. |
| lastActionDateTime | DateTimeOffset | The time of the last action of the operation. |
| percentComplete | string | The operation percent complete if the operation is still in `running` status. |
| resourceId | string | The resource id. |
| resourceLocation | string | The resource URI for the object. For example, the resource URI for a copied page or section. |
| status | operationStatus | The current status of the operation: `NotStarted`, `Running`, `Completed`, `Failed`. |

## Relationships

None

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get operation](https://learn.microsoft.com/en-us/graph/api/onenoteoperation-get?view=graph-rest-1.0) | [onenoteOperation](https://learn.microsoft.com/en-us/graph/api/resources/onenoteoperation?view=graph-rest-1.0) | Get the status of the operation. |
