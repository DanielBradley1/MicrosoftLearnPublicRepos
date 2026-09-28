<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recentnotebooklinks?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# recentNotebookLinks resource type

Namespace: microsoft.graph

Links for opening a OneNote notebook. This resource type exists as a property on a [recentNotebook](https://learn.microsoft.com/en-us/graph/api/resources/recentnotebook?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| oneNoteClientUrl | [externalLink](https://learn.microsoft.com/en-us/graph/api/resources/externallink?view=graph-rest-1.0) | Opens the notebook in the OneNote native client if it's installed. |
| oneNoteWebUrl | [externalLink](https://learn.microsoft.com/en-us/graph/api/resources/externallink?view=graph-rest-1.0) | Opens the notebook in OneNote on the web. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "oneNoteClientUrl": {"@odata.type": "microsoft.graph.externalLink"},
  "oneNoteWebUrl": {"@odata.type": "microsoft.graph.externalLink"}
}
```
