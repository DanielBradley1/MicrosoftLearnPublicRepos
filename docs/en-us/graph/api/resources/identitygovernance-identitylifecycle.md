<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# identityLifecycle resource type

Namespace: microsoft.graph.identityGovernance

Represents the lifecycle state of an identity governed by lifecycle policies, including its attestation status, compliance issues, and effective governing policy.

You can't create instances of this abstract type directly. Instead, use the following derived type:

- [userIdentityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-useridentitylifecycle?view=graph-rest-1.0)
- [agentIdentityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-agentidentitylifecycle?view=graph-rest-1.0)

Instances are differentiated by the **@odata.type** property. This is an abstract type.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the identity lifecycle state. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastAttestationDateTime | DateTimeOffset | The date and time when the identity was last attested. This value can be null if the identity hasn't yet been attested. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| complianceIssues | [microsoft.graph.identityGovernance.complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-1.0) collection | The collection of compliance issues that describe why the identity is currently non-compliant with its governing policy. |
| effectiveGoverningPolicy | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) | The highest-priority lifecycle policy that currently governs the identity. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.identityLifecycle",
  "id": "String (identifier)",
  "lastAttestationDateTime": "String (timestamp)"
}
```
