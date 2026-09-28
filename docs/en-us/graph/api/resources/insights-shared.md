<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/insights-shared?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# sharedInsight resource type

Namespace: microsoft.graph

An insight representing files shared with or by a specific user. The following shared files are supported:

- Files attached directly in an email or a meeting invite.
- OneDrive for Business and SharePoint modern attachments - files stored in OneDrive for Business and SharePoint that users share as a links in an email.

**Note**: We are currently working on populating the results of the Shared API with data. There may be some data missing in the first weeks after release.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List shared \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/insights-list-shared?view=graph-rest-1.0) | [sharedInsight](https://learn.microsoft.com/en-us/graph/api/resources/insights-shared?view=graph-rest-1.0) collection | Get a list of shared files. This API is deprecated and will stop returning data after November 2026. |

## Properties

| Property | Type | Description |
| --- | --- | --- |
| id | String | Unique identifier of the relationship. Read-only. |
| lastShared | [sharingDetail](https://learn.microsoft.com/en-us/graph/api/resources/insights-sharingdetail?view=graph-rest-1.0) | Details about the shared item. Read-only. |
| resourceReference | [resourceReference](https://learn.microsoft.com/en-us/graph/api/resources/insights-resourcereference?view=graph-rest-1.0) | Reference properties of the shared document, such as the url and type of the document. Read-only |
| resourceVisualization | [resourceVisualization](https://learn.microsoft.com/en-us/graph/api/resources/insights-resourcevisualization?view=graph-rest-1.0) | Properties that you can use to visualize the document in your experience. Read-only |

## Relationships

| Property | Type | Description |
| --- | --- | --- |
| resource | entity collection | Used for navigating to the item that was shared. For file attachments, the type is *fileAttachment*. For linked attachments, the type is *driveItem*. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "string",
  "lastShared": "sharingDetail",
  "resourceVisualization": "resourceVisualization",
  "resourceReference": "resourceReference",
  
  "resource": [ { "@odata.type": "microsoft.graph.entity" } ]
}
```
