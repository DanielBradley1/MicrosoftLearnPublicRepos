<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/commentaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# commentAction resource type

Namespace: microsoft.graph

The **commentAction** resource provides information about a comment [activity](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) made on an item.

> **Note:** Item activity records are currently only available on SharePoint and OneDrive for Business.

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| isReply | Boolean | If true, this activity was a reply to an existing comment thread. |
| parentAuthor | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity of the user who started the comment thread. |
| participants | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) collection | The identities of the users participating in this comment thread. |

## JSON representation

```json
{
  "isReply": false,
  "parentAuthor": {"@odata.type": "microsoft.graph.identitySet"},
  "participants": [{"@odata.type": "microsoft.graph.identitySet"}]
}
```
