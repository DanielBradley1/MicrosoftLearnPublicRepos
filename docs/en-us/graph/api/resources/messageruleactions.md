<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/messageruleactions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# messageRuleActions resource type

Namespace: microsoft.graph

Represents the set of actions that are available to a rule.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignCategories | String collection | A list of categories to be assigned to a message. |
| copyToFolder | String | The ID of a folder that a message is to be copied to. |
| delete | Boolean | Indicates whether a message should be moved to the Deleted Items folder. |
| forwardAsAttachmentTo | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The email addresses of the recipients to which a message should be forwarded as an attachment. |
| forwardTo | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The email addresses of the recipients to which a message should be forwarded. |
| markAsRead | Boolean | Indicates whether a message should be marked as read. |
| markImportance | importance | Sets the importance of the message, which can be: `low`, `normal`, `high`. |
| moveToFolder | String | The ID of the folder that a message will be moved to. |
| permanentDelete | Boolean | Indicates whether a message should be permanently deleted and not saved to the Deleted Items folder. |
| redirectTo | [recipient](https://learn.microsoft.com/en-us/graph/api/resources/recipient?view=graph-rest-1.0) collection | The email addresses to which a message should be redirected. |
| stopProcessingRules | Boolean | Indicates whether subsequent rules should be evaluated. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "assignCategories": ["String"],
  "copyToFolder": "String",
  "delete": "Boolean",
  "forwardAsAttachmentTo": [{"@odata.type": "microsoft.graph.recipient"}],
  "forwardTo": [{"@odata.type": "microsoft.graph.recipient"}],
  "markAsRead": "Boolean",
  "markImportance": "String",
  "moveToFolder": "String",
  "permanentDelete": "Boolean",
  "redirectTo": [{"@odata.type": "microsoft.graph.recipient"}],
  "stopProcessingRules": "Boolean"
}
```
