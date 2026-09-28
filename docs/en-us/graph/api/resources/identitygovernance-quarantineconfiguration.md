<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-quarantineconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# quarantineConfiguration resource type

Namespace: microsoft.graph.identityGovernance

Represents the threshold conditions that determine when a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) is automatically quarantined to stop it from processing more users than expected. This object is configured in the **quarantineConfiguration** property of the following resources:

- [lifecycleManagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclemanagementsettings?view=graph-rest-1.0)
- [workflowSetting](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflowsetting?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| conditions | [microsoft.graph.identityGovernance.quarantineCondition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-quarantinecondition?view=graph-rest-1.0) collection | The set of threshold conditions evaluated for the workflow. Each condition is either a [countBasedQuarantineCondition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-countbasedquarantinecondition?view=graph-rest-1.0) or a [percentageBasedQuarantineCondition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-percentagebasedquarantinecondition?view=graph-rest-1.0). |
| matchMode | microsoft.graph.identityGovernance.matchMode | Determines whether any or all of the **conditions** must be met for the workflow to be quarantined. The possible values are: `any`, `all`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.quarantineConfiguration",
  "conditions": [
    {
      "@odata.type": "microsoft.graph.identityGovernance.countBasedQuarantineCondition"
    }
  ],
  "matchMode": "String"
}
```
