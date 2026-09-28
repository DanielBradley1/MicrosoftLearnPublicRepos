<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onenote?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# onenote resource type

Namespace: microsoft.graph

Represents the entry point for OneNote resources.

All calls to the OneNote service through the Microsoft Graph API use this service root URL:

```http
https://graph.microsoft.com/{version}/{location}/onenote/ 
```

The location can be user notebooks on Microsoft 365 or consumer OneDrive, group notebooks or SharePoint site-hosted team notebooks on Microsoft 365.

**User notebooks** To access personal notebooks on consumer OneDrive or OneDrive for Business, use one of the following URLs:

```http
https://graph.microsoft.com/{version}/me/onenote/{notebooks | sections | sectionGroups | pages} 
https://graph.microsoft.com/{version}/users/{userPrincipalName}/onenote/{notebooks | sections | sectionGroups | pages} 
https://graph.microsoft.com/{version}/users/{id}/onenote/{notebooks | sections | sectionGroups | pages} 
```

**Group notebooks** To access notebooks that are owned by a group, use the following service root URL:

```http
https://graph.microsoft.com/{version}/groups/{id}/onenote/{notebooks | sections | sectionGroups | pages} 
```

**SharePoint site notebooks** To access notebooks that are owned by a SharePoint team site, use the following service root URL:

```http
https://graph.microsoft.com/{version}/sites/{id}/onenote/{notebooks | sections | sectionGroups | pages} 
```

## Authorization

For information about the permissions required to work with OneNote APIs, see [Notes permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#notes-permissions).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create notebook](https://learn.microsoft.com/en-us/graph/api/onenote-post-notebooks?view=graph-rest-1.0) | [notebook](https://learn.microsoft.com/en-us/graph/api/resources/notebook?view=graph-rest-1.0) | Create a notebook by posting to the notebooks collection. |
| [List notebooks](https://learn.microsoft.com/en-us/graph/api/onenote-list-notebooks?view=graph-rest-1.0) | [notebook](https://learn.microsoft.com/en-us/graph/api/resources/notebook?view=graph-rest-1.0) collection | Get a collection of notebooks. |
| [Create page](https://learn.microsoft.com/en-us/graph/api/onenote-post-pages?view=graph-rest-1.0) | [page](https://learn.microsoft.com/en-us/graph/api/resources/page?view=graph-rest-1.0) | Create a page by posting to the pages collection. |
| [List pages](https://learn.microsoft.com/en-us/graph/api/onenote-list-pages?view=graph-rest-1.0) | [page](https://learn.microsoft.com/en-us/graph/api/resources/page?view=graph-rest-1.0) collection | Get a collection of pages. |
| [List section groups](https://learn.microsoft.com/en-us/graph/api/onenote-list-sectiongroups?view=graph-rest-1.0) | [sectionGroup](https://learn.microsoft.com/en-us/graph/api/resources/sectiongroup?view=graph-rest-1.0) collection | Get a collection of section groups. |
| [List sections](https://learn.microsoft.com/en-us/graph/api/onenote-list-sections?view=graph-rest-1.0) | [onenoteSection](https://learn.microsoft.com/en-us/graph/api/resources/onenotesection?view=graph-rest-1.0) collection | Get a collection of sections. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| notebooks | [notebook](https://learn.microsoft.com/en-us/graph/api/resources/notebook?view=graph-rest-1.0) collection | The collection of OneNote notebooks that are owned by the user or group. Read-only. Nullable. |
| operations | [onenoteOperation](https://learn.microsoft.com/en-us/graph/api/resources/onenoteoperation?view=graph-rest-1.0) collection | The status of OneNote operations. Getting an operations collection isn't supported, but you can get the status of long-running operations if the `Operation-Location` header is returned in the response. Read-only. Nullable. |
| pages | [onenotePage](https://learn.microsoft.com/en-us/graph/api/resources/page?view=graph-rest-1.0) collection | The pages in all OneNote notebooks that are owned by the user or group. Read-only. Nullable. |
| resources | [onenoteResource](https://learn.microsoft.com/en-us/graph/api/resources/resource?view=graph-rest-1.0) collection | The image and other file resources in OneNote pages. Getting a resources collection isn't supported, but you can [get the binary content of a specific resource](https://learn.microsoft.com/en-us/graph/api/resources/resource?view=graph-rest-1.0). Read-only. Nullable. |
| sectionGroups | [sectionGroup](https://learn.microsoft.com/en-us/graph/api/resources/sectiongroup?view=graph-rest-1.0) collection | The section groups in all OneNote notebooks that are owned by the user or group. Read-only. Nullable. |
| sections | [onenoteSection](https://learn.microsoft.com/en-us/graph/api/resources/onenotesection?view=graph-rest-1.0) collection | The sections in all OneNote notebooks that are owned by the user or group. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "notebooks": [{ "@odata.type": "microsoft.graph.notebook" }],
  "operations": [{ "@odata.type": "microsoft.graph.onenoteOperation" }],
  "pages": [{ "@odata.type": "microsoft.graph.onenotePage" }],
  "resources": [ { "@odata.type": "microsoft.graph.onenoteResource" } ],
  "sectionGroups": [ { "@odata.type": "microsoft.graph.sectionGroup" } ],
  "sections": [ { "@odata.type": "microsoft.graph.onenoteSection" } ]
}
```
