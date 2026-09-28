<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# run resource type

Namespace: microsoft.graph.identityGovernance

Represents the result of a [lifecycle workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) that ran for a collection of users because they fulfilled the [conditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutionconditions?view=graph-rest-1.0) of the lifecycle workflow. The result is an aggregation of all [user processing results](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userprocessingresult?view=graph-rest-1.0) of the users that were either processed within an [interval](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclemanagementsettings?view=graph-rest-1.0#properties) or were part of an [on-demand execution](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-activate?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List runs](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-list-runs?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) collection | Get a list of the [run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) objects and their properties. |
| [Get runs](https://learn.microsoft.com/en-us/graph/api/identitygovernance-run-get?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) | Read the properties and relationships of a [run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) object. |
| [Get summary](https://learn.microsoft.com/en-us/graph/api/identitygovernance-run-summary?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.runSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-runsummary?view=graph-rest-1.0) | Get a summary of workflows runs. |
| [List task processing results](https://learn.microsoft.com/en-us/graph/api/identitygovernance-run-list-taskprocessingresults?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.taskReportSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) | List task processing results from a run. |
| [List reprocessedRuns](https://learn.microsoft.com/en-us/graph/api/identitygovernance-run-list-reprocessedruns?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) collection | Get a list of the workflow's reprocessed runs. |
| [Remove reprocessedRuns](https://learn.microsoft.com/en-us/graph/api/identitygovernance-run-delete-reprocessedruns?view=graph-rest-1.0) | None | Delete a reprocessed run object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activatedOnScope | [microsoft.graph.identityGovernance.activationScope](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-activationscope?view=graph-rest-1.0) | The scope for which the workflow runs. |
| completedDateTime | DateTimeOffset | The date time that the run completed. Value is `null` if the workflow hasn't completed.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| failedTasksCount | Int32 | The number of tasks that failed in the run execution. |
| failedUsersCount | Int32 | The number of users that failed in the run execution. |
| id | String | A unique identifier for the workflow run. |
| lastUpdatedDateTime | DateTimeOffset | The datetime that the run was last updated.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| processingStatus | [microsoft.graph.identityGovernance.lifecycleWorkflowProcessingStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance-lifecycleworkflowprocessingstatus?view=graph-rest-1.0) | The run execution status.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |
| scheduledDateTime | DateTimeOffset | The date time that the run is scheduled to be executed for a workflow.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| startedDateTime | DateTimeOffset | The date time that the run execution started.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| successfulUsersCount | Int32 | The number of successfully completed users in the run. |
| totalUsersCount | Int32 | The total number of users in the workflow execution. |
| totalTasksCounts | Int32 | The total number of tasks in the run execution. |
| totalUnprocessedTasksCount | Int32 | The total number of unprocessed tasks in the run execution. |
| workflowExecutionType | microsoft.graph.identityGovernance.workflowExecutionType | The execution type of the workflows associated with the run. The possible values are: `scheduled`, `onDemand`, `unknownFutureValue`, `activatedWithScope`, `preview`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `activatedWithScope`, `preview`.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| reprocessedRuns | [microsoft.graph.identityGovernance.run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) collection | The related reprocessed workflow run. |
| subjectProcessingResults | [microsoft.graph.identityGovernance.subjectProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectprocessingresult?view=graph-rest-1.0) collection | The processing results for each subject in this workflow run. |
| taskProcessingResults | [microsoft.graph.identityGovernance.taskProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) collection | The related taskProcessingResults. |
| taskReports | [microsoft.graph.identityGovernance.taskReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskreport?view=graph-rest-1.0) collection | The related taskProcessingReports. |
| userProcessingResults | [microsoft.graph.identityGovernance.userProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userprocessingresult?view=graph-rest-1.0) collection | The associated individual user execution. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.run",
  "id": "String (identifier)",
  "completedDateTime": "String (timestamp)",
  "failedTasksCount": "Integer",
  "failedUsersCount": "Integer",
  "lastUpdatedDateTime": "String (timestamp)",
  "processingStatus": "String",
  "startedDateTime": "String (timestamp)",
  "scheduledDateTime": "String (timestamp)",
  "successfulUsersCount": "Integer",
  "totalTasksCounts": "Integer",
  "totalUsersCount": "Integer",
  "totalUnprocessedTasksCount": "Integer",
  "workflowExecutionType": "String"
}
```
