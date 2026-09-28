<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/shareddriveitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-27 -->

# sharedDriveItem resource type

Namespace: microsoft.graph

The **sharedDriveItem** resource is returned when using the [shares](https://learn.microsoft.com/en-us/graph/api/shares-get?view=graph-rest-1.0) API to access a shared [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).

The **sharedDriveItem** resource is derived from [baseItem](https://learn.microsoft.com/en-us/graph/api/resources/baseitem?view=graph-rest-1.0) and inherits properties from that resource.

For more information about the facets on a DriveItem, see [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Use sharing links](https://learn.microsoft.com/en-us/graph/api/shares-get?view=graph-rest-1.0) | [sharedDriveItem](https://learn.microsoft.com/en-us/graph/api/resources/shareddriveitem?view=graph-rest-1.0) | Access a shared item or a collection of shared items by using a **shareId** or sharing URL. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the share being accessed. |
| name | String | The display name of the shared item. |
| owner | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | Information about the owner of the shared item being referenced. |

## Relationships

| Relationship name | Type | Description |
| --- | :--- | :--- |
| driveItem | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | Used to access the underlying driveItem |
| list | [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) | Used to access the underlying list |
| listItem | [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) | Used to access the underlying listItem |
| permission | [permission](https://learn.microsoft.com/en-us/graph/api/resources/permission?view=graph-rest-1.0) | Used to access the permission representing the underlying sharing link |
| site | [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0) | Used to access the underlying site |

Alternatively, for **driveItems** shared from personal OneDrive accounts, the following relationships may also be used.

| Relationship name | Type | Description |
| --- | :--- | :--- |
| items | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) collection | All driveItems contained in the sharing root. This collection cannot be enumerated. |
| root | [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) | Used to access the underlying driveItem. Deprecated -- use `driveItem` instead. |

## JSON representation

The following JSON representation shows the resource.

```json
{
  "id": "string",
  "name": "string",
  "owner": { "@odata.type": "microsoft.graph.identitySet" },

  "driveItem": { "@odata.type": "microsoft.graph.driveItem" },
  "items": [ { "@odata.type": "microsoft.graph.driveItem" }],
  "list": { "@odata.type": "microsoft.graph.list" },
  "listItem": { "@odata.type": "microsoft.graph.listItem" },
  "root": { "@odata.type": "microsoft.graph.driveItem" },
  "site": { "@odata.type": "microsoft.graph.site" }
}
```
