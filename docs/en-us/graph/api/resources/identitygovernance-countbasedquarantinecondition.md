<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-countbasedquarantinecondition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# countBasedQuarantineCondition resource type

Namespace: microsoft.graph.identityGovernance

Represents a [quarantineCondition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-quarantinecondition?view=graph-rest-1.0) that quarantines a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) when a single run would process more than a specified number of users. This condition is configured in the **conditions** property of a [quarantineConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-quarantineconfiguration?view=graph-rest-1.0).

Inherits from [quarantineCondition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-quarantinecondition?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| threshold | Int64 | The maximum number of users a workflow run can process before the workflow is quarantined. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.countBasedQuarantineCondition",
  "threshold": "Integer"
}
```
