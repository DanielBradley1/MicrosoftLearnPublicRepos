<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/levelmap?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# levelMap resource type

Namespace: microsoft.graph

Represents a level.geojson file in IMDF format that defines the physical floor structure within a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0).

Inherits from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/buildingmap-list-levels?view=graph-rest-1.0) | [levelMap](https://learn.microsoft.com/en-us/graph/api/resources/levelmap?view=graph-rest-1.0) collection | Get a list of the [levelMap](https://learn.microsoft.com/en-us/graph/api/resources/levelmap?view=graph-rest-1.0) objects and their properties. |
| [List fixtures](https://learn.microsoft.com/en-us/graph/api/levelmap-list-fixtures?view=graph-rest-1.0) | [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) collection | Get a list of the [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) objects and their properties. |
| [List sections](https://learn.microsoft.com/en-us/graph/api/levelmap-list-sections?view=graph-rest-1.0) | [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) collection | Get a list of the [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) objects and their properties. |
| [List units](https://learn.microsoft.com/en-us/graph/api/levelmap-list-units?view=graph-rest-1.0) | [unitMap](https://learn.microsoft.com/en-us/graph/api/resources/unitmap?view=graph-rest-1.0) collection | Get a list of the [unitMap](https://learn.microsoft.com/en-us/graph/api/resources/unitmap?view=graph-rest-1.0) objects and their properties. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the **levelMap** object. Inherited from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0). |
| placeId | String | Identifier of the [floor](https://learn.microsoft.com/en-us/graph/api/resources/floor?view=graph-rest-1.0) to which this **levelMap** belongs. |
| properties | String | Concatenated key-value pair of all properties of a GeoJSON file for this **levelMap**. Inherited from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| fixtures | [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) collection | Collection of fixtures \(such as furniture or equipment\) on this level. Supports upsert. |
| sections | [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) collection | Collection of sections \(such as zones or partitions\) on this level. Supports upsert. |
| units | [unitMap](https://learn.microsoft.com/en-us/graph/api/resources/unitmap?view=graph-rest-1.0) collection | Collection of units \(such as rooms or offices\) on this level. Supports upsert. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.levelMap",
  "id": "String (identifier)",
  "properties": "String",
  "placeId": "String"
}
```
