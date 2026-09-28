<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-19 -->

# drive resource type

Namespace: microsoft.graph

The top-level object that represents a user's OneDrive or a document library in SharePoint.

OneDrive users always have at least one drive available, their default drive. Users without a OneDrive license may not have a default drive available.

## Methods

| Method | Return type | Description |
| :--- | :--- | --- |
| [List drive](https://learn.microsoft.com/en-us/graph/api/drive-list?view=graph-rest-1.0) | drive collection | Retrieve the list of drive resources available for a target user, group, or site. |
| [Get drive](https://learn.microsoft.com/en-us/graph/api/drive-get?view=graph-rest-1.0) | drive | Get metadata about a drive. |
| [Get drive root](https://learn.microsoft.com/en-us/graph/api/driveitem-get?view=graph-rest-1.0) | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | Get root folder of a drive. |
| [List activities](https://learn.microsoft.com/en-us/graph/api/itemactivity-list?view=graph-rest-1.0) | [itemActivity](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) collection | List the recent [activities](https://learn.microsoft.com/en-us/graph/api/resources/itemactivity?view=graph-rest-1.0) that took place on a [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0), [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0), item, or within an item hierarchy. |
| [List followed items](https://learn.microsoft.com/en-us/graph/api/drive-list-following?view=graph-rest-1.0) | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) collection | List the user's followed driveItems. |
| [List children](https://learn.microsoft.com/en-us/graph/api/driveitem-list-children?view=graph-rest-1.0) | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) collection | List children of the root folder of a drive. |
| [List changes](https://learn.microsoft.com/en-us/graph/api/driveitem-delta?view=graph-rest-1.0) | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) collection | List changes for all driveItems in the drive. |
| [Search](https://learn.microsoft.com/en-us/graph/api/driveitem-search?view=graph-rest-1.0) | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) collection | Search for driveItems in a drive |
| [Get special folder](https://learn.microsoft.com/en-us/graph/api/drive-get-specialfolder?view=graph-rest-1.0) | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | Access a special folder by its canonical name. |
| [Recent \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/drive-recent?view=graph-rest-1.0) | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) collection | List a set of items recently used by the signed-in user. |
| [Shared with me \(deprecated\)](https://learn.microsoft.com/en-us/graph/api/drive-sharedwithme?view=graph-rest-1.0) | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) collection | Get a list of [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) objects shared with the owner of a [drive](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user, device, or application which created the item. Read-only. |
| createdDateTime | dateTimeOffset | Date and time of item creation. Read-only. |
| description | String | Provide a user-visible description of the drive. Read-write. |
| driveType | String | Describes the type of drive represented by this resource. OneDrive personal drives return `personal`. OneDrive for Business returns `business`. SharePoint document libraries return `documentLibrary`. Read-only. |
| id | String | The unique identifier of the drive. Read-only. |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Identity of the user, device, and application which last modified the item. Read-only. |
| lastModifiedDateTime | dateTimeOffset | Date and time the item was last modified. Read-only. |
| name | string | The name of the item. Read-write. |
| owner | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Optional. The user account that owns the drive. Read-only. |
| quota | [quota](https://learn.microsoft.com/en-us/graph/api/resources/quota?view=graph-rest-1.0) | Optional. Information about the drive's storage space quota. Read-only. |
| sharepointIds | [sharepointIds](https://learn.microsoft.com/en-us/graph/api/resources/sharepointids?view=graph-rest-1.0) | Returns identifiers useful for SharePoint REST compatibility. Read-only. This property isn't returned by default and must be selected using the `$select` query parameter. |
| system | [systemFacet](https://learn.microsoft.com/en-us/graph/api/resources/systemfacet?view=graph-rest-1.0) | If present, indicates that it's a system-managed drive. Read-only. |
| webUrl | string \(url\) | URL that displays the resource in the browser. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| bundles | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) collection | Collection of [bundles](https://learn.microsoft.com/en-us/graph/api/resources/bundle?view=graph-rest-1.0) \(albums and multi-select-shared sets of items\). Only in personal OneDrive. |
| following | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) collection | The list of items the user is following. Only in OneDrive for Business. |
| items | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) collection | All items contained in the drive. Read-only. Nullable. |
| list | [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) | For drives in SharePoint, the underlying document library list. Read-only. Nullable. |
| root | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | The root folder of the drive. Read-only. |
| special | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) collection | Collection of common folders available in OneDrive. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

The **drive** resource is derived from [**baseItem**](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0) and inherits properties from that resource.

```json
{

  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "string (timestamp)",
  "description": "string",
  "driveType": "personal | business | documentLibrary",
  "following": [{"@odata.type": "microsoft.graph.driveItem"}],
  "id": "string",
  "items": [{"@odata.type": "microsoft.graph.driveItem"}],
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "string (timestamp)",
  "name": "string",
  "owner": {"@odata.type": "microsoft.graph.identitySet"},
  "quota": {"@odata.type": "microsoft.graph.quota"},
  "root": {"@odata.type": "microsoft.graph.driveItem"},
  "sharepointIds": {"@odata.type": "microsoft.graph.sharepointIds"},
  "special": [{"@odata.type": "microsoft.graph.driveItem"}],
  "system": {"@odata.type": "microsoft.graph.systemFacet"},
  "webUrl": "string",

}
```
