<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicyReport resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the latest processing report for a lifecycle policy. Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get report](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-list-report?view=graph-rest-beta) | [lifecyclePolicyReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyreport?view=graph-rest-beta) | Read the latest report for a lifecycle policy. |
| [List subjects](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicyreport-list-subjects?view=graph-rest-beta) | [lifecyclePolicySubjectReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreport?view=graph-rest-beta) collection | List subjects included in the report. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the report. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| policyVersion | Int32 | The version of the lifecycle policy represented by the report. |
| scopeProcessing | [microsoft.graph.identityGovernance.lifecyclePolicyScopeProcessing](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyscopeprocessing?view=graph-rest-beta) | The current and latest scope-processing status for the policy. |
| subjectsInScopeCount | Int32 | The number of subjects currently in scope for the policy. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| subjects | [microsoft.graph.identityGovernance.lifecyclePolicySubjectReport](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicysubjectreport?view=graph-rest-beta) collection | The processing results for subjects included in the report. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyReport",
  "id": "String (identifier)",
  "policyVersion": "Integer",
  "scopeProcessing": {
    "@odata.type": "microsoft.graph.identityGovernance.lifecyclePolicyScopeProcessing"
  },
  "subjectsInScopeCount": "Integer"
}
```
