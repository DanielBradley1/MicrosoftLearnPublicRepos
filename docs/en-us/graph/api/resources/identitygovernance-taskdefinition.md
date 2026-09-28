<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskdefinition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# taskDefinition resource type

Namespace: microsoft.graph.identityGovernance

Represents the built-in tasks that you can use to construct tasks for lifecycle workflows. Each task has a unique template identifier. For a full list of available built-in tasks, see [Configure the arguments for built-in Lifecycle Workflow tasks](https://learn.microsoft.com/en-us/graph/identitygovernance-lifecycleworkflows-task-arguments).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-list-taskdefinitions?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.taskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskdefinition?view=graph-rest-1.0) collection | Get a list of the [taskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskdefinition?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/identitygovernance-taskdefinition-get?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.taskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskdefinition?view=graph-rest-1.0) | Read the properties and relationships of a [taskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-taskdefinition?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | microsoft.graph.identityGovernance.lifecycleTaskCategory | The category of the HR function that the tasks created using this definition can be used with. This flagged enumeration allows multiple members to be selected simultaneously. The possible values are: `joiner`, `leaver`, `unknownFutureValue`, `mover`, `extensibility`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `mover`, `extensibility`.  <br>  <br>Supports `$filter`\(`eq`, `ne`, `has`\) and `$orderby`. |
| continueOnError | Boolean | Defines if the workflow will continue if the task has an error. |
| description | String | The description of the taskDefinition. |
| displayName | String | The display name of the taskDefinition.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |
| id | String | The unique identifier for the taskDefinition. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| parameters | [microsoft.graph.identityGovernance.parameter](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-parameter?view=graph-rest-1.0) collection | The parameters that must be supplied when creating a workflow task object.  <br>  <br>Supports `$filter`\(`any`\). |
| version | Int32 | The version number of the taskDefinition. New records are pushed when we add support for new parameters.  <br>  <br>Supports `$filter`\(`ge`, `gt`, `le`, `lt`, `eq`, `ne`\) and `$orderby`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.taskDefinition",
  "id": "String (identifier)",
  "category": "String",
  "continueOnError": "Boolean",
  "description": "String",
  "displayName": "String",
  "parameters": [
    {
      "@odata.type": "microsoft.graph.identityGovernance.parameter"
    }
  ],
  "version": "Integer"
}
```
