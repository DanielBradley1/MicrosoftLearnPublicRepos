<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/richlongrunningoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# richLongRunningOperation resource type

Namespace: microsoft.graph

Represents the status of a long-running operation on a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) or a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/richlongrunningoperation-get?view=graph-rest-1.0) | [richLongRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/richlongrunningoperation?view=graph-rest-1.0) | Get the status of a [rich long-running operation](https://learn.microsoft.com/en-us/graph/api/resources/richlongrunningoperation?view=graph-rest-1.0) on a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) or a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when this operation was created. |
| error | [publicError](https://learn.microsoft.com/en-us/graph/api/resources/publicerror?view=graph-rest-1.0) | Error that caused the operation to fail. |
| id | String | Unique identifier for the operation. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastActionDateTime | DateTimeOffset | The date and time when the last action was performed on this operation. |
| percentageComplete | Int32 | A value between 0 and 100 that indicates the progress of the operation. |
| resourceId | String | The unique identifier for the result. |
| resourceLocation | String | The canonical URL of the resource. |
| status | longRunningOperationStatus | The status of the long-running operation. The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `unknownFutureValue`. |
| statusDetail | String | The detail about the status value. |
| type | String | The type of the operation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.richLongRunningOperation",
  "createdDateTime": "String (timestamp)",
  "error": {
    "@odata.type": "microsoft.graph.publicError"
  },
  "id": "String (identifier)",
  "lastActionDateTime": "String (timestamp)",
  "percentageComplete": "Integer",
  "resourceId": "String",
  "resourceLocation": "String",
  "status": "String",
  "statusDetail": "String",
  "type": "String"
}
```
