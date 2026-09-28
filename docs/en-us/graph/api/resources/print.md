<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/print?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# print resource type

Namespace: microsoft.graph

When accompanied by a Universal Print subscription, the Print feature enables management of printers and discovery of [printServiceEndpoints](https://learn.microsoft.com/en-us/graph/api/resources/printserviceendpoint?view=graph-rest-1.0) that can be used to manage printers and print jobs within Universal Print.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List connectors](https://learn.microsoft.com/en-us/graph/api/print-list-connectors?view=graph-rest-1.0) | [printConnector](https://learn.microsoft.com/en-us/graph/api/resources/printconnector?view=graph-rest-1.0) collection | Get a list of print connectors. |
| [List printers](https://learn.microsoft.com/en-us/graph/api/print-list-printers?view=graph-rest-1.0) | [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) collection | Get a list of printers. |
| [List shares](https://learn.microsoft.com/en-us/graph/api/print-list-shares?view=graph-rest-1.0) | [printerShare](https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0) collection | Get a list of printer shares. |
| [List services](https://learn.microsoft.com/en-us/graph/api/print-list-services?view=graph-rest-1.0) | [printService](https://learn.microsoft.com/en-us/graph/api/resources/printservice?view=graph-rest-1.0) collection | Get a list of services. |
| [Create printerShare](https://learn.microsoft.com/en-us/graph/api/print-post-shares?view=graph-rest-1.0) | [printerShare](https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0) | Create a new printer share by posting to the **shares** collection. |
| [Create printer](https://learn.microsoft.com/en-us/graph/api/printer-create?view=graph-rest-1.0) | [printerCreateOperation](https://learn.microsoft.com/en-us/graph/api/resources/printercreateoperation?view=graph-rest-1.0) | Create \(register\) a new printer with Universal Print. |
| [Update settings](https://learn.microsoft.com/en-us/graph/api/print-update-settings?view=graph-rest-1.0) | [printSettings](https://learn.microsoft.com/en-us/graph/api/resources/printsettings?view=graph-rest-1.0) | Updates tenant-wide settings for the Universal Print service. |
| [List taskDefinitions](https://learn.microsoft.com/en-us/graph/api/print-list-taskdefinitions?view=graph-rest-1.0) | [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) collection | Get a tenant-wide list of printTaskDefinitions created within Universal Print. |
| [Create taskDefinition](https://learn.microsoft.com/en-us/graph/api/print-post-taskdefinitions?view=graph-rest-1.0) | [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) | Create a new printTaskDefinition. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| settings | [printSettings](https://learn.microsoft.com/en-us/graph/api/resources/printsettings?view=graph-rest-1.0) | Tenant-wide settings for the Universal Print service. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| connectors | [printConnector](https://learn.microsoft.com/en-us/graph/api/resources/printconnector?view=graph-rest-1.0) collection | The list of available print connectors. |
| operations | [printOperation](https://learn.microsoft.com/en-us/graph/api/resources/printoperation?view=graph-rest-1.0) collection | The list of print long running operations. |
| printers | [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0) collection | The list of printers registered in the tenant. |
| services | [printService](https://learn.microsoft.com/en-us/graph/api/resources/printservice?view=graph-rest-1.0) collection | The list of available Universal Print service endpoints. |
| services | [printService](https://learn.microsoft.com/en-us/graph/api/resources/printservice?view=graph-rest-1.0) collection | The list of print service instances for various components of the printing infrastructure. |
| shares | [printerShare](https://learn.microsoft.com/en-us/graph/api/resources/printershare?view=graph-rest-1.0) collection | The list of printer shares registered in the tenant. |
| taskDefinitions | [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) collection | List of abstract definition for a task that can be triggered when various events occur within Universal Print. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.print",
  "settings": {
    "@odata.type": "microsoft.graph.printSettings"
  }
}
```
