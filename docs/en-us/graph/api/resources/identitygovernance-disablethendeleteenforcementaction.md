<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-disablethendeleteenforcementaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# disableThenDeleteEnforcementAction resource type

Namespace: microsoft.graph.identityGovernance

Represents an enforcement action that first disables a non-compliant identity and then deletes it after a configurable grace period. This type is configured in the **enforcementAction** property of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0).

Inherits from [lifecyclePolicyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyenforcementaction?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deletionGracePeriodInDays | Int32 | The number of days to wait after disabling a non-compliant identity before deleting it. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.disableThenDeleteEnforcementAction",
  "deletionGracePeriodInDays": "Int32"
}
```
