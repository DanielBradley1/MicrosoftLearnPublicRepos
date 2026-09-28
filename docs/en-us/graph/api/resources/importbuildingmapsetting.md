<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/importbuildingmapsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# importBuildingMapSetting resource type

Namespace: microsoft.graph

Represents the supported import setting for the [ingestMapFile](https://learn.microsoft.com/en-us/graph/api/building-ingestmapfile?view=graph-rest-1.0) API.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isDryRun | Boolean | `True` indicates that the service processes the map but doesn't save anything. `False` indicates that the service processes and stores the map. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.importBuildingMapSetting",
  "isDryRun": "Boolean"
}
```
