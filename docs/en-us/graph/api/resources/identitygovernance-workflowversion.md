<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowversion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# workflowVersion resource type

Namespace: microsoft.graph.identityGovernance

Represents a version of a [lifecycle workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowversion?view=graph-rest-1.0). Workflow versions are subsequent versions of workflows you can create when you need to change the workflow configuration other than its basic properties. You can view older versions of the workflow and associated reports will note which workflow version had been run.

Inherits from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-createnewversion?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflowVersion](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowversion?view=graph-rest-1.0) | Create a new workflowVersion object. |
| [List](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-list-versions?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflowVersion](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowversion?view=graph-rest-1.0) collection | Get a list of the [workflowVersion](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowversion?view=graph-rest-1.0) objects and their properties. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflowversion-get?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflowVersion](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowversion?view=graph-rest-1.0) | Read the properties and relationships of a [workflowVersion](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowversion?view=graph-rest-1.0) object. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0). |
| [List tasks for a workflow version](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflowversion-list-tasks?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowversion?view=graph-rest-1.0) collection | Get the task resources from the tasks navigation property. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0). |
| [Get task](https://learn.microsoft.com/en-us/graph/api/identitygovernance-task-get?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) | Read the properties and relationships of a [task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | microsoft.graph.identityGovernance.lifecycleWorkflowCategory | The category of the HR function supported by the workflows created using this template. A workflow can only belong to one category. The possible values are: `joiner`, `leaver`, `unknownFutureValue`, `mover`, `extensibility`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `mover`, `extensibility`. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`eq`,`ne`\) and `$orderby` |
| createdDateTime | DateTimeOffset | The date time when the `workflow` was versioned. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| description | String | The description of the `workflowversion`. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0). |
| displayName | String | The display name of the `workflowversion`. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `orderby`. |
| executionConditions | [microsoft.graph.identityGovernance.workflowExecutionConditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutionconditions?view=graph-rest-1.0) | Conditions describing when to execute the workflow and the criteria to identify in-scope subject set. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0). |
| isEnabled | Boolean | Whether the workflow is enabled or disabled. If this setting is `true`, the workflow can be run on demand or on schedule when **isSchedulingEnabled** is `true`. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `orderBy`. |
| isSchedulingEnabled | Boolean | If `true`, the Lifecycle Workflow engine executes the workflow based on the schedule defined by tenant settings. Cannot be `true` for a disabled workflow \(where **isEnabled** is `false`\). Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `orderBy`. |
| lastModifiedDateTime | DateTimeOffset | The date time when the `workflow` was last modified. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |
| settings | [microsoft.graph.identityGovernance.workflowSetting](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsetting?view=graph-rest-1.0) | The settings of the workflow version, including its quarantine configuration. |
| versionNumber | Int32 | The version of the workflow.  <br>  <br>Supports `$filter`\(`lt`, `le`, `gt`, `ge`, `eq`, `ne`\) and `$orderby`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| administrationScopeTargets | [microsoft.graph.directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The [administrative units](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) in the scope of the workflow. Optional. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).  <br>  <br>Supports `$expand`. |
| createdBy | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | The user who created the workflow. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$expand`. |
| lastModifiedBy | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | The user who last modified the workflow.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$expand`. |
| tasks | [microsoft.graph.identityGovernance.task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) collection | The tasks in the workflow. Inherited from [workflowBase](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.workflowVersion",
  "category": "String",
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "executionConditions": {
    "@odata.type": "microsoft.graph.identityGovernance.workflowExecutionConditions"
  },
  "isEnabled": "Boolean",
  "isSchedulingEnabled": "Boolean",
  "lastModifiedDateTime": "String (timestamp)",
  "versionNumber": "Integer",
  "settings": {
    "@odata.type": "microsoft.graph.identityGovernance.workflowSetting"
  }
}
```
