<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-airprintdestination?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# airPrintDestination resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an AirPrint destination.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ipAddress | String | The IP Address of the AirPrint destination. |
| resourcePath | String | The Resource Path associated with the printer. This corresponds to the rp parameter of the \_ipps.tcp Bonjour record. For example: printers/Canon\_MG5300\_series, printers/Xerox\_Phaser\_7600, ipp/print, Epson\_IPP\_Printer. |
| port | Int32 | The listening port of the AirPrint destination. If this key is not specified AirPrint will use the default port. Available in iOS 11.0 and later. |
| forceTls | Boolean | If true AirPrint connections are secured by Transport Layer Security \(TLS\). Default is false. Available in iOS 11.0 and later. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.airPrintDestination",
  "ipAddress": "String",
  "resourcePath": "String",
  "port": 1024,
  "forceTls": true
}
```
