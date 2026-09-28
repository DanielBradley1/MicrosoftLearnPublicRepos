<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/geocoordinates?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# GeoCoordinates resource type

Namespace: microsoft.graph

The **GeoCoordinates** resource provides geographic coordinates and elevation of a location based on metadata contained within the file. This object is configured in the **geoCoordinates** property of [signInLocation](https://learn.microsoft.com/en-us/graph/api/resources/signinlocation?view=graph-rest-1.0). If a [**DriveItem**](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) has a non-null **location** facet, the item represents a file with a known location assocaited with it.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "altitude": 1024.13,
  "latitude": 26.13246,
  "longitude": 24.34616
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| altitude | Double | Optional. The altitude \(height\), in feet, above sea level for the item. Read-only. |
| latitude | Double | Optional. The latitude, in decimal, for the item. Read-only. |
| longitude | Double | Optional. The longitude, in decimal, for the item. Read-only. |

## Remarks

For more information about the facets on a DriveItem, see [DriveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
