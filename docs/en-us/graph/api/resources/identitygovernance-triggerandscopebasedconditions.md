<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-triggerandscopebasedconditions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# triggerAndScopeBasedConditions resource type

Namespace: microsoft.graph.identityGovernance

Represents a lifecycle workflow running by schedule, who it runs for, and what triggers the workflow to run.

Inherits from [workflowExecutionConditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutionconditions?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| scope | [microsoft.graph.subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) | Defines who the workflow runs for. |
| trigger | [microsoft.graph.identityGovernance.workflowExecutionTrigger](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutiontrigger?view=graph-rest-1.0) | What triggers a workflow to run. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.triggerAndScopeBasedConditions",
  "scope": {
    "@odata.type": "microsoft.graph.subjectSet"
  },
  "trigger": {
    "@odata.type": "microsoft.graph.identityGovernance.workflowExecutionTrigger"
  }
}
```
