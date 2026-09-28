<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userprocessingresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-30 -->

# userProcessingResult resource type

Namespace: microsoft.graph.identityGovernance

Result of a [lifecycle workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) that was executed for a specific user because the user fulfilled the [execution conditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutionconditions?view=graph-rest-1.0) of the lifecycle workflow. The result is an aggregation of all [task processing results](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) of the [workflow tasks](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) that were part of the lifecycle workflow and executed for the specific user.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List user processing results](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-list-userprocessingresults?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.userProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userprocessingresult?view=graph-rest-1.0) collection | Get a list of the [userProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userprocessingresult?view=graph-rest-1.0) objects and their properties. |
| [Get user processing result](https://learn.microsoft.com/en-us/graph/api/identitygovernance-userprocessingresult-get?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.userProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userprocessingresult?view=graph-rest-1.0) | Get a user processing result. |
| [Get summary](https://learn.microsoft.com/en-us/graph/api/identitygovernance-userprocessingresult-summary?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.userSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-usersummary?view=graph-rest-1.0) | Provides a summary of user processing results for a specified time period. |
| [List task processing results](https://learn.microsoft.com/en-us/graph/api/identitygovernance-userprocessingresult-list-taskprocessingresults?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.taskReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) collection | Get a list of the [taskProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) objects and their properties. |
| [List reprocessedRuns](https://learn.microsoft.com/en-us/graph/api/identitygovernance-userprocessingresult-list-reprocessedruns?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) collection | Get a list of the workflow's reprocessed runs. |
| [Remove reprocessedRuns](https://learn.microsoft.com/en-us/graph/api/identitygovernance-userprocessingresult-delete-reprocessedruns?view=graph-rest-1.0) | None | Delete a reprocessed run object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completedDateTime | DateTimeOffset | The date time that the workflow execution for a user completed. Value is null if the workflow hasn't completed.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| failedTasksCount | Int32 | The number of tasks that failed in the workflow execution. |
| id | String | Identifier used for individually addressing a specific user processing result. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |
| processingStatus | [microsoft.graph.identityGovernance.lifecycleWorkflowProcessingStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance-lifecycleworkflowprocessingstatus?view=graph-rest-1.0) | The workflow execution status.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |
| scheduledDateTime | DateTimeOffset | The date time that the workflow is scheduled to be executed for a user.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| startedDateTime | DateTimeOffset | The date time that the workflow execution started. Value is `null` if the workflow execution hasn't started.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| totalTasksCount | Int32 | The total number of tasks that in the workflow execution. |
| totalUnprocessedTasksCount | Int32 | The total number of unprocessed tasks for the workflow. |
| workflowExecutionType | microsoft.graph.identityGovernance.workflowExecutionType | Describes the execution type of the workflow. The possible values are: `scheduled`, `onDemand`, `unknownFutureValue`, `activatedWithScope`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `activatedWithScope`.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| workflowVersion | Int32 | The version of the workflow that was executed. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| reprocessedRuns | [microsoft.graph.identityGovernance.run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) collection | The related reprocessed workflow run. |
| subject | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | The unique identifier of the user targeted for the `taskProcessingResult`.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$expand`. |
| taskProcessingResults | [microsoft.graph.identityGovernance.taskProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) collection | The associated individual task execution. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.userProcessingResult",
  "id": "String (identifier)",
  "completedDateTime": "String (timestamp)",
  "failedTasksCount": "Integer",
  "processingStatus": "String",
  "scheduledDateTime": "String (timestamp)",
  "startedDateTime": "String (timestamp)",
  "totalTasksCount": "Integer",
  "totalUnprocessedTasksCount": "Integer",
  "workflowExecutionType": "String",
  "workflowVersion": "Integer"
}
```
