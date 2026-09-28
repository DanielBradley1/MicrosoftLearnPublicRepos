<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/recentnotebook?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# recentNotebook resource type

Namespace: microsoft.graph

A recently accessed OneNote notebook. A **recentNotebook** is similar to a [notebook](https://learn.microsoft.com/en-us/graph/api/resources/notebook?view=graph-rest-1.0) but has fewer properties.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the notebook. |
| lastAccessedTime | DateTimeOffset | The date and time when the notebook was last modified. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| links | [recentNotebookLinks](https://learn.microsoft.com/en-us/graph/api/resources/recentnotebooklinks?view=graph-rest-1.0) | Links for opening the notebook. The `oneNoteClientURL` link opens the notebook in the OneNote client, if it's installed. The `oneNoteWebURL` link opens the notebook in OneNote on the web. |
| sourceService | onenoteSourceService | The backend store where the Notebook resides, either `OneDriveForBusiness` or `OneDrive`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "lastAccessedTime": "String (timestamp)",
  "links": {"@odata.type": "microsoft.graph.recentNotebookLinks"},
  "sourceService": "String"
}
```

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get recent notebooks](https://learn.microsoft.com/en-us/graph/api/notebook-getrecentnotebooks?view=graph-rest-1.0) | [notebook](https://learn.microsoft.com/en-us/graph/api/resources/notebook?view=graph-rest-1.0) collection | Get a collection of the most recently accessed notebooks for the user. |
