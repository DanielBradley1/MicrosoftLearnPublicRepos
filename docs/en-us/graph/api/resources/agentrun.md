<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentrun?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# agentRun resource type

Namespace: microsoft.graph

Represents an agent's contribution to an agentic session. Read its status, timing, and failure information to monitor processing. The **agent** property describes the agent; it doesn't expose an independently addressable agent catalog.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List agentRuns](https://learn.microsoft.com/en-us/graph/api/investigationsession-list-agentruns?view=graph-rest-beta) | [agentRun](https://learn.microsoft.com/en-us/graph/api/resources/agentrun?view=graph-rest-beta) collection | Get the session's runs. |
| [Get](https://learn.microsoft.com/en-us/graph/api/agentrun-get?view=graph-rest-beta) | [agentRun](https://learn.microsoft.com/en-us/graph/api/resources/agentrun?view=graph-rest-beta) | Read a run. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| agent | [agentInfo](https://learn.microsoft.com/en-us/graph/api/resources/agentinfo?view=graph-rest-beta) | The embedded description of the agent that performed this run. Read-only. |
| completedDateTime | DateTimeOffset | The UTC date and time when the run completed successfully, in ISO 8601 format. Absent otherwise. Read-only. |
| createdDateTime | DateTimeOffset | The UTC date and time when the resource was created, in ISO 8601 format. Read-only. |
| durationInMilliseconds | Int64 | The elapsed time from creation to successful completion, in milliseconds. Absent otherwise. Read-only. |
| failureInfo | [agentRunFailureInfo](https://learn.microsoft.com/en-us/graph/api/resources/agentrunfailureinfo?view=graph-rest-beta) | The run-level failure details, when available. Read-only. |
| id | String | The unique, read-only identifier of the resource. |
| initiatedBy | [investigationIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/investigationidentityset?view=graph-rest-beta) | The initiating principals recorded by the service, when available. Read-only. This property doesn't select an execution identity. |
| lastModifiedDateTime | DateTimeOffset | The UTC date and time when the resource was last updated, in ISO 8601 format. Read-only. |
| startedDateTime | DateTimeOffset | The UTC start timestamp, in ISO 8601 format. Currently reflects creation time, not a distinct execution-start measurement. Read-only. |
| status | longRunningOperationStatus | The service-computed processing status. The possible values are: `notStarted`, `running`, `succeeded`, `failed`, `unknownFutureValue`. A canceled execution has `failed` status and `canceled` **statusDetail**. A request for input has `running` status and `pendingInput` **statusDetail**. Read-only. |
| statusDetail | String | Additional processing detail, including `pendingInput` or `canceled`, when the status alone doesn't describe the source lifecycle. Read-only. Doesn't support `$filter`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentRun",
  "id": "String (identifier)",
  "agent": {
    "@odata.type": "microsoft.graph.agentInfo"
  },
  "status": "String",
  "statusDetail": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "startedDateTime": "String (timestamp)",
  "completedDateTime": "String (timestamp)",
  "durationInMilliseconds": "Integer",
  "failureInfo": {
    "@odata.type": "microsoft.graph.agentRunFailureInfo"
  },
  "initiatedBy": {
    "@odata.type": "microsoft.graph.investigationIdentitySet"
  }
}
```
