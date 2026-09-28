<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onenotesection?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# onenoteSection resource type

Namespace: microsoft.graph

A section in a OneNote notebook. Sections can contain pages.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "id": "string (identifier)",
  "isDefault": true,
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "links": {"@odata.type": "microsoft.graph.sectionLinks"},
  "displayName": "string",
  "pagesUrl": "string",
  "self": "string"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user, device, and application which created the item. Read-only. |
| createdDateTime | DateTimeOffset | The date and time when the section was created. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| displayName | String | The name of the section. |
| id | String | The unique identifier of the section. Read-only. |
| isDefault | Boolean | Indicates whether this is the user's default section. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user, device, and application which created the item. Read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the section was last modified. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| links | [SectionLinks](https://learn.microsoft.com/en-us/graph/api/resources/sectionlinks?view=graph-rest-1.0) | Links for opening the section. The `oneNoteClientURL` link opens the section in the OneNote native client if it's installed. The `oneNoteWebURL` link opens the section in OneNote on the web. |
| pagesUrl | String | The `pages` endpoint where you can get details for all the pages in the section. Read-only. |
| self | String | The endpoint where you can get details about the section. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| pages | [OnenotePage](https://learn.microsoft.com/en-us/graph/api/resources/page?view=graph-rest-1.0) collection | The collection of pages in the section. Read-only. Nullable. |
| parentNotebook | [Notebook](https://learn.microsoft.com/en-us/graph/api/resources/notebook?view=graph-rest-1.0) | The notebook that contains the section. Read-only. |
| parentSectionGroup | [SectionGroup](https://learn.microsoft.com/en-us/graph/api/resources/sectiongroup?view=graph-rest-1.0) | The section group that contains the section. Read-only. |

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get section](https://learn.microsoft.com/en-us/graph/api/onenotesection-get?view=graph-rest-1.0) | [OnenoteSection](https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0) | Read the properties and relationships of the section. |
| [Create page](https://learn.microsoft.com/en-us/graph/api/section-post-pages?view=graph-rest-1.0) | [Page](https://learn.microsoft.com/en-us/graph/api/resources/page?view=graph-rest-1.0) | Create a page by posting to the pages collection in the specified section. |
| [List pages](https://learn.microsoft.com/en-us/graph/api/section-list-pages?view=graph-rest-1.0) | [Page](https://learn.microsoft.com/en-us/graph/api/resources/page?view=graph-rest-1.0) collection | Get a collection of pages in the specified section. |
| [Copy to notebook](https://learn.microsoft.com/en-us/graph/api/section-copytonotebook?view=graph-rest-1.0) | None | Copy the section to a specific notebook. |
| [Copy to section group](https://learn.microsoft.com/en-us/graph/api/section-copytosectiongroup?view=graph-rest-1.0) | None | Copy the section to a specific section group. |
