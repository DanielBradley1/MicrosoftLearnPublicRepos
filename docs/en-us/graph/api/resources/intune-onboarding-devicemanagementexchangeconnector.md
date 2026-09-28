<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeconnector?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# deviceManagementExchangeConnector resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity which represents a connection to an Exchange environment.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementExchangeConnectors](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementexchangeconnector-list?view=graph-rest-1.0) | [deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeconnector?view=graph-rest-1.0) collection | List properties and relationships of the [deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeconnector?view=graph-rest-1.0) objects. |
| [Get deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementexchangeconnector-get?view=graph-rest-1.0) | [deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeconnector?view=graph-rest-1.0) | Read properties and relationships of the [deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeconnector?view=graph-rest-1.0) object. |
| [Create deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementexchangeconnector-create?view=graph-rest-1.0) | [deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeconnector?view=graph-rest-1.0) | Create a new [deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeconnector?view=graph-rest-1.0) object. |
| [Delete deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementexchangeconnector-delete?view=graph-rest-1.0) | None | Deletes a [deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeconnector?view=graph-rest-1.0). |
| [Update deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementexchangeconnector-update?view=graph-rest-1.0) | [deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeconnector?view=graph-rest-1.0) | Update the properties of a [deviceManagementExchangeConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeconnector?view=graph-rest-1.0) object. |
| [sync action](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-devicemanagementexchangeconnector-sync?view=graph-rest-1.0) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String |  |
| lastSyncDateTime | DateTimeOffset | Last sync time for the Exchange Connector |
| status | [deviceManagementExchangeConnectorStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeconnectorstatus?view=graph-rest-1.0) | Exchange Connector Status. The possible values are: `none`, `connectionPending`, `connected`, `disconnected`, `unknownFutureValue`. |
| primarySmtpAddress | String | Email address used to configure the Service To Service Exchange Connector. |
| serverName | String | The name of the Exchange server. |
| connectorServerName | String | The name of the server hosting the Exchange Connector. |
| exchangeConnectorType | [deviceManagementExchangeConnectorType](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-devicemanagementexchangeconnectortype?view=graph-rest-1.0) | The type of Exchange Connector Configured. The possible values are: `onPremises`, `hosted`, `serviceToService`, `dedicated`, `unknownFutureValue`. |
| version | String | The version of the ExchangeConnectorAgent |
| exchangeAlias | String | An alias assigned to the Exchange server |
| exchangeOrganization | String | Exchange Organization to the Exchange server |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementExchangeConnector",
  "id": "String (identifier)",
  "lastSyncDateTime": "String (timestamp)",
  "status": "String",
  "primarySmtpAddress": "String",
  "serverName": "String",
  "connectorServerName": "String",
  "exchangeConnectorType": "String",
  "version": "String",
  "exchangeAlias": "String",
  "exchangeOrganization": "String"
}
```
