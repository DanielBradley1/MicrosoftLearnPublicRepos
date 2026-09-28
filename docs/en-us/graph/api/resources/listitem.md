<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-31 -->

# listItem resource type

Namespace: microsoft.graph

Represents an item in a SharePoint [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0).

All items in a SharePoint document library can be represented as a **listItem** or [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) resource.

Column values in the list are available through the `fieldValueSet` dictionary.

## Methods

The following methods are available for **listItem** resources. All examples are relative to a **[list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0)**: `https://graph.microsoft.com/v1.0/sites/{site-id}/lists/{list-id}`.

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/listitem-list?view=graph-rest-1.0) | listItem collection | Get the collection of items in a list. |
| [Get](https://learn.microsoft.com/en-us/graph/api/listitem-get?view=graph-rest-1.0) | listItem | Get an item in a list. |
| [Get column values](https://learn.microsoft.com/en-us/graph/api/listitem-get?view=graph-rest-1.0) | listItem | Get column values from listItem. |
| [Get analytics](https://learn.microsoft.com/en-us/graph/api/itemanalytics-get?view=graph-rest-1.0) | [itemAnalytics](https://learn.microsoft.com/en-us/graph/api/resources/itemanalytics?view=graph-rest-1.0) | Get analytics for this resource. |
| [Get activities by interval](https://learn.microsoft.com/en-us/graph/api/itemactivitystat-getactivitybyinterval?view=graph-rest-1.0) | [itemActivityStat](https://learn.microsoft.com/en-us/graph/api/resources/itemactivitystat?view=graph-rest-1.0) | Get a collection of itemActivityStats within the specified time interval. |
| [Create](https://learn.microsoft.com/en-us/graph/api/listitem-create?view=graph-rest-1.0) | listItem | Create a new listItem in a list. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/listitem-delete?view=graph-rest-1.0) | No Content | Removes an item from a list. |
| [Update](https://learn.microsoft.com/en-us/graph/api/listitem-update?view=graph-rest-1.0) | [fieldValueSet](https://learn.microsoft.com/en-us/graph/api/resources/fieldvalueset?view=graph-rest-1.0) | Update the properties on a listItem. |
| [Update column values](https://learn.microsoft.com/en-us/graph/api/listitem-update?view=graph-rest-1.0) | [fieldValueSet](https://learn.microsoft.com/en-us/graph/api/resources/fieldvalueset?view=graph-rest-1.0) | Update column values on a listItem. |
| [List document set version](https://learn.microsoft.com/en-us/graph/api/listitem-list-documentsetversions?view=graph-rest-1.0) | [documentSetVersion](https://learn.microsoft.com/en-us/graph/api/resources/documentsetversion?view=graph-rest-1.0) collection | Get a list of the versions of a document set item in a list. |
| [Create](https://learn.microsoft.com/en-us/graph/api/listitem-post-documentsetversions?view=graph-rest-1.0) | [documentSetVersion](https://learn.microsoft.com/en-us/graph/api/resources/documentsetversion?view=graph-rest-1.0) | Create a new version of a document set item in a list. |
| [Restore](https://learn.microsoft.com/en-us/graph/api/documentsetversion-restore?view=graph-rest-1.0) | No Content | Restore the document set item to a specific version. |
| [Get delta](https://learn.microsoft.com/en-us/graph/api/listitem-delta?view=graph-rest-1.0) | [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) collection | Get newly created, updated, or deleted [list items](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) without having to perform a full read of the entire items collection. |
| [Get recent activities](https://learn.microsoft.com/en-us/graph/api/itemactivity-list?view=graph-rest-1.0) | [itemActivity](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) collection | List the recent [activities](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) that took place on a [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0), [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0), item, or within an item hierarchy. |
| [List permissions](https://learn.microsoft.com/en-us/graph/api/listitem-list-permissions?view=graph-rest-1.0) | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) collection | Get a list of the [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) objects associated with a [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0). |
| [Create permission](https://learn.microsoft.com/en-us/graph/api/listitem-post-permissions?view=graph-rest-1.0) | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) | Create a new [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) object on a [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0). |

## Properties

The **listItem** resource has the following properties.

| Property | Type | Description |
| :--- | :--- | :--- |
| contentType | [contentTypeInfo](https://learn.microsoft.com/en-us/graph/api/resources/contenttypeinfo?view=graph-rest-1.0) | The content type of this list item |

The following properties are inherited from **[baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0)**.

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the creator of this item. Read-only. |
| createdDateTime | DateTimeOffset | The date and time the item was created. Read-only. |
| deleted | [deleted](https://learn.microsoft.com/en-us/graph/api/resources/deleted?view=graph-rest-1.0) | If present in the result of a delta enumeration, indicates that the item was deleted. Read-only. |
| description | string | The descriptive text for the item. |
| eTag | string | ETag for the item. Read-only. |
| id | string | The unique identifier of the item. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the last modifier of this item. Read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time the item was last modified. Read-only. |
| name | string | The name / title of the item. |
| parentReference | [itemReference](https://learn.microsoft.com/en-us/graph/api/resources/itemreference?view=graph-rest-1.0) | Parent information, if the item has a parent. Read-write. |
| sharepointIds | [sharepointIds](https://learn.microsoft.com/en-us/graph/api/resources/sharepointids?view=graph-rest-1.0) | Returns identifiers useful for SharePoint REST compatibility. Read-only. |
| webUrl | string \(url\) | URL that displays the item in the browser. Read-only. |

## Relationships

The **listItem** resource has the following relationships to other resources.

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activities | [itemActivity](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) collection | The list of recent activities that took place on this item. |
| analytics | [itemAnalytics](https://learn.microsoft.com/en-us/graph/api/resources/itemanalytics?view=graph-rest-1.0) resource | Analytics about the view activities that took place on this item. |
| documentSetVersions | [documentSetVersion](https://learn.microsoft.com/en-us/graph/api/resources/documentsetversion?view=graph-rest-1.0) collection | Version information for a document set version created by a user. |
| driveItem | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | For document libraries, the **driveItem** relationship exposes the listItem as a **[driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0)** |
| fields | [fieldValueSet](https://learn.microsoft.com/en-us/graph/api/resources/fieldvalueset?view=graph-rest-1.0) | The values of the columns set on this list item. |
| permissions | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) collection | The set of permissions for the item. Read-only. Nullable. |
| versions | [listItemVersion](https://learn.microsoft.com/en-us/graph/api/resources/listitemversion?view=graph-rest-1.0) collection | The list of previous versions of the list item. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "contentType": { "@odata.type": "microsoft.graph.contentTypeInfo" },
  "deleted": { "@odata.type": "microsoft.graph.deleted" },
  "fields": { "@odata.type": "microsoft.graph.fieldValueSet" },
  "sharepointIds": { "@odata.type": "microsoft.graph.sharepointIds" },

  /* relationships */
  "activities": [{"@odata.type": "microsoft.graph.itemActivity"}],
  "analytics": { "@odata.type": "microsoft.graph.itemAnalytics" },
  "documentSetVersions": [{"@odata.type": "microsoft.graph.documentSetVersion"}],
  "driveItem": { "@odata.type": "microsoft.graph.driveItem" },
  "versions": [{"@odata.type": "microsoft.graph.listItemVersion"}],

  /* inherited from baseItem */
  "id": "string",
  "name": "name of resource",
  "createdBy": { "@odata.type": "microsoft.graph.identitySet" },
  "createdDateTime": "timestamp",
  "description": "description of resource",
  "eTag": "string",
  "lastModifiedBy": { "@odata.type": "microsoft.graph.identitySet" },
  "lastModifiedDateTime": "timestamp",
  "parentReference": { "@odata.type": "microsoft.graph.itemReference"},
  "webUrl": "url"
}
```
