<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectcompliance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# lifecyclePolicySubjectCompliance resource type

Namespace: microsoft.graph.identityGovernance

Represents the policy-specific compliance state for a subject. Returned in the **compliance** property of a [lifecyclePolicySubjectReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreport?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| evaluatedDateTime | DateTimeOffset | The date and time when the subject's compliance was evaluated. |
| status | microsoft.graph.identityGovernance.lifecyclePolicyComplianceStatus | The subject's compliance status. The possible values are: `notEvaluated`, `compliant`, `nonCompliant`, `unknownFutureValue`. |

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
