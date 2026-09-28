<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# printOperation resource type

Namespace: microsoft.graph

Represents a long-running Universal Print operation. Base class for operation types such as [printerCreateOperation](https://learn.microsoft.com/en-us/graph/api/resources/printercreateoperation?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/printoperation-get?view=graph-rest-1.0) | [printOperation](https://learn.microsoft.com/en-us/graph/api/resources/printoperation?view=graph-rest-1.0) | Retrieve a long-running operation within current user or app's tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The DateTimeOffset when the operation was created. Read-only. |
| id | String | The operation's identifier. Read-only. |
| status | [printOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/printoperationstatus?view=graph-rest-1.0) | The status of the operation. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printOperation",
  "id": "String (identifier)",
  "status": {
    "@odata.type": "microsoft.graph.printOperationStatus"
  },
  "createdDateTime": "String (timestamp)"
}
```
