<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# taskProcessingResult resource type

Namespace: microsoft.graph.identityGovernance

Result of a [workflow task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) that was executed for a specific user because the workflow task was part of the [lifecycle workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) for which the user fulfilled the [execution conditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutionconditions?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Resume](https://learn.microsoft.com/en-us/graph/api/identitygovernance-taskprocessingresult-resume?view=graph-rest-1.0) | None | Resumes the **taskProcessingResult** as part of the Azure Logic App integration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completedDateTime | DateTimeOffset | The date time when taskProcessingResult execution ended. Value is `null` if task execution is still in progress.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| createdDateTime | DateTimeOffset | The date time when the taskProcessingResult was created.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| failureReason | String | Describes why the taskProcessingResult failed. |
| id | String | Identifier used for individually addressing a specific task processing result. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |
| processingInfo | String | Additional human-readable context about the task processing outcome. This property contains information about edge cases where the task completed successfully but the expected action wasn't performed because the target was already in the desired state, such as when the user was already a member of the specified group. Returns `null` when no additional context is needed. Nullable. |
| processingStatus | [microsoft.graph.identityGovernance.lifecycleWorkflowProcessingStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance-lifecycleworkflowprocessingstatus?view=graph-rest-1.0) | Describes the execution status of the `taskProcessingResult`.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |
| startedDateTime | DateTimeOffset | The date time when taskProcessingResult execution started. Value is `null` if task execution hasn't started yet.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| workflowSubject | [microsoft.graph.identityGovernance.workflowSubject](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsubject?view=graph-rest-1.0) | The workflow subject associated with this task processing result. Populated for extensibility and provisioning workflows. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| subject | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | The unique identifier of the Microsoft Entra user targeted for the task execution.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$expand`. |
| task | [microsoft.graph.identityGovernance.task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) | The related workflow task |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.taskProcessingResult",
  "id": "String (identifier)",
  "completedDateTime": "String (timestamp)",
  "createdDateTime": "String (timestamp)",
  "failureReason": "String",
  "processingInfo": "String",
  "processingStatus": "String",
  "startedDateTime": "String (timestamp)",
  "workflowSubject": {
    "@odata.type": "microsoft.graph.identityGovernance.workflowSubject"
  }
}
```
