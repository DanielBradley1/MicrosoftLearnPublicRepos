<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# workflow resource type

Namespace: microsoft.graph.identityGovernance

Represents workflows created using Lifecycle Workflows. Workflows, when triggered by execution conditions, automate parts of the lifecycle management process using tasks. These tasks can either be built-in tasks, or a custom task can be called using the custom task extension which integrate with Azure Logic Apps.

You can create up to 100 workflows in a tenant.

Inherits from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-list-workflows?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) collection | Get a list of the [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-post-workflows?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) | Create a new [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-get?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) | Read the properties and relationships of a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-update?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) | Update the properties of a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-delete?view=graph-rest-1.0) | None | Deletes a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object. |
| [Activate](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-activate?view=graph-rest-1.0) | None | Run a workflow on-demand. |
| [Activate with scope](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-activatewithscope?view=graph-rest-1.0) | None | Run a workflow on-demand with a specific scope. |
| [Activate and wait](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-activateandwait?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.awaitedWorkflowProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-awaitedworkflowprocessingresult?view=graph-rest-1.0) | Activate a workflow for a subject and synchronously wait for completion. |
| [List users in scope](https://learn.microsoft.com/en-us/graph/api/workflow-list-executionscope?view=graph-rest-1.0) | [microsoft.graph.user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) collection | Get a list of users who are in the scope of the execution conditions of a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object. |
| [Clear quarantine](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-clearquarantine?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) | Release a quarantined workflow so that it resumes processing. |
| [Preview task failures](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-previewtaskfailures?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.previewFailedTask](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-previewfailedtask?view=graph-rest-1.0) collection | Validate the tasks configured in a workflow to check for configuration errors. |
| [Preview workflow](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-previewworkflow?view=graph-rest-1.0) | None | Run a workflow in preview mode for selected directory objects without affecting production users. |
| **Deleted workflows** | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-list-deleteditems?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) collection | Get a list of deleted [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/identitygovernance-deleteditemcontainer-get?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) | Get a deleted [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0). |
| [Restore](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-restore?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) | Restore a deleted workflow. |
| [Permanently delete](https://learn.microsoft.com/en-us/graph/api/identitygovernance-deleteditemcontainer-delete?view=graph-rest-1.0) | None | Permanently delete a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object from the deleted items container. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | microsoft.graph.identityGovernance.lifecycleWorkflowCategory | The category of the HR function supported by the workflows created using this template. A workflow can only belong to one category. The possible values are: `joiner`, `leaver`, `unknownFutureValue`, `mover`, `extensibility`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `mover`, `extensibility`. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0). Required.  <br>  <br>Supports `$filter`\(`eq`,`ne`\) and `$orderby` |
| createdDateTime | DateTimeOffset | When the `workflow` was created. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| deletedDateTime | DateTimeOffset | When the workflow was deleted.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| description | String | The description of the `workflow`. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0). Optional. |
| displayName | String | The display name of the `workflow`. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0). Required.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `orderby`. |
| executionConditions | [microsoft.graph.identityGovernance.workflowExecutionConditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutionconditions?view=graph-rest-1.0) | Conditions describing when to execute the workflow and the criteria to identify in-scope subject set. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0). Required. |
| id | String | Identifier used for individually addressing a specific workflow.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |
| isEnabled | Boolean | Whether the workflow is enabled or disabled. If this setting is `true`, the workflow can be run on demand or on schedule when **isSchedulingEnabled** is `true`. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0). Optional. Defaults to `true`.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `orderBy`. |
| isSchedulingEnabled | Boolean | If `true`, the Lifecycle Workflow engine executes the workflow based on the schedule defined by [tenant settings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclemanagementsettings?view=graph-rest-1.0). Cannot be `true` for a disabled workflow \(where **isEnabled** is `false`\). Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0). Optional. Defaults to `false`.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `orderBy`. |
| lastModifiedDateTime | DateTimeOffset | The date time when the `workflow` was last modified. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| nextScheduleRunDateTime | DateTimeOffset | The date time when the `workflow` is expected to run next based on the schedule interval, if there are any users matching the execution conditions.  <br>  <br>Supports `$filter`\(`lt`,`gt`\) and `$orderby`. |
| quarantineDetails | [microsoft.graph.identityGovernance.quarantineDetails](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-quarantinedetails?view=graph-rest-1.0) | The current quarantine state of the workflow. Read-only. |
| settings | [microsoft.graph.identityGovernance.workflowSetting](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsetting?view=graph-rest-1.0) | The settings of the workflow, including its quarantine configuration. |
| version | Int32 | The current version number of the workflow. Value is 1 when the workflow is first created.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| administrationScopeTargets | [microsoft.graph.directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The [administrative units](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) in the scope of the workflow. Optional. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).  <br>  <br>Supports `$expand`. |
| createdBy | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | The unique identifier of the Microsoft Entra user that created the [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$expand`. |
| executionScope | [microsoft.graph.user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) collection | The list of users that meet the [workflowExecutionConditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutionconditions?view=graph-rest-1.0) of a workflow. |
| lastModifiedBy | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | The user who last modified the [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$expand`. |
| previewScope | [microsoft.graph.directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The preview scope for the workflow. |
| runs | [microsoft.graph.identityGovernance.run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) collection | Workflow runs. |
| subjectProcessingResults | [microsoft.graph.identityGovernance.subjectProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-subjectprocessingresult?view=graph-rest-1.0) collection | Per-subject workflow execution results. |
| taskReports | [microsoft.graph.identityGovernance.taskReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskreport?view=graph-rest-1.0) collection | Represents the aggregation of task execution data for tasks within a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object. |
| tasks | [microsoft.graph.identityGovernance.task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) collection | Represents the configured tasks to execute and their execution sequence within a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) object. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0). Required. |
| userProcessingResults | [microsoft.graph.identityGovernance.userProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userprocessingresult?view=graph-rest-1.0) collection | Per-user workflow execution results. |
| versions | [microsoft.graph.identityGovernance.workflowVersion](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowversion?view=graph-rest-1.0) collection | The workflow versions that are available. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.workflow",
  "category": "String",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "executionConditions": {
    "@odata.type": "microsoft.graph.identityGovernance.workflowExecutionConditions"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "deletedDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "isEnabled": "Boolean",
  "isSchedulingEnabled": "Boolean",
  "nextScheduleRunDateTime": "String (timestamp)",
  "version": "Integer",
  "quarantineDetails": {
    "@odata.type": "microsoft.graph.identityGovernance.quarantineDetails"
  },
  "settings": {
    "@odata.type": "microsoft.graph.identityGovernance.workflowSetting"
  }
}
```
