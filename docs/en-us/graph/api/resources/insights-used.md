<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/insights-used?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# usedInsight resource type

Namespace: microsoft.graph

Represents insights from documents used by a specific user. The insights return the most relevant documents that a user viewed or modified. This includes documents in:

- OneDrive for work or school
- SharePoint

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List used \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/insights-list-used?view=graph-rest-1.0) | [usedInsight](https://learn.microsoft.com/en-us/graph/api/resources/insights-used?view=graph-rest-1.0) collection | Get a list of used files. This API is deprecated and will stop returning data after November 2026. |

## Properties

| Property | Type | Description |
| --- | --- | --- |
| id | String | Unique identifier of the relationship. Read-only. |
| lastUsed | [usageDetails](https://learn.microsoft.com/en-us/graph/api/resources/insights-usagedetails?view=graph-rest-1.0) | Information about when the item was last viewed or modified by the user. Read-only. |
| resourceReference | [resourceReference](https://learn.microsoft.com/en-us/graph/api/resources/insights-resourcereference?view=graph-rest-1.0) | Reference properties of the used document, such as the URL and type of the document. Read-only |
| resourceVisualization | [resourceVisualization](https://learn.microsoft.com/en-us/graph/api/resources/insights-resourcevisualization?view=graph-rest-1.0) | Properties that you can use to visualize the document in your experience. Read-only |

## Relationships

| Property | Type | Description |
| --- | --- | --- |
| resource | [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0) collection | Used for navigating to the item that was used. For file attachments, the type is *fileAttachment*. For linked attachments, the type is *driveItem*. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string",
  "lastUsed": "usageDetails",
  "resourceVisualization": { "@odata.type": "microsoft.graph.resourceVisualization" },
  "resourceReference": { "@odata.type": "microsoft.graph.resourceReference" }
}
```
