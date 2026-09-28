<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-26 -->

# printSettings resource type

Namespace: microsoft.graph

Represents tenant-wide settings for the Universal Print service.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| documentConversionEnabled | Boolean | Specifies whether document conversion is enabled for the tenant. If document conversion is enabled, Universal Print service converts documents into a format compatible with the printer \(xps to pdf\) when needed. |
| printerDiscoverySettings | [printerDiscoverySettings](https://learn.microsoft.com/en-us/graph/api/resources/printerdiscoverysettings?view=graph-rest-1.0) | Specifies settings that affect printer discovery when using Universal Print. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "documentConversionEnabled": "Boolean",
  "printerDiscoverySettings": {"@odata.type": "microsoft.graph.printerDiscoverySettings"}
}
```
