<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyimpactsummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicyImpactSummary resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Summarizes the effect of a lifecycle policy on a subject during a specified period. Returned by the [impact](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-impact?view=graph-rest-beta) function.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionsTaken | [microsoft.graph.identityGovernance.lifecyclePolicyImpactAction](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyimpactaction?view=graph-rest-beta) collection | The policy actions taken for the subject during the evaluation period. |
| id | String | The unique identifier for the impact result. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| subject | [directoryObject](https://learn.microsoft.com/en-us/graph/api/resources/directoryobject?view=graph-rest-beta) | The subject evaluated by the policy. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyImpactSummary",
  "id": "String (identifier)",
  "actionsTaken": [
    {
      "@odata.type": "microsoft.graph.identityGovernance.lifecyclePolicyImpactAction"
    }
  ]
}
```
