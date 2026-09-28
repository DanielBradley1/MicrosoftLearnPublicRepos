<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/airprintsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-02-26 -->

# airPrintSettings resource type

Namespace: microsoft.graph

Represents tenant-wide settings to configure the behavior of printers when print jobs are submitted to Universal Print from macOS, which requires AirPrint compatibility.

Note

**AirPrint**, **Mac**, and **macOS** are trademarks of Apple, Inc., registered in the US and other countries/regions.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| incompatiblePrinters | [incompatiblePrinterSettings](#incompatibleprintersettings-values) | Describes whether Universal Print hides printers from macOS when they don't support all capabilities required by the operating system as defined by AirPrint. |

### incompatiblePrinterSettings values

| Member | Description |
| :--- | :--- |
| show | Show printers that aren't compatible with AirPrint. |
| hide | Hide printers that aren't compatible with AirPrint. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON shows a representation of the resource.

```json
{
  "incompatiblePrinters": "String"
}
```
