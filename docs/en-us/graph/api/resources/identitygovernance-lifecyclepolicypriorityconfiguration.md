<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# lifecyclePolicyPriorityConfiguration resource type

Namespace: microsoft.graph.identityGovernance

Represents the ordered list of [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) objects that are evaluated for a given subject type. Policies are evaluated in priority order, and only the highest-priority matching policy binds to an identity.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicypriorityconfiguration-get?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-1.0) | Read the properties and relationships of [lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-1.0) object. |
| [Update lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicypriorityconfiguration-update?view=graph-rest-1.0) | None | Update the properties of a lifecyclePolicyPriorityConfiguration object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the priority configuration, which corresponds to the subject type that the configuration applies to. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| orderedPolicyIds | String collection | The identifiers of the lifecycle policies in evaluation priority order. The first policy in the collection has the highest priority. A maximum of 10 policies are allowed per subject type. |
| subjectType | microsoft.graph.identityGovernance.subjectType | The subject type that the lifecycle policies in this configuration apply to. The possible values are: `user`, `agentIdentity`, `unknownFutureValue`, `provisioningObject`. Use the `Prefer: include-unknown-enum-members` request header to get the `provisioningObject` value in this evolvable enum. Immutable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyPriorityConfiguration",
  "id": "String (identifier)",
  "orderedPolicyIds": [
    "String"
  ],
  "subjectType": "String"
}
```
