<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/notebooklinks?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# notebookLinks resource type

Namespace: microsoft.graph

Links for opening a OneNote notebook.

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
