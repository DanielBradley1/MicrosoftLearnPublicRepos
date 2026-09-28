<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-quarantinecondition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# quarantineCondition resource type

Namespace: microsoft.graph.identityGovernance

Represents a threshold condition that is evaluated against a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) run to determine whether the workflow should be quarantined. Quarantine conditions are configured in the **conditions** property of a [quarantineConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-quarantineconfiguration?view=graph-rest-1.0).

This is an abstract type. The following types are derived from this type:

- [countBasedQuarantineCondition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-countbasedquarantinecondition?view=graph-rest-1.0)
- [percentageBasedQuarantineCondition](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-percentagebasedquarantinecondition?view=graph-rest-1.0)

The type of a condition is differentiated by its `@odata.type` property.

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.quarantineCondition"
}
```
