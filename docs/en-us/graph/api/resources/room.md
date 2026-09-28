<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/room?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# room resource type

Namespace: microsoft.graph

Represents a room within a tenant. A room can be added to a [floor](https://learn.microsoft.com/en-us/graph/api/resources/floor?view=graph-rest-1.0) or to a [section](https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0).

Inherits from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

## Methods

For the list of supported methods, see [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The street address of the room. |
| audioDeviceName | String | Specifies the name of the audio device in the room. |
| bookingType | [bookingType](#bookingtype-values) | Type of room. Possible values are: `unknown`, `standard`, `reserved`. |
| building | String | Specifies the building name or building number that the room is in. |
| capacity | Int32 | Specifies the capacity of the room. |
| displayDeviceName | String | Specifies the name of the display device in the room. |
| displayName | String | The name associated with the room. |
| emailAddress | String | Email address of the room. |
| floorLabel | String | Specifies a descriptive label for the floor, for example, P. |
| floorNumber | Int32 | Specifies the floor number that the room is on. |
| geoCoordinates | [outlookGeoCoordinates](https://learn.microsoft.com/en-us/graph/api/resources/outlookgeocoordinates?view=graph-rest-1.0) | Specifies the room location in latitude, longitude, and optionally, altitude coordinates. |
| id | String | The unique identifier for the **room**. Read-only. This identifier isn't immutable and can change if the mailbox or tenant configuration changes. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| isWheelChairAccessible | Boolean | Specifies whether the room is wheelchair accessible. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| label | String | Specifies a descriptive label for the room, for example, a number or name. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| nickname | String | Specifies a nickname for the room, for example, "conf room". |
| parentId | String | The ID of a parent [floor](https://learn.microsoft.com/en-us/graph/api/resources/floor?view=graph-rest-1.0) or [section](https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0). Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| phone | String | The phone number of the room. |
| placeId | String | A stable service-level identifier for the **room** object used by Places workloads. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| tags | String collection | Specifies other features of the room, for example, details like the type of view or furniture type. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| teamsEnabledState | placeFeatureEnablement | A state that indicates whether the **room** is enabled for Microsoft Teams. The possible values are: `unknown`, `enabled`, `disabled`, `unknownFutureValue`. |
| videoDeviceName | String | Specifies the name of the video device in the room. |

### bookingType values

| Value | Description |
| :--- | :--- |
| unknown | Unspecified booking behavior. We don't recommend that you use this value. |
| reserved | The room is available only on a first-come, first-served basis. It can't be reserved. |
| standard | The room is available and can be reserved. This value is the default. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "address": {"@odata.type": "microsoft.graph.physicalAddress"},
  "audioDeviceName": "String",
  "bookingType": "String",
  "building": "String",
  "capacity": 1024,
  "displayName": "String",
  "displayDeviceName": "String",
  "emailAddress": "String",
  "floorLabel": "String",
  "floorNumber": 1024,
  "geoCoordinates": {"@odata.type": "microsoft.graph.outlookGeoCoordinates"},
  "id": "String (identifier)",
  "isWheelChairAccessible": true,
  "label": "String",
  "nickname": "String",
  "parentId": "String",
  "phone": "String",
  "placeId": "String",
  "tags": ["String"],
  "teamsEnabledState": "String",
  "videoDeviceName": "String"
}
```
