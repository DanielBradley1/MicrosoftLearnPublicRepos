<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# workbookOperation resource type

Represents the status of a long-running workbook operation.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/workbookoperation-get?view=graph-rest-1.0) | [workbookOperation](https://learn.microsoft.com/en-us/graph/api/resources/workbookoperation?view=graph-rest-1.0) | Get a workbookOperation object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| error | [workbookOperationError](https://learn.microsoft.com/en-us/graph/api/resources/workbookoperationerror?view=graph-rest-1.0) | The error returned by the operation. |
| id | String | The identifier for the operation. Read-only. |
| resourceLocation | String | The resource URI for the result. |
| status | String | The current status of the operation. The possible values are: `NotStarted`, `Running`, `Completed`, `Failed`. |
| statusCode | integer | Status code of the operation. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.workbookOperation",
  "error": {
    "@odata.type": "microsoft.graph.workbookOperationError"
  },
  "id": "String (identifier)",
  "resourceLocation": "String",
  "status": "String",
  "statusCode": "Integer"
}
```
