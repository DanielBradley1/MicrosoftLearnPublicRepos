<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# printTask resource type

Namespace: microsoft.graph

Represents a task that is executing or has been executed as a result of a Universal Print event.

For details about how to use this resource to add pull printing support to Universal Print, see [Extending Universal Print to support pull printing](https://learn.microsoft.com/en-us/graph/universal-print-concept-overview#extending-universal-print-to-support-pull-printing).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List tasks](https://learn.microsoft.com/en-us/graph/api/printtaskdefinition-list-tasks?view=graph-rest-1.0) | [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) | Get a list of tasks that have been created based on a particular printTaskDefinition. The list includes currently running tasks and recently completed tasks. |
| [Get task](https://learn.microsoft.com/en-us/graph/api/printtask-get?view=graph-rest-1.0) | [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) | Get details about a print task. |
| [Update task](https://learn.microsoft.com/en-us/graph/api/printtaskdefinition-update-task?view=graph-rest-1.0) | [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) | Updates a print task. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The printTask's identifier. Read-only. |
| status | [printTaskStatus](https://learn.microsoft.com/en-us/graph/api/resources/printtaskstatus?view=graph-rest-1.0) | The current execution status of this printTask. **The calling application is responsible for updating this status when processing is finished, unless the related printJob has been redirected to another printer.** Failure to report completion will result in the related print job being blocked from printing and eventually deleted. |
| parentUrl | String | The URL for the print entity that triggered this task. For example, `https://graph.microsoft.com/v1.0/print/printers/{printerId}/jobs/{jobId}`. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definition | [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) | The printTaskDefinition that was used to create this task. Read-only. |
| trigger | [printTaskTrigger](https://learn.microsoft.com/en-us/graph/api/resources/printtasktrigger?view=graph-rest-1.0) | The printTaskTrigger that triggered this task's execution. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printTask",
  "id": "String (identifier)",
  "status": {
    "@odata.type": "microsoft.graph.printTaskStatus"
  },
  "parentUrl": "String"
}
```
