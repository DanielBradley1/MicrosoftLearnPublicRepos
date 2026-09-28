<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/searchresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# searchResult resource type

Namespace: microsoft.graph

The **searchResult** resource indicates than an item is the response to a search query.

## JSON representation

```json
{
  "onClickTelemetryUrl": "url"
}
```

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| onClickTelemetryUrl | String | A callback URL that can be used to record telemetry information. The application should issue a GET on this URL if the user interacts with this item to improve the quality of results. |

## Remarks

For more information about the facets on a DriveItem, see [driveItem](https://learn.microsoft.com/en-us/graph/api/resources/driveitem?view=graph-rest-1.0).
