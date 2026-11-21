<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-attestationcomplianceissue?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# attestationComplianceIssue resource type

Namespace: microsoft.graph.identityGovernance

Represents a compliance issue that indicates an identity failed to meet an attestation requirement of its lifecycle policy.

Inherits from [complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-1.0).

## Methods

For the list of operations, see the methods of the [complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-1.0) base type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attestationBlockReasons | String collection | The reasons that prevented the identity from being attested. |
| description | String | A human-readable description of the compliance issue. Inherited from [complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-1.0). |
| governingPolicyReferenceId | String | The identifier of the lifecycle policy that generated the compliance issue. Inherited from [complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-1.0). |
| id | String | The unique identifier for the compliance issue. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| issueCode | String | A code that identifies the type of compliance issue. Inherited from [complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-1.0). |
| ruleType | String | The type of rule that generated the compliance issue, so callers can identify which rule caused non-compliance. Inherited from [complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.attestationComplianceIssue",
  "id": "String (identifier)",
  "issueCode": "String",
  "description": "String",
  "governingPolicyReferenceId": "String",
  "ruleType": "String",
  "attestationBlockReasons": [
    "String"
  ]
}
```
