<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationquarantine?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# synchronizationQuarantine resource type

Namespace: microsoft.graph

Provides information about the quarantine state of a [synchronizationJob](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0). This object is configured in the **quarantine** property of [synchronizationStatus](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationstatus?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| currentBegan | DateTimeOffset | Date and time when the quarantine was last evaluated and imposed. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| nextAttempt | DateTimeOffset | Date and time when the next attempt to re-evaluate the quarantine will be made. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| reason | quarantineReason | A code that signifies why the quarantine was imposed. The possible values are: `EncounteredBaseEscrowThreshold`, `EncounteredTotalEscrowThreshold`, `EncounteredEscrowProportionThreshold`, `EncounteredQuarantineException`, `Unknown`, `QuarantinedOnDemand`, `TooManyDeletes`, `IngestionInterrupted`. |
| seriesBegan | DateTimeOffset | Date and time when the quarantine was first imposed in this series \(a series starts when a quarantine is first imposed, and is reset as soon as the quarantine is lifted\). The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| seriesCount | Int64 | Number of times in this series the quarantine was re-evaluated and left in effect \(a series starts when quarantine is first imposed, and is reset as soon as quarantine is lifted\). |
| error | [synchronizationError](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationerror?view=graph-rest-1.0) | Describes the error\(s\) that occurred when putting the synchronization job into quarantine. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "error": {
    "@odata.type": "microsoft.graph.synchronizationError"
  },
  "currentBegan": "String (timestamp)",
  "nextAttempt": "String (timestamp)",
  "reason": "String",
  "seriesBegan": "String (timestamp)",
  "seriesCount": "Integer"
}
```
