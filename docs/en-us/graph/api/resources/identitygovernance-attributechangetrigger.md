<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-attributechangetrigger?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-23 -->

# attributeChangeTrigger resource type

Namespace: microsoft.graph.identityGovernance

Represents changes in user attributes that trigger the execution of workload conditions for a user.

Inherits from [microsoft.graph.identityGovernance.workflowExecutionTrigger](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowexecutiontrigger?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| triggerAttributes | [microsoft.graph.identityGovernance.triggerAttribute](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-triggerattribute?view=graph-rest-1.0) collection | The trigger attribute being changed that triggers the workflowexecutiontrigger of a workflow.\) |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.attributeChangeTrigger",
  "triggerAttributes": [
    {
      "@odata.type": "microsoft.graph.identityGovernance.triggerAttribute"
    }
  ]
}
```
