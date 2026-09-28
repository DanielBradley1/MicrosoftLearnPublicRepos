<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/notebook?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-20 -->

# notebook resource type

Namespace: microsoft.graph

A OneNote notebook.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "id": "string (identifier)",
  "isDefault": true,
  "isShared": true,
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "links": {"@odata.type": "microsoft.graph.notebookLinks"},
  "displayName": "string",
  "sectionGroupsUrl": "string",
  "sectionsUrl": "string",
  "self": "string",
  "userRole": "String"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user, device, and application which created the item. Read-only. |
| createdDateTime | DateTimeOffset | The date and time when the notebook was created. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| displayName | String | The name of the notebook. |
| id | String | The unique identifier of the notebook. Read-only. |
| isDefault | Boolean | Indicates whether this is the user's default notebook. Read-only. |
| isShared | Boolean | Indicates whether the notebook is shared. If true, the contents of the notebook can be seen by people other than the owner. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user, device, and application which created the item. Read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the notebook was last modified. The timestamp represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. |
| links | [NotebookLinks](https://learn.microsoft.com/en-us/graph/api/resources/notebooklinks?view=graph-rest-1.0) | Links for opening the notebook. The `oneNoteClientURL` link opens the notebook in the OneNote native client if it's installed. The `oneNoteWebURL` link opens the notebook in OneNote on the web. |
| sectionGroupsUrl | String | The URL for the `sectionGroups` navigation property, which returns all the section groups in the notebook. Read-only. |
| sectionsUrl | String | The URL for the `sections` navigation property, which returns all the sections in the notebook. Read-only. |
| self | String | The endpoint where you can get details about the notebook. Read-only. |
| userRole | onenoteUserRole | The possible values are: `Owner`, `Contributor`, `Reader`, `None`. Owner represents owner-level access to the notebook. Contributor represents read/write access to the notebook. Reader represents read-only access to the notebook. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| sectionGroups | [SectionGroup](https://learn.microsoft.com/en-us/graph/api/resources/sectiongroup?view=graph-rest-1.0) collection | The section groups in the notebook. Read-only. Nullable. |
| sections | [OnenoteSection](https://learn.microsoft.com/en-us/graph/api/resources/onenotesection?view=graph-rest-1.0) collection | The sections in the notebook. Read-only. Nullable. |

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get notebook](https://learn.microsoft.com/en-us/graph/api/notebook-get?view=graph-rest-1.0) | [Notebook](https://learn.microsoft.com/en-us/graph/api/resources/notebook?view=graph-rest-1.0) | Read the properties and relationships of the notebook. |
| [Get recent notebooks](https://learn.microsoft.com/en-us/graph/api/notebook-getrecentnotebooks?view=graph-rest-1.0) | [recentNotebook](https://learn.microsoft.com/en-us/graph/api/resources/recentnotebook?view=graph-rest-1.0) collection | Get a collection of the most recently accessed notebooks for the user. |
| [Get notebook from web](https://learn.microsoft.com/en-us/graph/api/notebook-getnotebookfromweburl?view=graph-rest-1.0) | [Notebook](https://learn.microsoft.com/en-us/graph/api/resources/notebook?view=graph-rest-1.0) | Retrieve the properties and relationships of a notebook object using its URL path. |
| [Create section group](https://learn.microsoft.com/en-us/graph/api/notebook-post-sectiongroups?view=graph-rest-1.0) | [SectionGroup](https://learn.microsoft.com/en-us/graph/api/resources/sectiongroup?view=graph-rest-1.0) | Create a section group by posting to the sectionGroups collection in the specified notebook. |
| [List section groups](https://learn.microsoft.com/en-us/graph/api/notebook-list-sectiongroups?view=graph-rest-1.0) | [SectionGroup](https://learn.microsoft.com/en-us/graph/api/resources/sectiongroup?view=graph-rest-1.0) collection | Get a collection of section groups in the specified notebook. |
| [Create section](https://learn.microsoft.com/en-us/graph/api/notebook-post-sections?view=graph-rest-1.0) | [OnenoteSection](https://learn.microsoft.com/en-us/graph/api/resources/onenotesection?view=graph-rest-1.0) | Create a section by posting to the sections collection in the specified notebook. |
| [List sections](https://learn.microsoft.com/en-us/graph/api/notebook-list-sections?view=graph-rest-1.0) | [OnenoteSection](https://learn.microsoft.com/en-us/graph/api/resources/onenotesection?view=graph-rest-1.0) collection | Get a collection of sections in the specified notebook. |
| [Copy notebook](https://learn.microsoft.com/en-us/graph/api/notebook-copynotebook?view=graph-rest-1.0) | None | Copies a notebook. |
