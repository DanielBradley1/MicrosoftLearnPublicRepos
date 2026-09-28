<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# workflowBase resource type

Namespace: microsoft.graph.identityGovernance

An abstract type that exposes the properties for configuring a custom lifecycle workflow. This resource is inherited by the following resource types:

- [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0)
- [workflowVersion](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowversion?view=graph-rest-1.0)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | microsoft.graph.identityGovernance.lifecycleWorkflowCategory | The category of the workflow. The possible values are: `joiner`, `leaver`, `unknownFutureValue`, `mover`, `extensibility`. Use the `Prefer: include-unknown-enum-members` request header to get the following members in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `mover`, `extensibility`. |
| createdDateTime | DateTimeOffset | When a workflow was created. |
| description | String | A string that describes the purpose of the workflow. |
| displayName | String | A string to identify the workflow. |
| executionConditions | [microsoft.graph.identityGovernance.workflowExecutionConditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutionconditions?view=graph-rest-1.0) | Defines when and for who the workflow will run. |
| isEnabled | Boolean | Whether the workflow is enabled or disabled. If this setting is `true`, the workflow can be run on demand or on schedule when **isSchedulingEnabled** is `true`. |
| isSchedulingEnabled | Boolean | If `true`, the Lifecycle Workflow engine executes the workflow based on the schedule defined by tenant settings. Can't be `true` for a disabled workflow \(where **isEnabled** is `false`\). |
| lastModifiedDateTime | DateTimeOffset | When the workflow was last modified. |
| targetSubjectType | microsoft.graph.identityGovernance.subjectType | The type of subject that the workflow targets. This flagged enumeration allows multiple members to be selected simultaneously. The possible values are: `user`, `unknownFutureValue`, `provisioningObject`. Use the `Prefer: include-unknown-enum-members` request header to get the following value from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `provisioningObject`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| administrationScopeTargets | [microsoft.graph.directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-1.0) collection | The [administrative units](https://learn.microsoft.com/en-us/graph/api/resources/administrativeunit?view=graph-rest-1.0) in the scope of the workflow. Optional.  <br>  <br>Supports `$expand`. |
| createdBy | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | The user who created the workflow. |
| lastModifiedBy | [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) | The unique identifier of the Microsoft Entra identity that last modified the workflow. |
| tasks | [microsoft.graph.identityGovernance.task](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) collection | The tasks in the workflow. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.workflowBase",
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
  "targetSubjectType": "String"
}
```
