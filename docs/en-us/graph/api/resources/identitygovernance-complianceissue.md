<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-complianceissue?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# complianceIssue resource type

Namespace: microsoft.graph.identityGovernance

Represents an issue that describes why an identity is non-compliant with its governing lifecycle policy. This type is the base type for compliance issues; a collection of compliance issues can contain both base and derived instances.

The following derived type is available:

- [attestationComplianceIssue](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-attestationcomplianceissue?view=graph-rest-1.0)

Instances are differentiated by the **@odata.type** property.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A human-readable description of the compliance issue. |
| governingPolicyReferenceId | String | The identifier of the lifecycle policy that generated the compliance issue. |
| id | String | The unique identifier for the compliance issue. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| issueCode | String | A code that identifies the type of compliance issue. |
| ruleType | String | The type of rule that generated the compliance issue, so callers can identify which rule caused non-compliance. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.complianceIssue",
  "id": "String (identifier)",
  "issueCode": "String",
  "description": "String",
  "governingPolicyReferenceId": "String",
  "ruleType": "String"
}
```
