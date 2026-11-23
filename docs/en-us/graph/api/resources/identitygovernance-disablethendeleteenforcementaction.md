<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-disablethendeleteenforcementaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# disableThenDeleteEnforcementAction resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an enforcement action that first disables a non-compliant identity and then deletes it after a configurable grace period. This type is configured in the **enforcementAction** property of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta).

Inherits from [lifecyclePolicyEnforcementAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyenforcementaction?view=graph-rest-beta).

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
  "deletionGracePeriodInDays": "Integer"
}
```
