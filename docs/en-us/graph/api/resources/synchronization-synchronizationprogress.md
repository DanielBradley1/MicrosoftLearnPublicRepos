<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationprogress?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# synchronizationProgress resource type

Namespace: microsoft.graph

Represents the **progress** of a [synchronizationJob](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0) toward completion.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completedUnits | Int32 | The numerator of a progress ratio; the number of units of changes already processed. |
| progressObservationDateTime | DateTimeOffset | The time of a progress observation as an offset in minutes from UTC. |
| totalUnits | Int32 | The denominator of a progress ratio; a number of units of changes to be processed to accomplish synchronization. |
| units | String | An optional description of the units. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.synchronizationProgress",
  "completedUnits": "Integer",
  "progressObservationDateTime": "String (timestamp)",
  "totalUnits": "Integer",
  "units": "String"
}
```
