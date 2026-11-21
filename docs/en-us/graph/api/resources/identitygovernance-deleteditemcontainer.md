<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-deleteditemcontainer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# deletedItemContainer resource type \(lifecycle workflows\)

Namespace: microsoft.graph

A container for [workflows](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) and [lifecycle policies](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) that have been deleted.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List lifecyclePolicies](https://learn.microsoft.com/en-us/graph/api/identitygovernance-deleteditemcontainer-list-lifecyclepolicies?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) collection | Get soft-deleted lifecycle policies. |

## Properties

| Property | Type | Description |
| --- | --- | --- |
| id | String | The unique identifier for the deleted item container. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| --- | --- | --- |
| lifecyclePolicies | [microsoft.graph.identityGovernance.lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-1.0) collection | A collection of soft-deleted lifecycle policies. |
| workflows | [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) collection | A collection of workflows that have been deleted. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deletedItemContainer",
  "id": "String (identifier)",
  "lifecyclePolicies": [
    {
      "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicy"
    }
  ],
  "workflows": [
    {
      "@odata.type": "#microsoft.graph.identityGovernance.workflow"
    }
  ]
}
```
