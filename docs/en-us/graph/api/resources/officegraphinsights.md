<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/officegraphinsights?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-02 -->

# officeGraphInsights resource type

Namespace: microsoft.graph

Note

Use [itemInsights](https://learn.microsoft.com/en-us/graph/api/resources/iteminsights?view=graph-rest-1.0) instead of **officeGraphInsights** to access the insights API.

**officeGraphInsights** is maintained for backward compatibility with earlier versions of the insights API. It's the base type for [itemInsights](https://learn.microsoft.com/en-us/graph/api/resources/iteminsights?view=graph-rest-1.0).

Insights are relationships calculated using advanced analytics and machine learning techniques. You can, for example, identify OneDrive for work or school documents trending around users.

Insights are returned by the following APIs:

- [Trending](https://learn.microsoft.com/en-us/graph/api/resources/insights-trending?view=graph-rest-1.0) - returns documents from OneDrive for work or school and from SharePoint sites trending around a user.
- [Used](https://learn.microsoft.com/en-us/graph/api/resources/insights-used?view=graph-rest-1.0) - returns documents viewed or modified by a user. Includes documents the user used in OneDrive for work or school, and SharePoint.
- [Shared](https://learn.microsoft.com/en-us/graph/api/resources/insights-shared?view=graph-rest-1.0) - returns documents shared with or by the user. Documents can be shared as URLs, file attachments, reference attachments to OneDrive for work or school and SharePoint files found in Outlook messages and meetings.

Each insight is returned with a **resourceVisualization** and **resourceReference** complex value type \(CVT\). The **resourceVisualization** CVT contains properties such as **title** and **previewImageUrl**. Microsoft uses the visualization properties to render the files in experiences like Office Delve.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| --- | --- | --- |
| shared | [sharedInsight](https://learn.microsoft.com/en-us/graph/api/resources/insights-shared?view=graph-rest-1.0) collection | Calculated relationship that identifies documents shared with or by the user. This includes URLs, file attachments, and reference attachments to OneDrive for work or school and SharePoint files found in Outlook messages and meetings. This also includes URLs and reference attachments to Teams conversations. Ordered by recency of share. |
| trending | [trending](https://learn.microsoft.com/en-us/graph/api/resources/insights-trending?view=graph-rest-1.0) collection | Calculated relationship that identifies documents trending around a user. Trending documents are calculated based on activity of the user's closest network of people and include files stored in OneDrive for work or school and SharePoint. Trending insights help the user to discover potentially useful content that the user has access to, but has never viewed before. |
| used | [usedInsight](https://learn.microsoft.com/en-us/graph/api/resources/insights-used?view=graph-rest-1.0) collection | Calculated relationship that identifies the latest documents viewed or modified by a user, including OneDrive for work or school and SharePoint documents, ranked by recency of use. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string",
  "shared": [ { "@odata.type": "microsoft.graph.shared" } ],
  "trending": [ { "@odata.type": "microsoft.graph.trending" } ],
  "used": [ { "@odata.type": "microsoft.graph.used" } ]
}
```
