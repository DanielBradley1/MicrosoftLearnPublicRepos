<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mentionaction?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# mentionAction resource type

Namespace: microsoft.graph

The **MentionAction** resource provides information about an [activity](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) that mentioned people.

> **Note:** Item activity records are currently only available on SharePoint and OneDrive for Business.

## Properties

| Property name | Type | Description |
| :--- | :--- | :--- |
| mentionees | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) collection | The identities of the users mentioned in this action. |

## JSON representation

```json
{
  "mentionees": [{"@odata.type": "microsoft.graph.identitySet"}]
}
```
