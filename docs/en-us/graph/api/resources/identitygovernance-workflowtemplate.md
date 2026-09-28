<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# workflowTemplate resource type

Namespace: microsoft.graph.identityGovernance

Represents the pre-configured templates of Lifecycle Workflows that are available in Microsoft Entra ID. Workflow templates are available for common scenarios such as new hires and users that are leaving the organization.

Workflow templates allow you to set up workflows based on common lifecycle management scenarios. You can also create custom workflows from the workflow templates to achieve specific situations.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-list-workflowtemplates?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflowTemplate](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtemplate?view=graph-rest-1.0) collection | Get a list of the [workflowTemplate](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtemplate?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflowtemplate-get?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.workflowTemplate](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtemplate?view=graph-rest-1.0) | Read the properties and relationships of a [workflowTemplate](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtemplate?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | microsoft.graph.identityGovernance.lifecycleWorkflowCategory | The category of the workflow template. The possible values are: `joiner`, `leaver`, `unknownFutureValue`, `mover`, `extensibility`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `mover`, `extensibility`.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |
| description | String | The description of the `workflowTemplate`. |
| displayName | String | The display name of the `workflowTemplate`.  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |
| executionConditions | [microsoft.graph.identityGovernance.workflowExecutionConditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutionconditions?view=graph-rest-1.0) | Conditions describing when to execute the workflow and the criteria to identify in-scope subject set. |
| id | String | The unique identifier for the `workflowTemplate`.Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).  <br>  <br>Supports `$filter`\(`eq`, `ne`\) and `$orderby`. |

### Supported workflow templates

Lifecycle Workflows currently provide the following predefined workflow templates:

| Workflow template type | Lifecycle category |
| --- | --- |
| Onboard pre-hire employee | Joiner |
| Onboard new hire employee | Joiner |
| Post-Onboarding new hire employee | Joiner |
| Real-time employee change | Mover |
| Employee group membership changes | Mover |
| Employee job profile change | Mover |
| Real-time employee termination | Leaver |
| Pre-Offboarding of an employee | Leaver |
| Offboard an employee | Leaver |
| Post-Offboarding of an employee | Leaver |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| tasks | [microsoft.graph.identityGovernance.task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) collection | Represents the configured tasks to execute and their execution sequence within a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0). This relationship is expanded by default. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.workflowTemplate",
  "id": "String (identifier)",
  "category": "String",
  "description": "String",
  "displayName": "String",
  "executionConditions": {
    "@odata.type": "microsoft.graph.identityGovernance.workflowExecutionConditions"
  }
}
```
