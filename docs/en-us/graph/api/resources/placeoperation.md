<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/placeoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# placeOperation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an upsert [places](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-beta) operation.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/place-listoperations?view=graph-rest-beta) | [placeOperation](https://learn.microsoft.com/en-us/graph/api/resources/placeoperation?view=graph-rest-beta) collection | List all existing [placeOperation](https://learn.microsoft.com/en-us/graph/api/resources/placeoperation?view=graph-rest-beta) objects. |
| [Get](https://learn.microsoft.com/en-us/graph/api/place-getoperation?view=graph-rest-beta) | [placeOperation](https://learn.microsoft.com/en-us/graph/api/resources/placeoperation?view=graph-rest-beta) | Get a [placeOperation](https://learn.microsoft.com/en-us/graph/api/resources/placeoperation?view=graph-rest-beta) by ID. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| details | [placeExecutionResult](https://learn.microsoft.com/en-us/graph/api/resources/placeexecutionresult?view=graph-rest-beta) collection | The detailed result of the operation, including errors and successful places. |
| id | String | The ID of the operation. |
| progress | [placeOperationProgress](https://learn.microsoft.com/en-us/graph/api/resources/placeoperationprogress?view=graph-rest-beta) | The progress of the operation. |
| status | placeOperationStatus | The status of the operation. The possible values are: `created`, `inProgress`, `succeeded`, `failed`, `partiallySucceeded`, `expired`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.placeOperation",
  "details": [{"@odata.type": "microsoft.graph.placeExecutionResult"}],
  "id": "String (identifier)",
  "progress": {"@odata.type": "microsoft.graph.placeOperationProgress"},
  "status": "String"
}
```
