<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# place resource type

Namespace: microsoft.graph

Represents different space types within a tenant. For more information, see [Working with the Places API in Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/resources/places-api-overview?view=graph-rest-1.0).

Base type of [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0), [desk](https://learn.microsoft.com/en-us/graph/api/resources/desk?view=graph-rest-1.0), [floor](https://learn.microsoft.com/en-us/graph/api/resources/floor?view=graph-rest-1.0), [room](https://learn.microsoft.com/en-us/graph/api/resources/room?view=graph-rest-1.0), [roomList](https://learn.microsoft.com/en-us/graph/api/resources/roomlist?view=graph-rest-1.0), [section](https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0), and [workspace](https://learn.microsoft.com/en-us/graph/api/resources/workspace?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/place-list?view=graph-rest-1.0) | [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) collection | Get a collection of the specified type of [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) objects defined in a tenant. |
| [Create](https://learn.microsoft.com/en-us/graph/api/place-post?view=graph-rest-1.0) | [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) | Create a new [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/place-get?view=graph-rest-1.0) | [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) | Read the properties of a [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) object. Returns the requested, derived type of **place**. |
| [Update](https://learn.microsoft.com/en-us/graph/api/place-update?view=graph-rest-1.0) | [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) | Update the properties of [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) object that can be a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0), [floor](https://learn.microsoft.com/en-us/graph/api/resources/floor?view=graph-rest-1.0), [section](https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0), [desk](https://learn.microsoft.com/en-us/graph/api/resources/desk?view=graph-rest-1.0), [room](https://learn.microsoft.com/en-us/graph/api/resources/room?view=graph-rest-1.0), [workspace](https://learn.microsoft.com/en-us/graph/api/resources/workspace?view=graph-rest-1.0), or [roomList](https://learn.microsoft.com/en-us/graph/api/resources/roomlist?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/place-delete?view=graph-rest-1.0) | None | Delete a [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) object. |
| [Descendants](https://learn.microsoft.com/en-us/graph/api/place-descendants?view=graph-rest-1.0) | [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) collection | Get all the descendants of a specific type under a [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| [Create check-in claim](https://learn.microsoft.com/en-us/graph/api/place-post-checkins?view=graph-rest-1.0) | [checkInClaim](https://learn.microsoft.com/en-us/graph/api/resources/checkinclaim?view=graph-rest-1.0) | Create a new [checkInClaim](https://learn.microsoft.com/en-us/graph/api/resources/checkinclaim?view=graph-rest-1.0) object to record the check-in status for a specific place, such as a [desk](https://learn.microsoft.com/en-us/graph/api/resources/desk?view=graph-rest-1.0) or a [room](https://learn.microsoft.com/en-us/graph/api/resources/room?view=graph-rest-1.0), associated with a specific calendar reservation. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The physical address of the **place**, including the street, city, state, country or region, and postal code. |
| label | String | User-defined description of the **place**. |
| displayName | String | The name that is associated with the **place**. |
| geoCoordinates | [outlookGeoCoordinates](https://learn.microsoft.com/en-us/graph/api/resources/outlookgeocoordinates?view=graph-rest-1.0) | Specifies the **place** location in latitude, longitude, and \(optionally\) altitude coordinates. |
| id | String | The unique identifier for the **place**. Read-only. This identifier isn't immutable and can change if the mailbox or tenant configuration changes. |
| isWheelChairAccessible | Boolean | Indicates whether the **place** is wheelchair accessible. |
| parentId | String | The ID of a parent **place**. |
| phone | String | The phone number of the **place**. |
| placeId | String | A stable service-level identifier for the **place** object used by Places workloads. |
| tags | String collection | Custom tags that are associated with the **place** for categorization or filtering. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| checkIns | [checkInClaim](https://learn.microsoft.com/en-us/graph/api/resources/checkinclaim?view=graph-rest-1.0) collection | A subresource of a **place** object that indicates the check-in status of an Outlook calendar event booked at the place. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.place",
  "address": {"@odata.type": "microsoft.graph.physicalAddress"},
  "displayName": "String",
  "geoCoordinates": {"@odata.type": "microsoft.graph.outlookGeoCoordinates"},
  "id": "String (identifier)",
  "isWheelChairAccessible": "Boolean",
  "label": "String",
  "parentId": "String",
  "phone": "String",
  "placeId": "String",
  "tags": ["String"]
}
```

## Related content

[Working with the Places API in Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/resources/places-api-overview?view=graph-rest-1.0)
