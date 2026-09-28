<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printconnector?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# printConnector resource type

Namespace: microsoft.graph

Represents a print connector that has been registered by using a Universal Print subscription. The printConnector resource can be used to view connector status and update properties.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/print-list-connectors?view=graph-rest-1.0) | [printConnector](https://learn.microsoft.com/en-us/graph/api/resources/printconnector?view=graph-rest-1.0) | Retrieve a list of print connectors. |
| [Get](https://learn.microsoft.com/en-us/graph/api/printconnector-get?view=graph-rest-1.0) | [printConnector](https://learn.microsoft.com/en-us/graph/api/resources/printconnector?view=graph-rest-1.0) | Read the properties and relationships of the connector object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/printconnector-update?view=graph-rest-1.0) | [printConnector](https://learn.microsoft.com/en-us/graph/api/resources/printconnector?view=graph-rest-1.0) | Update the connector object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/printconnector-delete?view=graph-rest-1.0) | None | Unregister the connector from the Universal Print service. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appVersion | String | The connector's version. |
| displayName | String | The name of the connector. |
| fullyQualifiedDomainName | String | The connector machine's hostname. |
| id | String | Read-only. |
| location | [printerLocation](https://learn.microsoft.com/en-us/graph/api/resources/printerlocation?view=graph-rest-1.0) | The physical and/or organizational location of the connector. |
| operatingSystem | String | The connector machine's operating system version. |
| registeredBy | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-1.0) | The user who registered the connector. |
| registeredDateTime | DateTimeOffset | The DateTimeOffset when the connector was registered. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printConnector",
  "id": "String (identifier)",
  "displayName": "String",
  "fullyQualifiedDomainName": "String",
  "operatingSystem": "String",
  "appVersion": "String",
  "location": {
    "@odata.type": "microsoft.graph.printerLocation"
  },
  "registeredDateTime": "String (timestamp)"
}
```
