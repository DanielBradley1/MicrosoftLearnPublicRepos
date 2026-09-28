<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateproductknowledgebasearticle?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsQualityUpdateProductKnowledgeBaseArticle resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents a knowledge base \(KB\) article.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| articleId | String | The unique identifier for the knowledge base article. Read-only |
| articleUrl | String | The URL of the knowledge base article. Read-only |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsQualityUpdateProductKnowledgeBaseArticle",
  "articleId": "String",
  "articleUrl": "String"
}
```
