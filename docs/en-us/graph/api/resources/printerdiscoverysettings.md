<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printerdiscoverysettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-26 -->

# printerDiscoverySettings resource type

Namespace: microsoft.graph

Represents tenant-wide printer discovery settings for the Universal Print service.

Note

**AirPrint**, **Mac**, and **macOS** are trademarks of Apple, Inc., registered in the US and other countries/regions.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| airPrint | [airPrintSettings](https://learn.microsoft.com/en-us/graph/api/resources/airprintsettings?view=graph-rest-1.0) | Represents tenant-wide settings to configure the behavior of printers when print jobs are submitted to Universal Print from macOS, which requires AirPrint compatibility. |

## Relationships

None.

## JSON representation

The following JSON shows a representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.printerDiscoverySettings",
  "airPrint": {"@odata.type": "microsoft.graph.airPrintSettings"}
}
```
