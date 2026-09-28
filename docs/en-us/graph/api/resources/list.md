<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-31 -->

# List resource type

Namespace: microsoft.graph

Represents a list in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0). This resource contains the top level properties of the list, including template and field definitions.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get list](https://learn.microsoft.com/en-us/graph/api/list-get?view=graph-rest-1.0) | [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) | Get the metadata for a **list**. |
| [Create list](https://learn.microsoft.com/en-us/graph/api/list-create?view=graph-rest-1.0) | [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) | Create a new **list** in a **site**. |
| [Get items](https://learn.microsoft.com/en-us/graph/api/listitem-list?view=graph-rest-1.0) | [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) collection | Get the collection of [listItems](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) in a **list**. |
| [List activities](https://learn.microsoft.com/en-us/graph/api/itemactivity-list?view=graph-rest-1.0) | [itemActivity](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) collection | List the recent [activities](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) that took place on a [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0), [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0), item, or within an item hierarchy. |
| [Update](https://learn.microsoft.com/en-us/graph/api/listitem-update?view=graph-rest-1.0) | [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) | Update the properties on a [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/listitem-delete?view=graph-rest-1.0) | None | Delete a [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) from a **list**. |
| [Create item](https://learn.microsoft.com/en-us/graph/api/listitem-create?view=graph-rest-1.0) | [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) | Create a new [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) in a **list**. |
| [Get websocket endpoint](https://learn.microsoft.com/en-us/graph/api/subscriptions-socketio?view=graph-rest-1.0) | [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0) | Get near-real-time change notifications for a [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) and **list** using [socket.io](https://socket.io/). |
| [List operations](https://learn.microsoft.com/en-us/graph/api/list-list-operations?view=graph-rest-1.0) | [richLongRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/richlongrunningoperation?view=graph-rest-1.0) collection | Get a list of [rich long-running operations](https://learn.microsoft.com/en-us/graph/api/resources/richlongrunningoperation?view=graph-rest-1.0) associated with a **list**. |
| [List permissions](https://learn.microsoft.com/en-us/graph/api/list-list-permissions?view=graph-rest-1.0) | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) collection | Get a list of the [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) objects associated with a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0). |
| [Create permission](https://learn.microsoft.com/en-us/graph/api/list-post-permissions?view=graph-rest-1.0) | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) | Create a new [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) object on a [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the creator of this item. Read-only. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| createdDateTime | DateTimeOffset | The date and time when the item was created. Read-only. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| description | String | The descriptive text for the item. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| displayName | String | The displayable title of the list. |
| eTag | String | ETag for the item. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| id | String | The unique identifier of the item. Read-only. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the last modifier of this item. Read-only. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the item was last modified. Read-only. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| list | [listInfo](https://learn.microsoft.com/en-us/graph/api/resources/listinfo?view=graph-rest-1.0) | Contains more details about the list. |
| name | String | The name of the item. Read-only. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| parentReference | [itemReference](https://learn.microsoft.com/en-us/graph/api/resources/itemreference?view=graph-rest-1.0) | Parent information if the item has a parent. Read-write. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |
| sharepointIds | [sharepointIds](https://learn.microsoft.com/en-us/graph/api/resources/sharepointids?view=graph-rest-1.0) | Returns identifiers useful for SharePoint REST compatibility. Read-only. |
| system | [systemFacet](https://learn.microsoft.com/en-us/graph/api/resources/systemfacet?view=graph-rest-1.0) | If present, indicates that the list is system-managed. Read-only. |
| webUrl | String | URL that displays the item in the browser. Read-only. Inherited from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| columns | [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) collection | The collection of field definitions for this list. |
| contentTypes | [contentType](https://learn.microsoft.com/en-us/graph/api/resources/contenttype?view=graph-rest-1.0) collection | The collection of content types present in this list. |
| drive | [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0) | Allows access to the list as a **drive** resource with [driveItems](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0). Only present on document libraries. |
| items | [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) collection | All items contained in the list. |
| operations | [richLongRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/richlongrunningoperation?view=graph-rest-1.0) collection | The collection of long-running operations on the list. |
| permissions | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) collection | The set of permissions for the item. Read-only. Nullable. |
| subscriptions | [subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0) collection | The set of subscriptions on the list. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "createdBy": { "@odata.type": "microsoft.graph.identitySet" },
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "eTag": "String",
  "id": "String (identifier)",
  "lastModifiedBy": { "@odata.type": "microsoft.graph.identitySet" },
  "lastModifiedDateTime": "String (timestamp)",
  "list": { "@odata.type": "microsoft.graph.listInfo" },
  "name": "String",
  "parentReference": { "@odata.type": "microsoft.graph.itemReference" },
  "sharepointIds": { "@odata.type": "microsoft.graph.sharepointIds" },
  "system": "Boolean",
  "webUrl": "String"
}
```
