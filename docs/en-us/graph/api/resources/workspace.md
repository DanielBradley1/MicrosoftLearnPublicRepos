<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workspace?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# workspace resource type

Namespace: microsoft.graph

Represents a collection of desks. A [workspace](https://learn.microsoft.com/en-us/graph/api/resources/workspace?view=graph-rest-1.0) can be added to a [section](https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0).

Inherits from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

## Methods

For the list of supported methods, see [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The physical address of the **workspace**, including the street, city, state, country or region, and postal code. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| capacity | Int32 | The maximum number of individual desks within a **workspace**. |
| displayDeviceName | String | The name of the display device \(for example, `monitor` or `projector`\) that is available in the **workspace**. |
| displayName | String | The name that is associated with the **workspace**. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| emailAddress | String | The email address that is associated with the **workspace**. This email address is used for booking. |
| geoCoordinates | [outlookGeoCoordinates](https://learn.microsoft.com/en-us/graph/api/resources/outlookgeocoordinates?view=graph-rest-1.0) | Specifies the **workspace** location in latitude, longitude, and \(optionally\) altitude coordinates. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| id | String | The unique identifier for the **workspace**. Read-only. This identifier isn't immutable and can change if the mailbox or tenant configuration changes. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isWheelChairAccessible | Boolean | Indicates whether the **workspace** is wheelchair accessible. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| label | String | User-defined description of the **workspace**. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| mode | [placeMode](https://learn.microsoft.com/en-us/graph/api/resources/placemode?view=graph-rest-1.0) | The mode for a **workspace**. The supported modes are:<br><br>- [reservablePlaceMode](https://learn.microsoft.com/en-us/graph/api/resources/reservableplacemode?view=graph-rest-1.0) - Workspaces that can be booked in advance using desk pool reservation tools.<br>- [dropInPlaceMode](https://learn.microsoft.com/en-us/graph/api/resources/dropinplacemode?view=graph-rest-1.0) - First come, first served desks. When you plug into a peripheral on one of these desks in the workspace, the desk is booked for you, assuming that the peripheral has been associated with the desk in the Microsoft Teams Rooms pro management portal.<br>- [unavailablePlaceMode](https://learn.microsoft.com/en-us/graph/api/resources/unavailableplacemode?view=graph-rest-1.0) - Workspaces that are taken down for maintenance or marked as not reservable. |
| nickname | String | A short, friendly name for the **workspace**, often used for easier identification or display in the UI. |
| parentId | String | The ID of a parent [section](https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0). Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| phone | String | The phone number of the **workspace**. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| placeId | String | A stable service-level identifier for the **workspace** object used by Places workloads. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| tags | String collection | Custom tags that are associated with the **workspace** for categorization or filtering. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.workspace",
  "address": {"@odata.type": "microsoft.graph.physicalAddress"},
  "capacity": "Integer",
  "displayDeviceName": "String",
  "displayName": "String",
  "emailAddress": "String",
  "geoCoordinates": {"@odata.type": "microsoft.graph.outlookGeoCoordinates"},
  "id": "String (identifier)",
  "isWheelChairAccessible": "Boolean",
  "label": "String",
  "mode": {"@odata.type": "microsoft.graph.placeMode"},
  "nickname": "String",
  "parentId": "String",
  "phone": "String",
  "placeId": "String",
  "tags": ["String"]
}
```
