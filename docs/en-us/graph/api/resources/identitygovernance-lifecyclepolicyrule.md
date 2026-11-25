<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# lifecyclePolicyRule resource type

Namespace: microsoft.graph.identityGovernance

Represents an abstract base compliance rule that's evaluated as part of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0). Each enabled rule is evaluated independently, and any violation makes the policy noncompliant. A maximum of 10 rules are allowed per policy.

Updating individual rules directly isn't supported.

You can't create instances of this abstract type directly. Instead, use one of the following derived types:

- [periodicAttestationRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-periodicattestationrule?view=graph-rest-1.0)
- [sponsorPresenceRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-sponsorpresencerule?view=graph-rest-1.0)
- [inactivityRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-inactivityrule?view=graph-rest-1.0)
- [accessPackageAssignmentRequiredRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-accesspackageassignmentrequiredrule?view=graph-rest-1.0)
- [invitationRedemptionRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-invitationredemptionrule?view=graph-rest-1.0)

Instances are differentiated by the **@odata.type** property. This is an abstract type.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| gracePeriodInDays | Int32 | The optional grace period, in days, that starts when the rule violation is first detected. The allowed range is 0 through 30. If omitted or set to `null`, the **gracePeriodInDays** value of the containing lifecycle policy applies. A value of `0` means no additional grace period. If multiple rules remain violated, the earliest rule grace-period expiry starts the policy action sequence; the policy-level grace period isn't added again. |
| id | String | The unique identifier for the rule. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isEnabled | Boolean | Indicates whether the rule is enabled and evaluated as part of its policy. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyRule",
  "gracePeriodInDays": "Int32",
  "id": "String (identifier)",
  "isEnabled": "Boolean"
}
```
