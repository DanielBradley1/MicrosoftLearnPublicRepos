<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/footprintmap?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# footprintMap resource type

Namespace: microsoft.graph

Represents a footprint.geojson file in IMDF format that defines the approximate physical extent of a referenced [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0).

Inherits from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/buildingmap-list-footprints?view=graph-rest-1.0) | [footprintMap](https://learn.microsoft.com/en-us/graph/api/resources/footprintmap?view=graph-rest-1.0) collection | Get a list of [footprintMap](https://learn.microsoft.com/en-us/graph/api/resources/footprintmap?view=graph-rest-1.0) objects for [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0) footprints and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the **footprintMap** object. Inherited from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0). |
| properties | String | Concatenated key-value pair of all properties of a GeoJSON file for this **footprintMap**. Inherited from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.footprintMap",
  "id": "String (identifier)",
  "properties": "String"
}
```
