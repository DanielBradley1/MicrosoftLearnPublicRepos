<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# fixtureMap resource type

Namespace: microsoft.graph

Represents a fixture.geojson file in IMDF format that defines movable or semi-permanent physical assets within a space. These assets support utility, service, or aesthetic functions without affecting structural integrity.

Inherits from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/levelmap-list-fixtures?view=graph-rest-1.0) | [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) collection | Get a list of the [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) objects and their properties. |
| [Update](https://learn.microsoft.com/en-us/graph/api/fixturemap-update?view=graph-rest-1.0) | [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) | Update the properties of an existing [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) object in IMDF format on a specified floor, or create one if it doesn't exist. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/fixturemap-delete?view=graph-rest-1.0) | None | Delete a [fixture](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) on a specified floor. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the **fixtureMap** object. Inherited from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0). |
| placeId | String | Identifier for the [floor](https://learn.microsoft.com/en-us/graph/api/resources/floor?view=graph-rest-1.0) to which this **fixtureMap** belongs. |
| properties | String | Concatenated key-value pair of all properties of a GeoJSON file for this **fixtureMap**. Inherited from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.fixtureMap",
  "id": "String (identifier)",
  "placeId": "String",
  "properties": "String"
}
```
