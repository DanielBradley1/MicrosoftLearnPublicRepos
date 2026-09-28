<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-timebasedattributetrigger?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# timeBasedAttributeTrigger resource type

Namespace: microsoft.graph.identityGovernance

Trigger based on a time-based attribute for initiating the execution of a [lifecycle workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0). The combination of scope and trigger conditions determines when a workflow is executed and on which identities.

Inherits from [workflowExecutionTrigger](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutiontrigger?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| offsetInDays | Int32 | How many days before or after the time-based attribute specified the workflow should trigger. For example, if the attribute is `employeeHireDate` and offsetInDays is -1, then the workflow should trigger one day before the employee hire date. The value can range between -180 and 180 days. |
| timeBasedAttribute | [microsoft.graph.identityGovernance.workflowTriggerTimeBasedAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-timebasedattributetrigger?view=graph-rest-1.0) | Determines which time-based identity property to reference. The possible values are: `employeeHireDate`, `employeeLeaveDateTime`, `createdDateTime`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.timeBasedAttributeTrigger",
  "offsetInDays": "Integer",
  "timeBasedAttribute": "String"
}
```
