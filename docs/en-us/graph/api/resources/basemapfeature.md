<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# baseMapFeature resource type

Namespace: microsoft.graph

An abstract type that represents different map types within a tenant.

Base type of [buildingMap](https://learn.microsoft.com/en-us/graph/api/resources/buildingmap?view=graph-rest-1.0), [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0), [footprintMap](https://learn.microsoft.com/en-us/graph/api/resources/footprintmap?view=graph-rest-1.0), [levelMap](https://learn.microsoft.com/en-us/graph/api/resources/levelmap?view=graph-rest-1.0), [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0), and [unitMap](https://learn.microsoft.com/en-us/graph/api/resources/unitmap?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the **baseMapFeature** object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| properties | String | Concatenated key-value pair of all properties of a GeoJSON file for this **baseMapFeature**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.baseMapFeature",
  "id": "String (identifier)",
  "properties": "String"
}
```
