<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyenforcementaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# lifecyclePolicyEnforcementAction resource type

Namespace: microsoft.graph.identityGovernance

Represents the abstract base type for the action applied to an identity that becomes non-compliant with a lifecycle policy. This type is configured in the **enforcementAction** property of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0).

You can't create instances of this abstract type directly. Instead, use one of the following derived types:

- [deleteOnlyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-deleteonlyenforcementaction?view=graph-rest-1.0)
- [disableOnlyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-disableonlyenforcementaction?view=graph-rest-1.0)
- [disableThenDeleteEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-disablethendeleteenforcementaction?view=graph-rest-1.0)

Instances are differentiated by the **@odata.type** property. This is an abstract type.

## Methods

None.

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyEnforcementAction"
}
```
