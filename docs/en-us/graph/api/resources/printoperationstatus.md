<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printoperationstatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-05 -->

# printOperationStatus resource type

Namespace: microsoft.graph

Represents the current status of a long-running Universal Print operation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A human-readable description of the printOperation's current processing state. Read-only. |
| state | printOperationProcessingState | The printOperation's current processing state. Valid values are described in the following table. Read-only. |

### printOperationProcessingState values

| Member | Value | Description |
| :--- | :--- | :--- |
| notStarted | 0 | The operation has not yet started. |
| running | 1 | The operation is running. |
| succeeded | 2 | The operation completed successfully. |
| failed | 3 | The operation failed. |
| unknownFutureValue | 4 | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printOperationStatus",
  "state": "String",
  "description": "String"
}
```
