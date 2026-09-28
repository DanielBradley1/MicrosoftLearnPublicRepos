<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/roomlist?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# roomList resource type

Namespace: microsoft.graph

Represents a group of [room](https://learn.microsoft.com/en-us/graph/api/resources/room?view=graph-rest-1.0) or [workspace](https://learn.microsoft.com/en-us/graph/api/resources/workspace?view=graph-rest-1.0) resources defined in the tenant. A **roomList** can contain a mix of **room** and **workspace** resources.

In Exchange Online, each **roomList** is associated with a mailbox.

Inherits from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List places](https://learn.microsoft.com/en-us/graph/api/place-list?view=graph-rest-1.0) | A collection of the requested, derived type of [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) | Get a collection of the specified type of **place** object defined in the tenant. For example, you can get all the rooms, all the workspaces, all the room lists, the workspaces in a specific room list, or the rooms in a specific room list in the tenant. |
| [Get place](https://learn.microsoft.com/en-us/graph/api/place-get?view=graph-rest-1.0) | The requested, derived type of [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) | Get the properties and relationships of the specified **place** object, such as a room list. |
| [Update place](https://learn.microsoft.com/en-us/graph/api/place-update?view=graph-rest-1.0) | The requested, derived type of [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) | Update the properties and relationships of a specified **place** object. |

For more supported methods, see [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The street address of the room list. |
| displayName | String | The name associated with the room list. |
| emailAddress | String | The email address of the room list. |
| geoCoordinates | [outlookGeoCoordinates](https://learn.microsoft.com/en-us/graph/api/resources/outlookgeocoordinates?view=graph-rest-1.0) | Specifies the room list location in latitude, longitude, and \(optionally\) altitude coordinates. |
| id | String | Unique identifier for the room list. Read-only. This identifier isn't immutable and can change if there are changes to the mailbox or to the tenant configuration. |
| isWheelChairAccessible | Boolean | If the room allows wheelchairs. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| label | String | The label of the room list. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| phone | String | The phone number of the room list. |
| parentId | String | The place ID of the parent of the room list. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| tags | String collection | Custom tags that are associated with the room list categorization or filtering. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| rooms | [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) collection | Read-only. Nullable. |
| workspaces | [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) collection | Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.roomList",
  "id": "String (identifier)",
  "displayName": "String",
  "geoCoordinates": {
    "@odata.type": "microsoft.graph.outlookGeoCoordinates"
  },
  "phone": "String",
  "address": {
    "@odata.type": "microsoft.graph.physicalAddress"
  },
  "parentId": "String",
  "tags": [
    "String"
  ],
  "isWheelChairAccessible": "Boolean",
  "label": "String",
  "emailAddress": "String"
}
```
