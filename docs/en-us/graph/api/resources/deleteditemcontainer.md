<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/deleteditemcontainer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# deletedItemContainer resource type

Namespace: microsoft.graph

A container for deleted lifecycle workflow objects during the period before they're permanently deleted. Microsoft Entra ID Governance may permanently delete the workflows after 30 days, or you may [permanently delete the workflows](https://learn.microsoft.com/en-us/graph/api/identitygovernance-deleteditemcontainer-delete?view=graph-rest-1.0), or you may [restore the deleted workflow and its associated objects](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-restore?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List deleted workflows](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecycleworkflowscontainer-list-deleteditems?view=graph-rest-1.0) | [deletedItemContainer](https://learn.microsoft.com/en-us/graph/api/resources/deleteditemcontainer?view=graph-rest-1.0) collection | Get a list of the [deletedItemContainer](https://learn.microsoft.com/en-us/graph/api/resources/deleteditemcontainer?view=graph-rest-1.0) objects and their properties. |
| [Get a deleted workflow](https://learn.microsoft.com/en-us/graph/api/identitygovernance-deleteditemcontainer-get?view=graph-rest-1.0) | [deletedItemContainer](https://learn.microsoft.com/en-us/graph/api/resources/deleteditemcontainer?view=graph-rest-1.0) | Read the properties and relationships of a [deletedItemContainer](https://learn.microsoft.com/en-us/graph/api/resources/deleteditemcontainer?view=graph-rest-1.0) object. |
| [Restore](https://learn.microsoft.com/en-us/graph/api/identitygovernance-workflow-restore?view=graph-rest-1.0) | [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) | Restore a deleted [lifecycle workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) from the [deletedItemContainer](https://learn.microsoft.com/en-us/graph/api/resources/deleteditemcontainer?view=graph-rest-1.0) object. |
| [Permanently delete a workflow](https://learn.microsoft.com/en-us/graph/api/identitygovernance-deleteditemcontainer-delete?view=graph-rest-1.0) | None | Permanently delete a deleted [lifecycle workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) from the [lifecycleWorkflowsContainer](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecycleworkflowscontainer?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) that was deleted. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| workflows | [microsoft.graph.identityGovernance.workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) collection | Deleted workflows that end up in the deletedItemsContainer. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deletedItemContainer",
  "id": "String (identifier)"
}
```
