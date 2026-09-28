<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-userinactivitytrigger?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-25 -->

# userInactivityTrigger resource type

Namespace: microsoft.graph.identityGovernance

Represents a trigger based on user inactivity that initiates workflow execution for a user.

Inherits from [microsoft.graph.identityGovernance.workflowExecutionTrigger](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutiontrigger?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| inactivityPeriodInDays | Int32 | The number of days a user must be inactive before triggering workflow execution. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.userInactivityTrigger",
  "inactivityPeriodInDays": "Integer"
}
```
