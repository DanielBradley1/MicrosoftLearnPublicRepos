<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-percentagebasedquarantinecondition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# percentageBasedQuarantineCondition resource type

Namespace: microsoft.graph.identityGovernance

Represents a [quarantineCondition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-quarantinecondition?view=graph-rest-1.0) that quarantines a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) when a single run would process more than a specified percentage of in-scope users. This condition is configured in the **conditions** property of a [quarantineConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-quarantineconfiguration?view=graph-rest-1.0).

Inherits from [quarantineCondition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-quarantinecondition?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| percentage | Int32 | The maximum percentage of in-scope users a workflow run can process before the workflow is quarantined. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.percentageBasedQuarantineCondition",
  "percentage": "Integer"
}
```
