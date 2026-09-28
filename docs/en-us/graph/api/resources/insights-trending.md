<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/insights-trending?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-16 -->

# trending resource type

Namespace: microsoft.graph

Rich relationship connecting a user to documents that are trending around the user \(are relevant to the user\). OneDrive files, and files stored on SharePoint team sites can trend around the user.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List trending](https://learn.microsoft.com/en-us/graph/api/insights-list-trending?view=graph-rest-1.0) | [trending](https://learn.microsoft.com/en-us/graph/api/resources/insights-trending?view=graph-rest-1.0) collection | Get a list of trending files. |

## Properties

| Property | Type | Description |
| --- | --- | --- |
| id | String | Unique identifier of the relationship. Read-only. |
| lastModifiedDateTime | DateTimeOffset | The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z` |
| resourceReference | [resourceReference](https://learn.microsoft.com/en-us/graph/api/resources/insights-resourcereference?view=graph-rest-1.0) | Reference properties of the trending document, such as the url and type of the document. |
| resourceVisualization | [resourceVisualization](https://learn.microsoft.com/en-us/graph/api/resources/insights-resourcevisualization?view=graph-rest-1.0) | Properties that you can use to visualize the document in your experience. |
| weight | Double | Value indicating how much the document is currently trending. The larger the number, the more the document is currently trending around the user \(the more relevant it is\). Returned documents are sorted by this value. |

## Relationships

| Property | Type | Description |
| --- | --- | --- |
| resource | entity | Used for navigating to the trending document. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string",
  "weight": "double",
  "resourceVisualization": {"@odata.type": "microsoft.graph.resourceVisualization"},
  "resourceReference": {"@odata.type": "microsoft.graph.resourceReference"},
  "lastModifiedDateTime": "String (timestamp)"
}
```
