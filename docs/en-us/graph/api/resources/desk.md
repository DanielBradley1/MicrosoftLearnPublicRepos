<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/desk?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# desk resource type

Namespace: microsoft.graph

Represents individual desks.

Inherits from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

## Methods

For the list of supported methods, see [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The physical address of the **desk**, including the street, city, state, country or region, and postal code. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| displayDeviceName | String | The name of the display device \(for example, `monitor` or `projector`\) that is available at the **desk**. |
| displayName | String | The name that is associated with the **desk**. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| geoCoordinates | [outlookGeoCoordinates](https://learn.microsoft.com/en-us/graph/api/resources/outlookgeocoordinates?view=graph-rest-1.0) | Specifies the **desk** location in latitude, longitude, and \(optionally\) altitude coordinates. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| heightAdjustableState | placeFeatureEnablement | A state that indicates whether the **desk** is height adjustable. The possible values are: `unknown`, `enabled`, `disabled`, `unknownFutureValue`. |
| id | String | The unique identifier for the **desk**. Read-only. This identifier isn't immutable and can change if the mailbox or tenant configuration changes. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| isWheelChairAccessible | Boolean | Indicates whether the **desk** is wheelchair accessible. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| label | String | User-defined description of the **desk**. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| mailboxDetails | [mailboxDetails](https://learn.microsoft.com/en-us/graph/api/resources/mailboxdetails?view=graph-rest-1.0) | The mailbox object **id** and email address that are associated with the desk. |
| mode | [placeMode](https://learn.microsoft.com/en-us/graph/api/resources/placemode?view=graph-rest-1.0) | The mode of the desk. The supported modes are:<br><br>- [assignedPlaceMode](https://learn.microsoft.com/en-us/graph/api/resources/assignedplacemode?view=graph-rest-1.0) - Desks that are assigned to a user.<br>- [reservablePlaceMode](https://learn.microsoft.com/en-us/graph/api/resources/reservableplacemode?view=graph-rest-1.0) - Desks that can be booked in advance using desk reservation tools.<br>- [dropInPlaceMode](https://learn.microsoft.com/en-us/graph/api/resources/dropinplacemode?view=graph-rest-1.0) - First come, first served desks. When you plug into a peripheral on one of these desks, the desk is booked for you, assuming the peripheral is associated with the desk in the Microsoft Teams Rooms pro management portal.<br>- [unavailablePlaceMode](https://learn.microsoft.com/en-us/graph/api/resources/unavailableplacemode?view=graph-rest-1.0) - Desks that are taken down for maintenance or marked as not reservable. |
| parentId | String | The ID of a parent [section](https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0). Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| phone | String | The phone number of the **desk**. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| placeId | String | A stable service-level identifier for the **desk** object used by Places workloads. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| servicePlans | [placeServicePlanInfo](https://learn.microsoft.com/en-us/graph/api/resources/placeserviceplaninfo?view=graph-rest-1.0) collection | The service plans associated with the **desk**. |
| tags | String collection | Custom tags that are associated with the **desk** for categorization or filtering. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.desk",
  "address": {"@odata.type": "microsoft.graph.physicalAddress"},
  "displayDeviceName": "String",
  "displayName": "String",
  "geoCoordinates": {"@odata.type": "microsoft.graph.outlookGeoCoordinates"},
  "heightAdjustableState": "String",
  "id": "String (identifier)",
  "isWheelChairAccessible": "Boolean",
  "label": "String",
  "mailboxDetails": {"@odata.type": "microsoft.graph.mailboxDetails"},
  "mode": {"@odata.type": "microsoft.graph.placeMode"},
  "parentId": "String",
  "phone": "String",
  "placeId": "String",
  "servicePlans": [{"@odata.type": "microsoft.graph.placeServicePlanInfo"}],
  "tags": ["String"]
}
```
