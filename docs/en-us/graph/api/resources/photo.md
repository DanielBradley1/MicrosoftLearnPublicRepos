<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/photo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2023-01-06 -->

# photo resource type

Namespace: microsoft.graph

The **photo** resource provides photo and camera properties, for example, EXIF metadata, on a [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).

## JSON representation

```json
{
  "cameraMake": "string",
  "cameraModel": "string",
  "exposureDenominator": 1000.0,
  "exposureNumerator": 1.0,
  "fNumber": 1.8,
  "focalLength": 22.5,
  "iso": 100,
  "orientation": 3,
  "takenDateTime": "String (timestamp)"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| **cameraMake** | String | Camera manufacturer. Read-only. |
| **cameraModel** | String | Camera model. Read-only. |
| **exposureDenominator** | Double | The denominator for the exposure time fraction from the camera. Read-only. |
| **exposureNumerator** | Double | The numerator for the exposure time fraction from the camera. Read-only. |
| **fNumber** | Double | The F-stop value from the camera. Read-only. |
| **focalLength** | Double | The focal length from the camera. Read-only. |
| **iso** | Int32 | The ISO value from the camera. Read-only. |
| **orientation** | Int16 | The orientation value from the camera. Writable on OneDrive Personal. |
| **takenDateTime** | DateTimeOffset | Represents the date and time the photo was taken. Read-only. |

## Remarks

OneDrive for Business and SharePoint only return the **takenDateTime** property.

For more information about the facets on a DriveItem, see [DriveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
