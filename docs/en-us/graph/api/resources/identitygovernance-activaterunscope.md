<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-activaterunscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-12 -->

# activateRunScope resource type

Namespace: microsoft.graph.identityGovernance

Represents activating a run scope for a [run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) of a workflow.

Inherits from [microsoft.graph.identityGovernance.activationScope](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-activationscope?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| taskScope | microsoft.graph.identityGovernance.activationTaskScopeType | Defines which tasks are in scope for the workflow run. The possible values are: `allTasks`, `failedTasks`, `unknownFutureValue`. |
| userScope | microsoft.graph.identityGovernance.activationUserScopeType | Defines which users are in scope. The possible values are: `allUsers`, `failedUsers`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| run | [microsoft.graph.identityGovernance.run](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-run?view=graph-rest-1.0) | The specific run scope for the workflow being run. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.activateRunScope",
  "userScope": "String",
  "taskScope": "String"
}
```
