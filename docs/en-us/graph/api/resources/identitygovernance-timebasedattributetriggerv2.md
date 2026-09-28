<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-timebasedattributetriggerv2?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# timeBasedAttributeTriggerV2 resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an extensible time-based trigger that evaluates a user's date attribute by using a configurable operator to initiate a [lifecycle workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-beta).

Inherits from [workflowExecutionTrigger](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutiontrigger?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attribute | String | The name of the date-type user attribute to evaluate, such as `employeeHireDate` or `employeeLeaveDateTime`. |
| operator | [microsoft.graph.identityGovernance.workflowExecutionTriggerOperator](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutiontriggeroperator?view=graph-rest-beta) | The operator that determines how to evaluate the date attribute. |

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
