<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-useridentitylifecycle?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# userIdentityLifecycle resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents lifecycle information for a user governed by lifecycle policies. Inherits from [microsoft.graph.identityGovernance.identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta).

## Methods

Access this resource through the **lifecycle** relationship on a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| complianceState | microsoft.graph.identityGovernance.complianceState | The user's current lifecycle-policy compliance state. The possible values are: `compliant`, `warning`, `warningNotify`, `nonCompliant`, `unknownFutureValue`. |
| id | String | The unique identifier for the lifecycle record. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastAttestationDateTime | DateTimeOffset | The date and time of the user's latest attestation. Inherited from [identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| complianceIssues | [microsoft.graph.identityGovernance.complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-beta) collection | The user's lifecycle-policy compliance issues. Inherited from [identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta). |
| effectiveGoverningPolicy | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) | The lifecycle policy currently governing the user. Inherited from [identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta). |

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
