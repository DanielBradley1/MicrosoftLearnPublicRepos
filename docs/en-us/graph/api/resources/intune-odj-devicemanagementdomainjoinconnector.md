<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-odj-devicemanagementdomainjoinconnector?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# deviceManagementDomainJoinConnector resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

A Domain Join Connector is a connector that is responsible to allocate \(and delete\) machine account blobs

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementDomainJoinConnectors](https://learn.microsoft.com/en-us/graph/api/intune-odj-devicemanagementdomainjoinconnector-list?view=graph-rest-beta) | [deviceManagementDomainJoinConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-odj-devicemanagementdomainjoinconnector?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementDomainJoinConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-odj-devicemanagementdomainjoinconnector?view=graph-rest-beta) objects. |
| [Get deviceManagementDomainJoinConnector](https://learn.microsoft.com/en-us/graph/api/intune-odj-devicemanagementdomainjoinconnector-get?view=graph-rest-beta) | [deviceManagementDomainJoinConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-odj-devicemanagementdomainjoinconnector?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementDomainJoinConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-odj-devicemanagementdomainjoinconnector?view=graph-rest-beta) object. |
| [Create deviceManagementDomainJoinConnector](https://learn.microsoft.com/en-us/graph/api/intune-odj-devicemanagementdomainjoinconnector-create?view=graph-rest-beta) | [deviceManagementDomainJoinConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-odj-devicemanagementdomainjoinconnector?view=graph-rest-beta) | Create a new [deviceManagementDomainJoinConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-odj-devicemanagementdomainjoinconnector?view=graph-rest-beta) object. |
| [Delete deviceManagementDomainJoinConnector](https://learn.microsoft.com/en-us/graph/api/intune-odj-devicemanagementdomainjoinconnector-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementDomainJoinConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-odj-devicemanagementdomainjoinconnector?view=graph-rest-beta). |
| [Update deviceManagementDomainJoinConnector](https://learn.microsoft.com/en-us/graph/api/intune-odj-devicemanagementdomainjoinconnector-update?view=graph-rest-beta) | [deviceManagementDomainJoinConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-odj-devicemanagementdomainjoinconnector?view=graph-rest-beta) | Update the properties of a [deviceManagementDomainJoinConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-odj-devicemanagementdomainjoinconnector?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier to represent a connector. |
| displayName | String | The connector display name. |
| lastConnectionDateTime | DateTimeOffset | Last time connector contacted Intune. |
| state | [deviceManagementDomainJoinConnectorState](https://learn.microsoft.com/en-us/graph/api/resources/intune-odj-devicemanagementdomainjoinconnectorstate?view=graph-rest-beta) | The connector state. Possible values are: `active`, `error`, `inactive`. |
| version | String | The version of the connector. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementDomainJoinConnector",
  "id": "String (identifier)",
  "displayName": "String",
  "lastConnectionDateTime": "String (timestamp)",
  "state": "String",
  "version": "String"
}
```
