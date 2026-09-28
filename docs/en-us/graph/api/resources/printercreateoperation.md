<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printercreateoperation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# printerCreateOperation resource type

Namespace: microsoft.graph

Represents a long-running printer registration operation. Derived from [printOperation](https://learn.microsoft.com/en-us/graph/api/resources/printoperation?view=graph-rest-1.0).

Inherits from [printOperation](https://learn.microsoft.com/en-us/graph/api/resources/printoperation?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/printoperation-get?view=graph-rest-1.0) | [printOperation](https://learn.microsoft.com/en-us/graph/api/resources/printoperation?view=graph-rest-1.0) | Retrieve a long-running operation within current user or app's tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| certificate | String | The signed certificate created during the registration process. Read-only. |
| createdDateTime | DateTimeOffset | The DateTimeOffset when the operation was created. Read-only. |
| id | String | The operation's identifier. Read-only. |
| status | [printOperationStatus](https://learn.microsoft.com/en-us/graph/api/resources/printoperationstatus?view=graph-rest-1.0) | The status of the registration operation. Contains the operation's progress and whether it completed successfully. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| printer | [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) | The created printer entity. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printerCreateOperation",
  "id": "String (identifier)",
  "status": {
    "@odata.type": "microsoft.graph.printOperationStatus"
  },
  "createdDateTime": "String (timestamp)",
  "certificate": "String"
}
```
