<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectcompliance?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicySubjectCompliance resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the policy-specific compliance state for a subject. Returned in the **compliance** property of a [lifecyclePolicySubjectReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreport?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| evaluatedDateTime | DateTimeOffset | The date and time when the subject's compliance was evaluated. |
| status | [microsoft.graph.identityGovernance.lifecyclePolicyComplianceStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-identitygovernance?view=graph-rest-beta#lifecyclepolicycompliancestatus-values) | The subject's compliance status. The possible values are: `notEvaluated`, `compliant`, `nonCompliant`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicySubjectCompliance",
  "evaluatedDateTime": "String (timestamp)",
  "status": "String"
}
```
