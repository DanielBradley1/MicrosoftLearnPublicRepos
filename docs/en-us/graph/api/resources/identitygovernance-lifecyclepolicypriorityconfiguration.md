<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicyPriorityConfiguration resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the ordered list of [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) objects that are evaluated for a given subject type. Policies are evaluated in priority order, and only the highest-priority matching policy binds to an identity.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List lifecyclePolicyPriorityConfigurations](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-list-lifecyclepolicypriorityconfigurations?view=graph-rest-beta) | [microsoft.graph.identityGovernance.lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-beta) collection | Get a list of the lifecyclePolicyPriorityConfiguration objects and their properties. |
| [Get lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicypriorityconfiguration-get?view=graph-rest-beta) | [microsoft.graph.identityGovernance.lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-beta) | Read the properties and relationships of [lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-beta) object. |
| [Update lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicypriorityconfiguration-update?view=graph-rest-beta) | [microsoft.graph.identityGovernance.lifecyclePolicyPriorityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicypriorityconfiguration?view=graph-rest-beta) | Update the properties of a lifecyclePolicyPriorityConfiguration object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the priority configuration, which corresponds to the subject type that the configuration applies to. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| orderedPolicyIds | String collection | The identifiers of the lifecycle policies in evaluation priority order. The first policy in the collection has the highest priority. A maximum of 10 policies are allowed per subject type. |
| subjectType | [microsoft.graph.identityGovernance.subjectType](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance?view=graph-rest-beta#subjecttype-values) | The subject type that the lifecycle policies in this configuration apply to. The possible values are: `user`, `agentIdentity`, `unknownFutureValue`, `provisioningObject`. Use the `Prefer: include-unknown-enum-members` request header to get the `provisioningObject` value in this evolvable enum. Immutable. |

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
