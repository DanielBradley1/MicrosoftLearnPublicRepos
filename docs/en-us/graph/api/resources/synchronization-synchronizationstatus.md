<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationstatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# synchronizationStatus resource type

Namespace: microsoft.graph

Represents the current status \(**status** property\) of the [synchronizationJob](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationjob?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | synchronizationStatusCode | High-level status code of the synchronization job. The possible values are: `NotConfigured`, `NotRun`, `Active`, `Paused`, `Quarantine`. |
| countSuccessiveCompleteFailures | Int64 | Number of consecutive times this job failed. |
| escrowsPruned | Boolean | `true` if the job's escrows \(object-level errors\) were pruned during initial synchronization. Escrows can be pruned if during the initial synchronization, you reach the threshold of errors that would normally put the job in quarantine. Instead of going into quarantine, the synchronization process clears the job's errors and continues until the initial synchronization is completed. When the initial synchronization is completed, the job will pause and wait for the customer to clean up the errors. |
| lastExecution | [synchronizationTaskExecution](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationtaskexecution?view=graph-rest-1.0) | Details of the last execution of the job. |
| lastSuccessfulExecution | [synchronizationTaskExecution](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationtaskexecution?view=graph-rest-1.0) | Details of the last execution of this job, which didn't have any errors. |
| lastSuccessfulExecutionWithExports | [synchronizationTaskExecution](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationtaskexecution?view=graph-rest-1.0) | Details of the last execution of the job, which exported objects into the target directory. |
| progress | [synchronizationProgress](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationprogress?view=graph-rest-1.0) collection | Details of the progress of a job toward completion. |
| quarantine | [synchronizationQuarantine](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-synchronizationquarantine?view=graph-rest-1.0) | If job is in quarantine, quarantine details. |
| steadyStateFirstAchievedTime | DateTimeOffset | The time when steady state \(no more changes to the process\) was first achieved. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| steadyStateLastAchievedTime | DateTimeOffset | The time when steady state \(no more changes to the process\) was last achieved. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| synchronizedEntryCountByType | [stringKeyLongValuePair](https://learn.microsoft.com/en-us/graph/api/resources/synchronization-stringkeylongvaluepair?view=graph-rest-1.0) collection | Count of synchronized objects, listed by object type. |
| troubleshootingUrl | String | In the event of an error, the URL with the troubleshooting steps for the issue. |

### Synchronization status code details

| Value | Description |
| :--- | :--- |
| NotConfigured | Job was not configured and never run. No authorization was provided. |
| NotRun | Job was configured, and possibly started, but hasn't completed its first run. |
| Active | Job is running periodically. |
| Paused | Job was paused \(usually by an administrator\) and currently is not running, but the state of the job is preserved. |
| Quarantine | Job is in quarantine. This might happen when there is a high volume of errors, or critical errors such as revoked/expired credentials. While in quarantine, the synchronization process will attempt to run the job with reduced frequency. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "code": "String",
  "countSuccessiveCompleteFailures": "Integer",
  "escrowsPruned": true,
  "lastExecution": {
    "@odata.type": "microsoft.graph.synchronizationTaskExecution"
  },
  "lastSuccessfulExecution": {
    "@odata.type": "microsoft.graph.synchronizationTaskExecution"
  },
  "lastSuccessfulExecutionWithExports": {
    "@odata.type": "microsoft.graph.synchronizationTaskExecution"
  },
  "progress": [
    {
      "@odata.type": "microsoft.graph.synchronizationProgress"
    }
  ],
  "quarantine": {
    "@odata.type": "microsoft.graph.synchronizationQuarantine"
  },
  "steadyStateFirstAchievedTime": "String (timestamp)",
  "steadyStateLastAchievedTime": "String (timestamp)",
  "synchronizedEntryCountByType": [
    {
      "@odata.type": "microsoft.graph.stringKeyLongValuePair"
    }
  ],
  "troubleshootingUrl": "String"
}
```
