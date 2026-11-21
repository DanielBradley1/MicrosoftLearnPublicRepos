<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-useridentitylifecycle?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# userIdentityLifecycle resource type

Namespace: microsoft.graph.identityGovernance

Represents lifecycle information for a user governed by lifecycle policies. Inherits from [microsoft.graph.identityGovernance.identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-1.0).

## Methods

Access this resource through the **lifecycle** relationship on a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| complianceState | microsoft.graph.identityGovernance.complianceState | The user's current lifecycle-policy compliance state. The possible values are: `compliant`, `warning`, `warningNotify`, `nonCompliant`, `unknownFutureValue`. |
| id | String | The unique identifier for the lifecycle record. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastAttestationDateTime | DateTimeOffset | The date and time of the user's latest attestation. Inherited from [identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| complianceIssues | [microsoft.graph.identityGovernance.complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-1.0) collection | The user's lifecycle-policy compliance issues. Inherited from [identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-1.0). |
| effectiveGoverningPolicy | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) | The lifecycle policy currently governing the user. Inherited from [identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.userIdentityLifecycle",
  "complianceState": "String",
  "id": "String (identifier)",
  "lastAttestationDateTime": "String (timestamp)"
}
```
