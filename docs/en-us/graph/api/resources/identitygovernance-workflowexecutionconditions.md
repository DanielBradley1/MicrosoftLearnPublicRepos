<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutionconditions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# workflowExecutionConditions resource type

Namespace: microsoft.graph.identityGovernance

The derived types of this abstract object are configured in the **executionConditions** property of the [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0), [workflowTemplate](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowtemplate?view=graph-rest-1.0), and [workflowVersion](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowversion?view=graph-rest-1.0) resources. Execution conditions define when a workflow runs and which users or subjects it targets. The following types are derived from this abstract type:

- [onDemandExecutionOnly](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-ondemandexecutiononly?view=graph-rest-1.0)
- [triggerAndScopeBasedConditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-triggerandscopebasedconditions?view=graph-rest-1.0)

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.workflowExecutionConditions"
}
```
