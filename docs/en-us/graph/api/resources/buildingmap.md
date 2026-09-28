<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/buildingmap?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# buildingMap resource type

Namespace: microsoft.graph

Represents a map file associated with a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0) in Places. This object is the IMDF-format representation of building.geojson.

Inherits from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/buildingmap-get?view=graph-rest-1.0) | [buildingMap](https://learn.microsoft.com/en-us/graph/api/resources/buildingmap?view=graph-rest-1.0) | Get the [map](https://learn.microsoft.com/en-us/graph/api/resources/buildingmap?view=graph-rest-1.0) of a building in IMDF format. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/buildingmap-delete?view=graph-rest-1.0) | None | Delete the [map](https://learn.microsoft.com/en-us/graph/api/resources/buildingmap?view=graph-rest-1.0) of a specific building. |
| [List footprints](https://learn.microsoft.com/en-us/graph/api/buildingmap-list-footprints?view=graph-rest-1.0) | [footprintMap](https://learn.microsoft.com/en-us/graph/api/resources/footprintmap?view=graph-rest-1.0) collection | Get a list of [footprintMap](https://learn.microsoft.com/en-us/graph/api/resources/footprintmap?view=graph-rest-1.0) objects for [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0) footprints and their properties. |
| [List levels](https://learn.microsoft.com/en-us/graph/api/buildingmap-list-levels?view=graph-rest-1.0) | [levelMap](https://learn.microsoft.com/en-us/graph/api/resources/levelmap?view=graph-rest-1.0) collection | Get a list of the [levelMap](https://learn.microsoft.com/en-us/graph/api/resources/levelmap?view=graph-rest-1.0) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the **buildingMapFeature** object. Inherited from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0). |
| placeId | String | Identifier for the [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0) to which this **buildingMap** belongs. |
| properties | String | Concatenated key-value pair of all properties of a GeoJSON file for this **buildingMap**. Inherited from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| footprints | [footprintMap](https://learn.microsoft.com/en-us/graph/api/resources/footprintmap?view=graph-rest-1.0) collection | Represents the approximate physical extent of a referenced [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0). It corresponds to footprint.geojson in IMDF format. |
| levels | [levelMap](https://learn.microsoft.com/en-us/graph/api/resources/levelmap?view=graph-rest-1.0) collection | Represents a physical floor structure within a building. It corresponds to level.geojson in IMDF format. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.buildingMap",
  "id": "String (identifier)",
  "placeId": "String",
  "properties": "String"
}
```
