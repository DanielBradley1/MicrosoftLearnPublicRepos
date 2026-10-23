<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicyRule resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an abstract base compliance rule that's evaluated as part of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta). Each enabled rule is evaluated independently, and any violation makes the policy noncompliant. A maximum of 10 rules are allowed per policy.

You can't create instances of this abstract type directly. Instead, use one of the following derived types:

- [periodicAttestationRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-periodicattestationrule?view=graph-rest-beta)
- [sponsorPresenceRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-sponsorpresencerule?view=graph-rest-beta)
- [inactivityRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-inactivityrule?view=graph-rest-beta)

Instances are differentiated by the **@odata.type** property. This is an abstract type.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List rules](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-list-rules?view=graph-rest-beta) | [microsoft.graph.identityGovernance.lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta) collection | Get a list of the lifecyclePolicyRule objects and their properties. |
| [Get lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicyrule-get?view=graph-rest-beta) | [microsoft.graph.identityGovernance.lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta) | Read the properties and relationships of [lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta) object. |
| [Update lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicyrule-update?view=graph-rest-beta) | [microsoft.graph.identityGovernance.lifecyclePolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyrule?view=graph-rest-beta) | Update the properties of a lifecyclePolicyRule object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| gracePeriodInDays | Int32 | The optional grace period, in days, that starts when the rule violation is first detected. The allowed range is 0 through 30. If omitted or set to `null`, the **gracePeriodInDays** value of the containing lifecycle policy applies. A value of `0` means no additional grace period. If multiple rules remain violated, the earliest rule grace-period expiry starts the policy action sequence; the policy-level grace period isn't added again. |
| id | String | The unique identifier for the rule. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
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
