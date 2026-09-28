<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationtaskexecution?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# synchronizationTaskExecution resource type

Namespace: microsoft.graph

Summarizes the results of the synchronization job run. This object is configured in the **lastExecution**, **lastSuccessfulExecution**, and **lastSuccessfulExecutionWithExports** properties of [synchronizationStatus](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationstatus?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activityIdentifier | String | Identifier of the job run. |
| countEntitled | Int64 | Count of processed entries that were assigned for this application. |
| countEntitledForProvisioning | Int64 | Count of processed entries that were assigned for provisioning. |
| countEscrowed | Int64 | Count of entries that were escrowed \(errors\). |
| countEscrowedRaw | Int64 | Count of entries that were escrowed, including system-generated escrows. |
| countExported | Int64 | Count of exported entries. |
| countExports | Int64 | Count of entries that were expected to be exported. |
| countImported | Int64 | Count of imported entries. |
| countImportedDeltas | Int64 | Count of imported delta-changes. |
| countImportedReferenceDeltas | Int64 | Count of imported delta-changes pertaining to reference changes. |
| error | [synchronizationError](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationerror?view=graph-rest-1.0) | If an error was encountered, contains a **synchronizationError** object with details. |
| state | synchronizationTaskExecutionResult | Code summarizing the result of this run. The possible values are: `Succeeded`, `Failed`, `EntryLevelErrors`. |
| timeBegan | DateTimeOffset | Time when this job run began. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| timeEnded | DateTimeOffset | Time when this job run ended. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "activityIdentifier": "String",
  "countEntitled": 1024,
  "countEntitledForProvisioning": 1024,
  "countEscrowed": 1024,
  "countEscrowedRaw": 1024,
  "countExported": 1024,
  "countExports": 1024,
  "countImported": 1024,
  "countImportedDeltas": 1024,
  "countImportedReferenceDeltas": 1024,
  "error": {
    "@odata.type": "microsoft.graph.synchronizationError"
  },
  "state": "String",
  "timeBegan": "String (timestamp)",
  "timeEnded": "String (timestamp)"
}
```
