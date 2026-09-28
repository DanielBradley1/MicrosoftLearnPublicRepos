<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-deleteditemcontainer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# deletedItemContainer resource type

Namespace: microsoft.graph.identityGovernance

A container for [workflows](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) that have been deleted.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| id | String | The unique identifier for the deleted item container. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| --- | --- | --- |
| workflows | [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) collection | A collection of workflows that have been deleted. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.deletedItemContainer",
  "id": "String (identifier)",
  "workflows": [
    {
      "@odata.type": "#microsoft.graph.identityGovernance.workflow"
    }
  ]
}
```
