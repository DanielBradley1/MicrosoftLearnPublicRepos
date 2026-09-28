<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printtaskstatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# printTaskStatus resource type

Namespace: microsoft.graph

Represents the current execution status of a [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A human-readable description of the current processing state of the [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0). |
| state | printTaskProcessingState | The current processing state of the [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0). Valid values are described in the following table. |

### printTaskProcessingState values

| Member | Value | Description |
| :--- | :--- | :--- |
| pending | 0 | Task execution is pending. |
| processing | 1 | Task execution is in progress. |
| completed | 2 | Task execution has completed. |
| aborted | 3 | Task execution was aborted. |
| unknownFutureValue | 4 | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printTaskStatus",
  "state": "String",
  "description": "String"
}
```
