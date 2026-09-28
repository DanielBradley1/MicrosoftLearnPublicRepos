<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# workflowSetting resource type

Namespace: microsoft.graph.identityGovernance

Represents the configurable settings of a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) or a [workflowVersion](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowversion?view=graph-rest-1.0). This object is configured in the **settings** property of those resources.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| quarantineConfiguration | [microsoft.graph.identityGovernance.quarantineConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-quarantineconfiguration?view=graph-rest-1.0) | The threshold configuration that automatically halts the workflow when its conditions are met. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.workflowSetting",
  "quarantineConfiguration": {
    "@odata.type": "microsoft.graph.identityGovernance.quarantineConfiguration"
  }
}
```
