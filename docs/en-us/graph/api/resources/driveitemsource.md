<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driveitemsource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-03-12 -->

# driveItemSource resource type

Contains metadata about the source application in which the drive item was created.

It's available on the source property of [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0) resources.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| application | driveItemSourceApplication | Enumeration value that indicates the source application where the file was created. |
| externalId | string | The external identifier for the drive item from the source. |

### driveItemSourceApplication values

| Value | Description |
| :--- | :--- |
| teams | The application is Teams. |
| yammer | The application is Yammer. |
| sharePoint | The application is SharePoint. |
| oneDrive | The application is OneDrive. |
| stream | The application is Stream. |
| powerPoint | The application is PowerPoint. |
| office | The application is Office. |
| loki | The application is Loki. |
| loop | The application is Loop. |
| other | The application is a third party application. |
| unknownFutureValue | Marker value for future compatibility. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "application": "string",
  "externalId" : "string"
}
```

## See also

For more information about the facets on a driveItem, see [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
