<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# identityLifecycle resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the lifecycle state of an identity governed by lifecycle policies, including its attestation status, compliance issues, and effective governing policy.

You can't create instances of this abstract type directly. Instead, use the following derived type:

- [agentIdentityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-agentidentitylifecycle?view=graph-rest-beta)

Instances are differentiated by the **@odata.type** property. This is an abstract type.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get identityLifecycle](https://learn.microsoft.com/en-us/graph/api/identitygovernance-identitylifecycle-get?view=graph-rest-beta) | [microsoft.graph.identityGovernance.identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta) | Read the properties and relationships of [identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta) object. |
| [Update identityLifecycle](https://learn.microsoft.com/en-us/graph/api/identitygovernance-identitylifecycle-update?view=graph-rest-beta) | [microsoft.graph.identityGovernance.identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta) | Update the properties of a identityLifecycle object. |
| [List complianceIssues](https://learn.microsoft.com/en-us/graph/api/identitygovernance-identitylifecycle-list-complianceissues?view=graph-rest-beta) | [microsoft.graph.identityGovernance.complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-beta) collection | Get the compliance issues associated with the identity's lifecycle state. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the identity lifecycle state. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastAttestationDateTime | DateTimeOffset | The date and time when the identity was last attested. This value can be null if the identity hasn't yet been attested. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| complianceIssues | [microsoft.graph.identityGovernance.complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-beta) collection | The collection of compliance issues that describe why the identity is currently non-compliant with its governing policy. |
| effectiveGoverningPolicy | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) | The highest-priority lifecycle policy that currently governs the identity. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.identityLifecycle",
  "id": "String (identifier)",
  "lastAttestationDateTime": "String (timestamp)"
}
```
