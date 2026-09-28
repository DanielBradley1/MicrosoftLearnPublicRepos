<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-membershipchangetrigger?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-23 -->

# membershipChangeTrigger resource type

Namespace: microsoft.graph.identityGovernance

Represents the change in group membership that triggers the execution conditions of a workflow for a user.

Inherits from [microsoft.graph.identityGovernance.workflowExecutionTrigger](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutiontrigger?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| changeType | microsoft.graph.identityGovernance.membershipChangeType | Defines what change that happens to the workflow group to trigger the [workflowExecutionTrigger](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutiontrigger?view=graph-rest-1.0). The possible values are: `add`, `remove`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.membershipChangeTrigger",
  "changeType": "String"
}
```
