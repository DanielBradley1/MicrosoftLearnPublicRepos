<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-attestationcomplianceissue?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# attestationComplianceIssue resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a compliance issue that indicates an identity failed to meet an attestation requirement of its lifecycle policy.

Inherits from [complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-beta).

## Methods

For the list of operations, see the methods of the [complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-beta) base type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attestationBlockReasons | String collection | The reasons that prevented the identity from being attested. |
| description | String | A human-readable description of the compliance issue. Inherited from [complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-beta). |
| governingPolicyReferenceId | String | The identifier of the lifecycle policy that generated the compliance issue. Inherited from [complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-beta). |
| id | String | The unique identifier for the compliance issue. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| issueCode | String | A code that identifies the type of compliance issue. Inherited from [complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-beta). |
| ruleType | String | The type of rule that generated the compliance issue, so callers can identify which rule caused non-compliance. Inherited from [complianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-beta). |

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
