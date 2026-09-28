<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# sectionMap resource type

Namespace: microsoft.graph

Represents a section.geojson file in IMDF format that defines sections \(such as zones or partitions\) on the floor of a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0).

Inherits from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/levelmap-list-sections?view=graph-rest-1.0) | [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) collection | Get a list of the [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) objects and their properties. |
| [Update](https://learn.microsoft.com/en-us/graph/api/sectionmap-update?view=graph-rest-1.0) | [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) | Update the properties of an existing [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) object in IMDF format on a specified floor, or create one if it doesn't exist. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/sectionmap-delete?view=graph-rest-1.0) | None | Delete a [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) object on a specified floor. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the **sectionMap** object. Inherited from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0). |
| placeId | String | Identifier of the [section](https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0) to which this **sectionMap** belongs. |
| properties | String | Concatenated key-value pair of all properties of a GeoJSON file for this **sectionMap**. Inherited from [baseMapFeature](https://learn.microsoft.com/en-us/graph/api/resources/basemapfeature?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sectionMap",
  "id": "String (identifier)",
  "placeId": "String",
  "properties": "String"
}
```
