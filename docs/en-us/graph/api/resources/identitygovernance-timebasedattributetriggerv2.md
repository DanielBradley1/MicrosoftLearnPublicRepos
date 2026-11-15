<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-timebasedattributetriggerv2?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# timeBasedAttributeTriggerV2 resource type

Namespace: microsoft.graph.identityGovernance

Represents an extensible time-based trigger that evaluates a user's date attribute by using a configurable operator to initiate a [lifecycle workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0).

Inherits from [workflowExecutionTrigger](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutiontrigger?view=graph-rest-1.0).

Configure this type in the **trigger** property of [triggerAndScopeBasedConditions](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-triggerandscopebasedconditions?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attribute | String | The name of the date-type user attribute to evaluate, such as `employeeHireDate` or `employeeLeaveDateTime`. |
| operator | [microsoft.graph.identityGovernance.workflowExecutionTriggerOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutiontriggeroperator?view=graph-rest-1.0) | The operator that determines how to evaluate the date attribute. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTriggerV2",
  "attribute": "String",
  "operator": {"@odata.type": "microsoft.graph.identityGovernance.workflowExecutionTriggerOperator"}
}
```
