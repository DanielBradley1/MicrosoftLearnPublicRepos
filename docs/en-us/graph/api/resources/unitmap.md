<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unitmap?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# unitMap resource type

Namespace: microsoft.graph

Represents a unit.geojson file in IMDF format that defines units \(such as rooms or offices\) on a floor of a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0).

Inherits from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/levelmap-list-units?view=graph-rest-1.0) | [unitMap](https://learn.microsoft.com/en-us/graph/api/resources/unitmap?view=graph-rest-1.0) collection | Get a list of the [unitMap](https://learn.microsoft.com/en-us/graph/api/resources/unitmap?view=graph-rest-1.0) objects and their properties. |
| [Update](https://learn.microsoft.com/en-us/graph/api/unitmap-update?view=graph-rest-1.0) | [unitMap](https://learn.microsoft.com/en-us/graph/api/resources/unitmap?view=graph-rest-1.0) | Update the properties of an existing [unitMap](https://learn.microsoft.com/en-us/graph/api/resources/unitmap?view=graph-rest-1.0) object in IMDF format on a specified floor, or create one if it doesn't exist. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/unitmap-delete?view=graph-rest-1.0) | None | Delete a [unitMap](https://learn.microsoft.com/en-us/graph/api/resources/unitmap?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the **unitMap** object. Inherited from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0). |
| placeId | String | Identifier of the [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) \(such as a [room](https://learn.microsoft.com/en-us/graph/api/resources/room?view=graph-rest-1.0)\) to which this **unitMap** belongs. |
| properties | String | Concatenated key-value pair of all properties of a GeoJSON file for this **unitMap**. Inherited from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unitMap",
  "id": "String (identifier)",
  "placeId": "String",
  "properties": "String"
}
```
