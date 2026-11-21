<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# lifecyclePolicyReport resource type

Namespace: microsoft.graph.identityGovernance

Represents the latest processing report for a lifecycle policy. Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get report](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-list-report?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecyclePolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-1.0) | Read the latest report for a lifecycle policy. |
| [List subjects](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicyreport-list-subjects?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecyclePolicySubjectReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreport?view=graph-rest-1.0) collection | List subjects included in the report. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the report. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| policyVersion | Int32 | The version of the lifecycle policy represented by the report. |
| scopeProcessing | [microsoft.graph.identityGovernance.lifecyclePolicyScopeProcessing](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyscopeprocessing?view=graph-rest-1.0) | The current and latest scope-processing status for the policy. |
| subjectsInScopeCount | Int32 | The number of subjects currently in scope for the policy. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| subjects | [microsoft.graph.identityGovernance.lifecyclePolicySubjectReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreport?view=graph-rest-1.0) collection | The processing results for subjects included in the report. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyReport",
  "id": "String (identifier)",
  "policyVersion": "Int32",
  "scopeProcessing": {
    "@odata.type": "microsoft.graph.identityGovernance.lifecyclePolicyScopeProcessing"
  },
  "subjectsInScopeCount": "Int32"
}
```
