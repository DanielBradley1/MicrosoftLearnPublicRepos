<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/addlargegalleryviewoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# addLargeGalleryViewOperation resource type

Namespace: microsoft.graph

Describes the response format for an operation that adds the large gallery view.

Inherits from [commsOperation](https://learn.microsoft.com/en-us/graph/api/resources/commsoperation?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get large gallery view operation status](https://learn.microsoft.com/en-us/graph/api/addlargegalleryviewoperation-get?view=graph-rest-1.0) | [addLargeGalleryViewOperation](https://learn.microsoft.com/en-us/graph/api/resources/addlargegalleryviewoperation?view=graph-rest-1.0) | Get the status of an operation that adds the large gallery view to a call. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientContext | String | The client context. |
| id | String | The ID of the server operation. Read-only. |
| resultInfo | [resultInfo](https://learn.microsoft.com/en-us/graph/api/resources/resultinfo?view=graph-rest-1.0) | The result information. Read-only. |
| status | operationStatus | The status of the operation. The possible values are: `notStarted`, `running`, `completed`, `failed`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "clientContext": "String",
  "id": "String (identifier)",
  "resultInfo": {"@odata.type": "#microsoft.graph.resultInfo"},
  "status": "String"
}
```
