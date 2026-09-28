<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/iteminsights?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-31 -->

# itemInsights resource type

Namespace: microsoft.graph

Represents relationships between a user and items such as OneDrive for work or school documents, calculated using advanced analytics and machine learning techniques. You can, for example, identify OneDrive for work or school documents trending around users. Derived from [officeGraphInsights](https://learn.microsoft.com/en-us/graph/api/resources/officegraphinsights?view=graph-rest-1.0).

Insights are returned by the following APIs:

- [Shared](https://learn.microsoft.com/en-us/graph/api/resources/insights-shared?view=graph-rest-1.0) - returns documents shared with a user. Documents can be shared as email attachments or as OneDrive for work or school links sent in emails.
- [Trending](https://learn.microsoft.com/en-us/graph/api/resources/insights-trending?view=graph-rest-1.0) - returns documents from OneDrive for work or school and from SharePoint sites trending around a user.
- [Used](https://learn.microsoft.com/en-us/graph/api/resources/insights-used?view=graph-rest-1.0) - returns documents viewed and modified by a user. Includes documents the user used in OneDrive for work or school and SharePoint.

Each insight is returned with a **resourceVisualization** and **resourceReference** complex value type \(CVT\). The **resourceVisualization** CVT contains properties such as **title** and **previewImageUrl**. Microsoft uses the visualization properties to render the files in experiences like Microsoft365.com.

### Limiting item insights

Update [insightsSettings](https://learn.microsoft.com/en-us/graph/api/resources/insightssettings?view=graph-rest-1.0) to disable item insights for a specific Microsoft Entra group or an entire organization. For more information, see [customize insights privacy](https://learn.microsoft.com/en-us/graph/insights-customize-item-insights-privacy).

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| shared | [sharedInsight](https://learn.microsoft.com/en-us/graph/api/resources/insights-shared?view=graph-rest-1.0) collection | Calculated relationship that identifies documents shared with or by the user, includes file attachments in emails and meetings, as well as URLs and reference attachments to OneDrive for work or school and SharePoint, files found in emails, meetings, and Teams conversations. Ordered by recency of share. Inherited from [officeGraphInsights](https://learn.microsoft.com/en-us/graph/api/resources/officegraphinsights?view=graph-rest-1.0). |
| trending | [trending](https://learn.microsoft.com/en-us/graph/api/resources/insights-trending?view=graph-rest-1.0) collection | Calculated relationship that identifies documents trending around a user. Trending documents are calculated based on activity of the user's closest network of people and include files stored in OneDrive for work or school and SharePoint. Trending insights help users discover potentially useful content they have access to but have never viewed before. Inherited from [officeGraphInsights](https://learn.microsoft.com/en-us/graph/api/resources/officegraphinsights?view=graph-rest-1.0). |
| used | [usedInsight](https://learn.microsoft.com/en-us/graph/api/resources/insights-used?view=graph-rest-1.0) collection | Calculated relationship that identifies the latest documents viewed and modified by a user, including OneDrive for work or school and SharePoint documents. Ranked by recency of use. Inherited from [officeGraphInsights](https://learn.microsoft.com/en-us/graph/api/resources/officegraphinsights?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "shared": [ { "@odata.type": "microsoft.graph.shared" } ],
  "trending": [ { "@odata.type": "microsoft.graph.trending" } ],
  "used": [ { "@odata.type": "microsoft.graph.used" } ]
}
```
