<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/itemactionset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# itemActionSet resource type

Namespace: microsoft.graph

The **itemActionSet** resource provides information about the actions that made up an [activity](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) on an item.

> **Note:** Item activity records are currently only available on SharePoint and OneDrive for Business.

## Properties

The following actions are currently available. Because new actions might be added in the future, make sure that your app can handle an **itemActionSet** that includes unknown actions.

| Property name | Type | Description |
| :--- | :--- | :--- |
| access | [accessAction](https://learn.microsoft.com/en-us/graph/api/resources/accessaction?view=graph-rest-1.0) | An item was accessed. |
| comment | [commentAction](https://learn.microsoft.com/en-us/graph/api/resources/commentaction?view=graph-rest-1.0) | A comment was added to the item. |
| create | [createAction](https://learn.microsoft.com/en-us/graph/api/resources/createaction?view=graph-rest-1.0) | An item was created. |
| delete | [deleteAction](https://learn.microsoft.com/en-us/graph/api/resources/deleteaction?view=graph-rest-1.0) | An item was deleted. |
| edit | [editAction](https://learn.microsoft.com/en-us/graph/api/resources/editaction?view=graph-rest-1.0) | An item was edited. |
| mention | [mentionAction](https://learn.microsoft.com/en-us/graph/api/resources/mentionaction?view=graph-rest-1.0) | A user was mentioned in the item. |
| move | [moveAction](https://learn.microsoft.com/en-us/graph/api/resources/moveaction?view=graph-rest-1.0) | An item was moved. |
| rename | [renameAction](https://learn.microsoft.com/en-us/graph/api/resources/renameaction?view=graph-rest-1.0) | An item was renamed. |
| restore | [restoreAction](https://learn.microsoft.com/en-us/graph/api/resources/restoreaction?view=graph-rest-1.0) | An item was restored. |
| share | [shareAction](https://learn.microsoft.com/en-us/graph/api/resources/shareaction?view=graph-rest-1.0) | An item was shared. |
| version | [versionAction](https://learn.microsoft.com/en-us/graph/api/resources/versionaction?view=graph-rest-1.0) | An item was versioned. |

## JSON representation

```json
{
  "access": {"@odata.type": "microsoft.graph.accessAction"},
  "comment": {"@odata.type": "microsoft.graph.commentAction"},
  "create": {"@odata.type": "microsoft.graph.createAction"},
  "delete": {"@odata.type": "microsoft.graph.deleteAction"},
  "edit": {"@odata.type": "microsoft.graph.editAction"},
  "mention": {"@odata.type": "microsoft.graph.mentionAction"},
  "move": {"@odata.type": "microsoft.graph.moveAction"},
  "rename": {"@odata.type": "microsoft.graph.renameAction"},
  "restore": {"@odata.type": "microsoft.graph.restoreAction"},
  "share": {"@odata.type": "microsoft.graph.shareAction"},
  "version": {"@odata.type": "microsoft.graph.versionAction"},
  
}
```
