<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-23 -->

# site resource type

Namespace: microsoft.graph

The **site** resource provides metadata and relationships for a SharePoint site.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get root site](https://learn.microsoft.com/en-us/graph/api/site-get?view=graph-rest-1.0) | site | Access the root SharePoint site within a tenant. |
| [Get site](https://learn.microsoft.com/en-us/graph/api/site-get?view=graph-rest-1.0) | site | Access a sharePoint site using the siteId. |
| [List sites across geographies](https://learn.microsoft.com/en-us/graph/api/site-getallsites?view=graph-rest-1.0) | collection of sites | List sites across all geographies in an organization. |
| [List subsites for a site](https://learn.microsoft.com/en-us/graph/api/site-list-subsites?view=graph-rest-1.0) | collection of sites | Get a collection of subsites defined for a site. |
| [List root sites](https://learn.microsoft.com/en-us/graph/api/site-list?view=graph-rest-1.0) | site | List all available sites in an organization. |
| [Get site by path](https://learn.microsoft.com/en-us/graph/api/site-getbypath?view=graph-rest-1.0) | site | Access the root SharePoint site with a relative path. |
| [Get site for a group](https://learn.microsoft.com/en-us/graph/api/site-get?view=graph-rest-1.0) | site | Access the team site for a group. |
| [Get analytics](https://learn.microsoft.com/en-us/graph/api/itemanalytics-get?view=graph-rest-1.0) | [itemAnalytics](https://learn.microsoft.com/en-us/graph/api/resources/itemanalytics?view=graph-rest-1.0) | Get analytics for this resource. |
| [Get activities by interval](https://learn.microsoft.com/en-us/graph/api/itemactivitystat-getactivitybyinterval?view=graph-rest-1.0) | [itemActivityStat](https://learn.microsoft.com/en-us/graph/api/resources/itemactivitystat?view=graph-rest-1.0) | Get a collection of **itemActivityStats** within the specified time interval. |
| [Get delta](https://learn.microsoft.com/en-us/graph/api/site-delta?view=graph-rest-1.0) | [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) collection | Get newly created, updated, or deleted [sites](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) without having to perform a full read of the entire sites collection. |
| [Search for sites](https://learn.microsoft.com/en-us/graph/api/site-search?view=graph-rest-1.0) | collection of site | Search across a SharePoint tenant for sites that match the keywords provided. |
| [Follow site](https://learn.microsoft.com/en-us/graph/api/site-follow?view=graph-rest-1.0) | collection of site | Follow a user's site or multiple sites. |
| [Unfollow site](https://learn.microsoft.com/en-us/graph/api/site-unfollow?view=graph-rest-1.0) | collection of site | Follow a user's site or multiple sites. |
| [List followed sites](https://learn.microsoft.com/en-us/graph/api/sites-list-followed?view=graph-rest-1.0) | collection of site | List the sites that are followed by the signed-in user. |
| [Get permission](https://learn.microsoft.com/en-us/graph/api/site-get-permission?view=graph-rest-1.0) | GET /sites/{site-id}/permissions/{permission-id} |  |
| [List permissions](https://learn.microsoft.com/en-us/graph/api/site-list-permissions?view=graph-rest-1.0) | GET /sites/{site-id}/permissions |  |
| [Create permissions](https://learn.microsoft.com/en-us/graph/api/site-post-permissions?view=graph-rest-1.0) | POST /sites/{site-id}/permissions |  |
| [Delete permission](https://learn.microsoft.com/en-us/graph/api/site-delete-permission?view=graph-rest-1.0) | DELETE /sites/{site-id}/permissions/{permission-id} |  |
| [Update permission](https://learn.microsoft.com/en-us/graph/api/site-update-permission?view=graph-rest-1.0) | PATCH /sites/{site-id}/permissions/{permission-id} |  |
| [List operations](https://learn.microsoft.com/en-us/graph/api/site-list-operations?view=graph-rest-1.0) | [richLongRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/richlongrunningoperation?view=graph-rest-1.0) collection | Get a list of [rich long-running operations](https://learn.microsoft.com/en-us/graph/api/resources/richlongrunningoperation?view=graph-rest-1.0) associated with a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). |
| [List pages](https://learn.microsoft.com/en-us/graph/api/basesitepage-list?view=graph-rest-1.0) | GET /sites/{site-id}/pages |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| **createdDateTime** | DateTimeOffset | The date and time the item was created. Read-only. |
| **description** | string | The descriptive text for the site. |
| **displayName** | string | The full title for the site. Read-only. |
| **eTag** | string | ETag for the item. Read-only. |
| **id** | string | The unique identifier of the item. Read-only. |
| **isPersonalSite** | bool | Identifies whether the site is personal or not. Read-only. |
| **lastModifiedDateTime** | DateTimeOffset | The date and time the item was last modified. Read-only. |
| **name** | string | The name/title of the item. |
| **root** | [root](https://learn.microsoft.com/en-us/graph/api/resources/root?view=graph-rest-1.0) | If present, provides the root site in the site collection. Read-only. |
| **sharepointIds** | [sharepointIds](https://learn.microsoft.com/en-us/graph/api/resources/sharepointids?view=graph-rest-1.0) | Returns identifiers useful for SharePoint REST compatibility. Read-only. |
| **siteCollection** | [siteCollection](https://learn.microsoft.com/en-us/graph/api/resources/sitecollection?view=graph-rest-1.0) | Provides details about the site's site collection. Available only on the root site. Read-only. |
| **webUrl** | string \(url\) | URL that displays the item in the browser. Read-only. |

### id property

A **site** is identified by a unique ID that is a composite of the following values:

- Site collection hostname \(contoso.sharepoint.com\)
- Site collection unique ID \(GUID\)
- Site unique ID \(GUID\)

The `root` identifier always references the root site for a given target, as follows:

- `/sites/root`: The tenant root site.
- `/groups/{group-id}/sites/root`: The group's team site.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| **analytics** | [itemAnalytics](https://learn.microsoft.com/en-us/graph/api/resources/itemanalytics?view=graph-rest-1.0) resource | Analytics about the view activities that took place on this site. |
| **columns** | Collection\([columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0)\) | The collection of column definitions reusable across lists under this site. |
| **contentTypes** | Collection\([contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0)\) | The collection of content types defined for this site. |
| **drive** | [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) | The default drive \(document library\) for this site. |
| **drives** | Collection\([drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0)\) | The collection of drives \(document libraries\) under this site. |
| **items** | Collection\([baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0)\) | Used to address any item contained in this site. This collection can't be enumerated. |
| **lists** | Collection\([list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0)\) | The collection of lists under this site. |
| **onenote** | [onenote](https://learn.microsoft.com/en-us/graph/api/resources/onenote?view=graph-rest-1.0) | Calls the OneNote service for notebook related operations. |
| **operations** | [richLongRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/richlongrunningoperation?view=graph-rest-1.0) collection | The collection of long-running operations on the site. |
| **pages** | Collection\([baseSitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0)\) | The collection of pages in the baseSitePages list in this site. |
| **permissions** | Collection\([permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0)\) | The permissions associated with the site. Nullable. |
| **sites** | Collection\([site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0)\) | The collection of the sub-sites under this site. |
| **termStore** | [microsoft.graph.termStore.store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0) | The default termStore under this site. |
| **termStores** | Collection\([microsoft.graph.termStore.store](https://learn.microsoft.com/en-us/graph/api/resources/termstore-store?view=graph-rest-1.0)\) | The collection of termStores under this site. |

## JSON representation

The following JSON representation shows the resource type.

The **site** resource is derived from [**baseItem**](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0) and inherits properties from that resource.

```json
{
  "id": "string",
  "isPersonalSite": "bool",
  "root": { "@odata.type": "microsoft.graph.root" },
  "sharepointIds": { "@odata.type": "microsoft.graph.sharepointIds" },
  "siteCollection": {"@odata.type": "microsoft.graph.siteCollection"},
  "displayName": "string",

  /* relationships */
  "analytics": { "@odata.type": "microsoft.graph.itemAnalytics" },
  "contentTypes": [ { "@odata.type": "microsoft.graph.contentType" }],
  "drive": { "@odata.type": "microsoft.graph.drive" },
  "drives": [ { "@odata.type": "microsoft.graph.drive" }],
  "items": [ { "@odata.type": "microsoft.graph.baseItem" }],
  "lists": [ { "@odata.type": "microsoft.graph.list" }],
  "operations": [ { "@odata.type": "microsoft.graph.richLongRunningOperation" }],
  "permissions": [ { "@odata.type": "microsoft.graph.permission" }],
  "sites": [ { "@odata.type": "microsoft.graph.site"} ],
  "columns": [ { "@odata.type": "microsoft.graph.columnDefinition" }],
  "onenote": { "@odata.type": "microsoft.graph.onenote"},
  "termStore": { "@odata.type": "microsoft.graph.termStore.store" },
  "termStores": [ { "@odata.type": "microsoft.graph.termStore.store" } ],

  /* inherited from baseItem */
  "name": "string",
  "createdDateTime": "datetime",
  "description": "string",
  "eTag": "string",
  "lastModifiedDateTime": "datetime",
  "webUrl": "url"
}
```
