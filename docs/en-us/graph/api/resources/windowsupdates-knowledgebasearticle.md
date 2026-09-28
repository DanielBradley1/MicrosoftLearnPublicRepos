<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-knowledgebasearticle?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# knowledgeBaseArticle resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a knowledge base \(KB\) article.

Each quality update contains one or more [product revisions](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-productrevision?view=graph-rest-beta). Each product revision is associated with exactly one knowledge base article.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the knowledge base article. Read-only. |
| url | String | The URL of the knowledge base article. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.knowledgeBaseArticle",
  "id": "String (identifier)",
  "url": "String"
}
```
