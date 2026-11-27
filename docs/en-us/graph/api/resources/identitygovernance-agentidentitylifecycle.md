<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-agentidentitylifecycle?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# agentIdentityLifecycle resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the lifecycle state of an agent identity, including its attestation status, compliance issues, and effective governing policy.

Inherits from [identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta).

## Methods

For the list of operations, see the methods of the [identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta) base type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the agent identity lifecycle state. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastAttestationDateTime | DateTimeOffset | The date and time when the agent identity was last attested. This value can be null if the identity hasn't yet been attested. Inherited from [identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| complianceIssues | [microsoft.graph.identityGovernance.complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-beta) collection | The collection of compliance issues that describe why the agent identity is currently non-compliant with its governing policy. Inherited from [identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta). |
| effectiveGoverningPolicy | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) | The highest-priority lifecycle policy that currently governs the agent identity. Supports `$expand`. Inherited from [identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.agentIdentityLifecycle",
  "id": "String (identifier)",
  "lastAttestationDateTime": "String (timestamp)"
}
```
