<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-03 -->

# printerBase resource type

Namespace: microsoft.graph

Represents the base type for the [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) and [printerShare](https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0) entity types. Inherits from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capabilities | [printerCapabilities](https://learn.microsoft.com/en-us/graph/api/resources/printercapabilities?view=graph-rest-1.0) | The capabilities of the printer/printerShare. |
| defaults | [printerDefaults](https://learn.microsoft.com/en-us/graph/api/resources/printerdefaults?view=graph-rest-1.0) | The default print settings of printer/printerShare. |
| displayName | String | The name of the printer/printerShare. |
| id | String | The identifier. |
| isAcceptingJobs | Boolean | Specifies whether the printer/printerShare is currently accepting new print jobs. |
| location | [printerLocation](https://learn.microsoft.com/en-us/graph/api/resources/printerlocation?view=graph-rest-1.0) | The physical and/or organizational location of the printer/printerShare. |
| manufacturer | String | The manufacturer of the printer/printerShare. |
| model | String | The model name of the printer/printerShare. |
| status | [printerStatus](https://learn.microsoft.com/en-us/graph/api/resources/printerstatus?view=graph-rest-1.0) | The processing status of the printer/printerShare, including any errors. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| jobs | [printJob](https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0) collection | The list of jobs that are queued for printing by the printer/printerShare. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printerBase",
  "id": "String (identifier)",
  "displayName": "String",
  "manufacturer": "String",
  "model": "String",
  "isAcceptingJobs": "Boolean",
  "defaults": {
    "@odata.type": "microsoft.graph.printerDefaults"
  },
  "location": {
    "@odata.type": "microsoft.graph.printerLocation"
  },
  "capabilities": {
    "@odata.type": "microsoft.graph.printerCapabilities"
  },
  "status": {
    "@odata.type": "microsoft.graph.printerStatus"
  }
}
```
