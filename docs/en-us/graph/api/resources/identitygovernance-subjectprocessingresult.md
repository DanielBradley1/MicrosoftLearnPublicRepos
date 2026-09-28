<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectprocessingresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# subjectProcessingResult resource type

Namespace: microsoft.graph.identityGovernance

Represents the processing results for a single subject \(for example, a provisioning object\) in a lifecycle workflow run. This resource mirrors [userProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userprocessingresult?view=graph-rest-1.0) but uses a [workflowSubject](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsubject?view=graph-rest-1.0)-typed **subject** property to support non-user subjects.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List \(from run\)](https://learn.microsoft.com/en-us/graph/api/identitygovernance-run-list-subjectprocessingresults?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.subjectProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectprocessingresult?view=graph-rest-1.0) collection | Get a list of the subjectProcessingResult objects and their properties from a run. |
| [Get](https://learn.microsoft.com/en-us/graph/api/identitygovernance-subjectprocessingresult-get?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.subjectProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectprocessingresult?view=graph-rest-1.0) | Read the properties and relationships of a subjectProcessingResult object. |
| [Summary](https://learn.microsoft.com/en-us/graph/api/identitygovernance-subjectprocessingresult-summary?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.subjectSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectsummary?view=graph-rest-1.0) | Get a [subjectSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectsummary?view=graph-rest-1.0) of subjectProcessingResult objects over a specified time period. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completedDateTime | DateTimeOffset | The date and time when the subject processing completed. Read-only. |
| failedTasksCount | Int32 | The count of tasks that failed for the subject. Read-only. |
| id | String | The unique identifier for the subject processing result. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Read-only. |
| processingStatus | [microsoft.graph.identityGovernance.lifecycleWorkflowProcessingStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance-lifecycleworkflowprocessingstatus?view=graph-rest-1.0) | The overall processing status for the subject. Read-only. Supports `$filter` \(`eq`, `ne`\). |
| scheduledDateTime | DateTimeOffset | The date and time when processing was scheduled. Read-only. |
| startedDateTime | DateTimeOffset | The date and time when processing started. Read-only. |
| subject | [microsoft.graph.identityGovernance.workflowSubject](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsubject?view=graph-rest-1.0) | The subject for which tasks were processed. Read-only. |
| subjectType | microsoft.graph.identityGovernance.subjectType | The type of subject for which tasks were processed. This flagged enumeration allows multiple members to be selected simultaneously. The possible values are: `user`, `unknownFutureValue`, `provisioningObject`. Use the `Prefer: include-unknown-enum-members` request header to get the following value from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `provisioningObject`. Read-only. Supports `$filter` \(`eq`, `ne`\). |
| totalTasksCount | Int32 | The total number of tasks in the workflow. Read-only. |
| totalUnprocessedTasksCount | Int32 | The count of tasks that have not yet been processed. Read-only. |
| workflowExecutionType | microsoft.graph.identityGovernance.workflowExecutionType | The workflow execution type. The possible values are: `scheduled`, `onDemand`, `unknownFutureValue`, `activatedWithScope`, `preview`, `extensibilityOnDemand`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `activatedWithScope`, `preview`, `extensibilityOnDemand`. Read-only. Supports `$filter` \(`eq`, `ne`\). |
| workflowVersion | Int32 | The version of the workflow at the time of execution. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| reprocessedRuns | [microsoft.graph.identityGovernance.run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) collection | The reprocessed runs associated with this subject processing result. |
| taskProcessingResults | [microsoft.graph.identityGovernance.taskProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) collection | The task-level processing results for this subject. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.subjectProcessingResult",
  "id": "String (identifier)",
  "completedDateTime": "String (timestamp)",
  "failedTasksCount": "Integer",
  "processingStatus": "String",
  "scheduledDateTime": "String (timestamp)",
  "startedDateTime": "String (timestamp)",
  "totalTasksCount": "Integer",
  "totalUnprocessedTasksCount": "Integer",
  "workflowExecutionType": "String",
  "workflowVersion": "Integer",
  "subjectType": "String",
  "subject": {
    "@odata.type": "microsoft.graph.identityGovernance.workflowSubject"
  }
}
```
