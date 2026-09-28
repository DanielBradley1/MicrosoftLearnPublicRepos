<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskreport?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# taskReport resource type

Namespace: microsoft.graph.identityGovernance

An aggregation of [task processing results](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) for a specific [workflow task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) within a [workflow run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0). With this report, the health status of a workflow task within a workflow run can be easily determined and thus the source of error can be identified more quickly should a workflow run not have been completed successfully.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List task reports](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-list-taskreports?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.taskReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskreport?view=graph-rest-1.0) collection | Get a list of the [taskReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskreport?view=graph-rest-1.0) objects and their properties. |
| [Get summary](https://learn.microsoft.com/en-us/graph/api/identitygovernance-taskreport-summary?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.taskReportSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskreportsummary?view=graph-rest-1.0) | Read the properties and relationships of a [taskReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskreport?view=graph-rest-1.0) object. |
| [List task processing results](https://learn.microsoft.com/en-us/graph/api/identitygovernance-taskreport-list-taskprocessingresults?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.taskProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) collection | Get the taskProcessingResult resources for a task report. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completedDateTime | DateTimeOffset | The date time that the associated run completed. Value is `null` if the run has not completed.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| failedUsersCount | Int32 | The number of users in the run execution for which the associated task failed.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| id | String | The unique identifier of the task report. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |
| lastUpdatedDateTime | DateTimeOffset | The date and time that the task report was last updated. |
| processingStatus | [microsoft.graph.identityGovernance.lifecycleWorkflowProcessingStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance-lifecycleworkflowprocessingstatus?view=graph-rest-1.0) | The processing status of the associated task based on the taskProcessingResults.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |
| runId | String | The unique identifier of the associated [run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0). |
| startedDateTime | DateTimeOffset | The date time that the associated run started. Value is `null` if the run has not started. |
| successfulUsersCount | Int32 | The number of users in the run execution for which the associated task succeeded.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| totalUsersCount | Int32 | The total number of users in the run execution for which the associated task was scheduled to execute.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| unprocessedUsersCount | Int32 | The number of users in the run execution for which the associated task is `queued`, `in progress`, or `canceled`.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| task | [microsoft.graph.identityGovernance.taskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) | The related lifecycle workflow task.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$expand`. |
| taskDefinition | [microsoft.graph.identityGovernance.task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskdefinition?view=graph-rest-1.0) | The taskDefinition associated with the related lifecycle workflow task.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$expand`. |
| taskProcessingResults | [microsoft.graph.identityGovernance.taskProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) collection | The related lifecycle workflow taskProcessingResults. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.taskReport",
  "id": "String (identifier)",
  "runId": "String",
  "processingStatus": "String",
  "successfulUsersCount": "Integer",
  "failedUsersCount": "Integer",
  "unprocessedUsersCount": "Integer",
  "totalUsersCount": "Integer",
  "startedDateTime": "String (timestamp)",
  "completedDateTime": "String (timestamp)",
  "lastUpdatedDateTime": "String (timestamp)"
}
```
