<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# task resource type \(lifecycle workflow tasks\)

Namespace: microsoft.graph.identityGovernance

Represents the built-in tasks available for lifecycle workflows. Tasks are the actions a workflow executes when triggered. The built-in task "Run a custom task extension" can be used to trigger [custom task extensions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) when you reach the limits of the other available built-in tasks. The task allows integration with Azure Logic Apps.

A workflow can have up to 25 tasks.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List tasks](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-list-task?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) collection | Get a list of the [task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) objects and their properties. |
| [Get task](https://learn.microsoft.com/en-us/graph/api/identitygovernance-task-get?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) | Read the properties and relationships of a [task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) object. |
| [Update task](https://learn.microsoft.com/en-us/graph/api/identitygovernance-task-update?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) | update the properties of a [task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| arguments | [microsoft.graph.keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-1.0) collection | Arguments included within the task.  <br>For guidance to configure this property, see [Configure the arguments for built-in Lifecycle Workflow tasks](https://learn.microsoft.com/en-us/graph/identitygovernance-lifecycleworkflows-task-arguments). Required. |
| category | microsoft.graph.identityGovernance.lifecycleTaskCategory | The category of the task. The possible values are: `joiner`, `leaver`, `unknownFutureValue`, `mover`, `extensibility`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `mover`, `extensibility`. This property is multi-valued and the same task can apply to both `joiner` and `leaver` categories.  <br>  <br>Supports `$filter`\(`eq`, `ne`\). |
| continueOnError | Boolean | A Boolean value that specifies whether, if this task fails, the workflow stops, and subsequent tasks aren't run. Optional. |
| description | String | A string that describes the purpose of the task for administrative use. Optional. |
| displayName | String | A unique string that identifies the task. Required.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `orderBy`. |
| executionSequence | Int32 | An integer that states in what order the task runs in a workflow.  <br>  <br>Supports `$orderby`. |
| id | String | Identifier used for individually addressing a specific task. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |
| isEnabled | Boolean | A Boolean value that denotes whether the task is set to run or not. Optional.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `orderBy`. |
| taskDefinitionId | String | A unique template identifier for the task. For more information about the tasks that Lifecycle Workflows currently supports and their unique identifiers, see [Configure the arguments for built-in Lifecycle Workflow tasks](https://learn.microsoft.com/en-us/graph/identitygovernance-lifecycleworkflows-task-arguments). Required.  <br>  <br>Supports `$filter`\(`eq`, `ne`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| taskProcessingResults | [microsoft.graph.identityGovernance.taskProcessingResult](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskprocessingresult?view=graph-rest-1.0) collection | The result of processing the task. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.task",
  "id": "String (identifier)",
  "arguments": [
    {
      "@odata.type": "microsoft.graph.keyValuePair"
    }
  ],
  "category": "String",
  "continueOnError": "Boolean",
  "description": "String",
  "displayName": "String",
  "executionSequence": "Integer",
  "isEnabled": "Boolean",
  "taskDefinitionId": "String"
}
```

## Related content

- [Configure task arguments](https://learn.microsoft.com/en-us/graph/identitygovernance-lifecycleworkflows-task-arguments)
