<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onenotepage?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# onenotePage resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A page in a OneNote notebook.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | Stream | The page's HTML content. |
| contentUrl | String | The URL for the page's HTML content. Read-only. |
| createdByAppId | String | The unique identifier of the application that created the page. Read-only. |
| createdDateTime | DateTimeOffset | The date and time when the page was created. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| id | String | The unique identifier of the page. Read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the page was last modified. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| level | Int32 | The indentation level of the page. Read-only. |
| links | [pageLinks](https://learn.microsoft.com/en-us/graph/api/resources/pagelinks?view=graph-rest-beta) | Links for opening the page. The `oneNoteClientURL` link opens the page in the OneNote native client if it 's installed. The `oneNoteWebUrl` link opens the page in OneNote on the web. Read-only. |
| order | Int32 | The order of the page within its parent section. Read-only. |
| self | String | The endpoint where you can get details about the page. Read-only. |
| title | String | The title of the page. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| parentNotebook | [notebook](https://learn.microsoft.com/en-us/graph/api/resources/notebook?view=graph-rest-beta) | The notebook that contains the page. Read-only. |
| parentSection | [onenoteSection](https://learn.microsoft.com/en-us/graph/api/resources/onenotesection?view=graph-rest-beta) | The section that contains the page. Read-only. |

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get page](https://learn.microsoft.com/en-us/graph/api/page-get?view=graph-rest-beta) | [onenotePage](https://learn.microsoft.com/en-us/graph/api/resources/onenotepage?view=graph-rest-beta) | Read the properties and relationships of the page. |
| [Update page](https://learn.microsoft.com/en-us/graph/api/page-update?view=graph-rest-beta) | None | Update the HTML content of the page. |
| [Delete page](https://learn.microsoft.com/en-us/graph/api/page-delete?view=graph-rest-beta) | None | Delete the page. |
| [Copy to section](https://learn.microsoft.com/en-us/graph/api/page-copytosection?view=graph-rest-beta) | None | Copies the page to a specific section. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "content": "stream",
  "contentUrl": "string",
  "createdByAppId": "string",
  "createdDateTime": "String (timestamp)",
  "id": "string (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "level": 1024,
  "links": {"@odata.type": "microsoft.graph.pageLinks"},
  "order": 1024,
  "self": "string",
  "title": "string"
}
```
