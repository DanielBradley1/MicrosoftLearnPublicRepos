<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-article?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# article resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents an article, which is a narrative that provides insight into threat actors, tooling, attacks, and vulnerabilities. Articles are not blog posts about threat intelligence; while they summarize different threats, they also link to actionable content and key indicators of compromise to help users take action.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List articles](https://learn.microsoft.com/en-us/graph/api/security-threatintelligence-list-articles?view=graph-rest-1.0) | [article](https://learn.microsoft.com/en-us/graph/api/resources/security-article?view=graph-rest-1.0) collection | Get a list of the [microsoft.graph.security.article](https://learn.microsoft.com/en-us/graph/api/resources/security-article?view=graph-rest-1.0) objects and their properties. |
| [Get article](https://learn.microsoft.com/en-us/graph/api/security-article-get?view=graph-rest-1.0) | [article](https://learn.microsoft.com/en-us/graph/api/resources/security-article?view=graph-rest-1.0) | Read the properties and relationships of a [microsoft.graph.security.article](https://learn.microsoft.com/en-us/graph/api/resources/security-article?view=graph-rest-1.0) object. |
| [List article indicators](https://learn.microsoft.com/en-us/graph/api/security-article-list-indicators?view=graph-rest-1.0) | [articleIndicator](https://learn.microsoft.com/en-us/graph/api/resources/security-articleindicator?view=graph-rest-1.0) collection | Get the articleIndicator resources from the indicators navigation property. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| body | [microsoft.graph.security.formattedContent](https://learn.microsoft.com/en-us/graph/api/resources/security-formattedcontent?view=graph-rest-1.0) | Formatted article contents. |
| createdDateTime | DateTimeOffset | The date and time when this **article** was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| isFeatured | Boolean | Indicates whether this **article** is currently featured by Microsoft. |
| id | String | The system-generated ID for this **article**. |
| imageUrl | String | URL of the header image for this **article**, used for display purposes. |
| lastUpdatedDateTime | DateTimeOffset | The most recent date and time when this **article** was updated. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| summary | [microsoft.graph.security.formattedContent](https://learn.microsoft.com/en-us/graph/api/resources/security-formattedcontent?view=graph-rest-1.0) | A quick summary of this **article**. |
| tags | String collection | Tags for this **article**, communicating keywords, or key concepts. |
| title | String | The title of this **article**. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| indicators | [microsoft.graph.security.articleIndicator](https://learn.microsoft.com/en-us/graph/api/resources/security-articleindicator?view=graph-rest-1.0) collection | Indicators related to this **article**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.article",
  "body": {
    "@odata.type": "microsoft.graph.security.formattedContent"
  },
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "imageUrl": "String",
  "isFeatured": "Boolean",
  "lastUpdatedDateTime": "String (timestamp)",
  "summary": {
    "@odata.type": "microsoft.graph.security.formattedContent"
  },
  "tags": ["String"],
  "title": "String"
}
```
