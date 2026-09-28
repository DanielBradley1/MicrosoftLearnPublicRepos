<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# building resource type

Namespace: microsoft.graph

Represents a building within the tenant.

Inherits from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Ingest map file](https://learn.microsoft.com/en-us/graph/api/building-ingestmapfile?view=graph-rest-1.0) | None | Ingest the map file for a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0) in Places. |

For more supported methods, see [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The physical address of the **building**, including the street, city, state, country or region, and postal code. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| displayName | String | The name that is associated with the building. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| geoCoordinates | [outlookGeoCoordinates](https://learn.microsoft.com/en-us/graph/api/resources/outlookgeocoordinates?view=graph-rest-1.0) | Specifies the **building** location in latitude, longitude, and \(optionally\) altitude coordinates. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| id | String | The unique identifier for the building. Read-only. This identifier isn't immutable and can change if the mailbox or tenant configuration changes. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| isWheelChairAccessible | Boolean | Indicates whether the **building** is wheelchair accessible. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| label | String | User-defined description of the building. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| parentId | String | Currently, buildings don't have a parent. Don't use. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| phone | String | The phone number of the **building**. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| resourceLinks | [resourceLink](https://learn.microsoft.com/en-us/graph/api/resources/resourcelink?view=graph-rest-1.0) collection | A set of links to external resources that are associated with the **building**. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| tags | String collection | Custom tags that are associated with the building for categorization or filtering. Inherited from [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0). |
| wifiState | placeFeatureEnablement | A state that indicates whether the **building** has Wi-Fi. The possible values are: `unknown`, `enabled`, `disabled`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| map | [buildingMap](https://learn.microsoft.com/en-us/graph/api/resources/buildingmap?view=graph-rest-1.0) | Map file associated with a building in Places. This object is the IMDF-format representation of building.geojson. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.building",
  "address": {"@odata.type": "microsoft.graph.physicalAddress"},
  "displayName": "String",
  "geoCoordinates": {"@odata.type": "microsoft.graph.outlookGeoCoordinates"},
  "id": "String (identifier)",
  "isWheelChairAccessible": "Boolean",
  "label": "String",
  "parentId": "String",
  "phone": "String",
  "resourceLinks": [{"@odata.type": "microsoft.graph.resourceLink"}],
  "tags": ["String"],
  "wifiState": "String"
}
```
