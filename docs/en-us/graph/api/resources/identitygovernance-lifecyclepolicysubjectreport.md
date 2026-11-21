<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreport?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# lifecyclePolicySubjectReport resource type

Namespace: microsoft.graph.identityGovernance

Represents the lifecycle policy processing result for a single subject. Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List subjects](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicyreport-list-subjects?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecyclePolicySubjectReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreport?view=graph-rest-1.0) collection | List subject processing results for a lifecycle policy report. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| compliance | [microsoft.graph.identityGovernance.lifecyclePolicySubjectCompliance](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectcompliance?view=graph-rest-1.0) | The subject's compliance status and the date and time when it was evaluated. |
| effectivePolicy | [microsoft.graph.identityGovernance.lifecyclePolicyReference](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreference?view=graph-rest-1.0) | A reference to the effective lifecycle policy for the subject. |
| enforcement | [microsoft.graph.identityGovernance.lifecyclePolicySubjectEnforcement](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectenforcement?view=graph-rest-1.0) | The subject's enforcement status and action schedule. |
| id | String | The unique identifier for the subject report. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| relationship | microsoft.graph.identityGovernance.lifecyclePolicyRelationship | The relationship between this policy and the subject. The possible values are: `effective`, `inScopeButIneffective`, `pending`, `unknownFutureValue`. |
| subject | [microsoft.graph.identityGovernance.lifecyclePolicySubjectReference](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreference?view=graph-rest-1.0) | The subject represented by this result. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicySubjectReport",
  "compliance": {
    "@odata.type": "microsoft.graph.identityGovernance.lifecyclePolicySubjectCompliance"
  },
  "effectivePolicy": {
    "@odata.type": "microsoft.graph.identityGovernance.lifecyclePolicyReference"
  },
  "enforcement": {
    "@odata.type": "microsoft.graph.identityGovernance.lifecyclePolicySubjectEnforcement"
  },
  "id": "String (identifier)",
  "relationship": "String",
  "subject": {
    "@odata.type": "microsoft.graph.identityGovernance.lifecyclePolicySubjectReference"
  }
}
```
