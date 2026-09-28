<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-03 -->

# printer resource type

Namespace: microsoft.graph

Represents a printer device that is registered with the Universal Print service. Printer resources can be used to manage print jobs, printer settings, printer metadata, and registration status.

This resource supports:

- [Subscribing to change notifications](https://learn.microsoft.com/en-us/graph/universal-print-webhook-notifications).

Inherits from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/printer-create?view=graph-rest-1.0) | [printerCreateOperation](https://learn.microsoft.com/en-us/graph/api/resources/printercreateoperation?view=graph-rest-1.0) | Create \(register\) a new printer with Universal Print. |
| [Get](https://learn.microsoft.com/en-us/graph/api/printer-get?view=graph-rest-1.0) | [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) | Read the properties and relationships of the printer object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/printer-update?view=graph-rest-1.0) | [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) | Update the printer object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/printer-delete?view=graph-rest-1.0) | None | Unregister the physical printer from the Universal Print service. |
| [Restore factory defaults](https://learn.microsoft.com/en-us/graph/api/printer-restorefactorydefaults?view=graph-rest-1.0) | None | Restore a printer's default settings to the values specified by the manufacturer. |
| [List print jobs](https://learn.microsoft.com/en-us/graph/api/printer-list-jobs?view=graph-rest-1.0) | [printJob](https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0) collection | Get a list of print jobs that the printer queues for processing. |
| [Create print job](https://learn.microsoft.com/en-us/graph/api/printer-post-jobs?view=graph-rest-1.0) | [printJob](https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0) | Create a new print job for the printer. To start printing the job, use [start](https://learn.microsoft.com/en-us/graph/api/printjob-start?view=graph-rest-1.0). |
| [List connectors](https://learn.microsoft.com/en-us/graph/api/printer-list-connectors?view=graph-rest-1.0) | [printConnector](https://learn.microsoft.com/en-us/graph/api/resources/printconnector?view=graph-rest-1.0) collection | Get a list of connectors that this printer is associated with. |
| [List printerShares](https://learn.microsoft.com/en-us/graph/api/printer-list-shares?view=graph-rest-1.0) | [printerShare](https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0) collection | Get a list of printerShares that this printer is associated with. Currently, only one printerShare can be associated with a printer. |
| [List task triggers](https://learn.microsoft.com/en-us/graph/api/printer-list-tasktriggers?view=graph-rest-1.0) | None | List [printTaskTriggers](https://learn.microsoft.com/en-us/graph/api/resources/printtasktrigger?view=graph-rest-1.0) associated with this printer. |
| [Create task trigger](https://learn.microsoft.com/en-us/graph/api/printer-post-tasktriggers?view=graph-rest-1.0) | [printTaskTrigger](https://learn.microsoft.com/en-us/graph/api/resources/printtasktrigger?view=graph-rest-1.0) | Create a [printTaskTrigger](https://learn.microsoft.com/en-us/graph/api/resources/printtasktrigger?view=graph-rest-1.0) that runs when print events occur. |
| [Delete task trigger](https://learn.microsoft.com/en-us/graph/api/printer-delete-tasktrigger?view=graph-rest-1.0) | None | Delete a [printTaskTrigger](https://learn.microsoft.com/en-us/graph/api/resources/printtasktrigger?view=graph-rest-1.0) that is associated with the printer. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| capabilities | [printerCapabilities](https://learn.microsoft.com/en-us/graph/api/resources/printercapabilities?view=graph-rest-1.0) | The capabilities of the printer associated with this printer share. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). |
| defaults | [printerDefaults](https://learn.microsoft.com/en-us/graph/api/resources/printerdefaults?view=graph-rest-1.0) | The printer's default print settings. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). |
| displayName | String | The name of the printer. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). |
| hasPhysicalDevice | Boolean | True if the printer has a physical device for printing. Read-only. |
| id | String | The document's identifier. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). Read-only. |
| isAcceptingJobs | Boolean | True if the printer is currently accepting new print jobs. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). |
| isShared | Boolean | True if the printer is shared; false otherwise. Read-only. |
| lastSeenDateTime | DateTimeOffset | The most recent dateTimeOffset when a printer interacted with Universal Print. Read-only. |
| location | [printerLocation](https://learn.microsoft.com/en-us/graph/api/resources/printerlocation?view=graph-rest-1.0) | The physical and/or organizational location of the printer. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). |
| manufacturer | String | The manufacturer reported by the printer. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). |
| model | String | The model name reported by the printer. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). |
| registeredDateTime | DateTimeOffset | The DateTimeOffset when the printer was registered. Read-only. |
| status | [printerStatus](https://learn.microsoft.com/en-us/graph/api/resources/printerstatus?view=graph-rest-1.0) | The processing status of the printer, including any errors. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| connectors | [printConnector](https://learn.microsoft.com/en-us/graph/api/resources/printconnector?view=graph-rest-1.0) | The connectors that are associated with the printer. |
| jobs | [printJob](https://learn.microsoft.com/en-us/graph/api/resources/printjob?view=graph-rest-1.0) collection | The list of jobs that the printer queues for printing. Inherited from [printerBase](https://learn.microsoft.com/en-us/graph/api/resources/printerbase?view=graph-rest-1.0). |
| shares | [printerShare](https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0) collection | The list of printerShares that are associated with the printer. Currently, only one printerShare can be associated with the printer. Read-only. Nullable. |
| taskTriggers | [printTaskTrigger](https://learn.microsoft.com/en-us/graph/api/resources/printtasktrigger?view=graph-rest-1.0) collection | A list of task triggers that are associated with the printer. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printer",
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
  },
  "registeredDateTime": "String (timestamp)",
  "isShared": "Boolean",
  "hasPhysicalDevice": "Boolean",
  "lastSeenDateTime": "String (timestamp)"
}
```
