<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ndesconnector?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# ndesConnector resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity which represents an OnPrem Ndes connector.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List ndesConnectors](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ndesconnector-list?view=graph-rest-beta) | [ndesConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ndesconnector?view=graph-rest-beta) collection | List properties and relationships of the [ndesConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ndesconnector?view=graph-rest-beta) objects. |
| [Get ndesConnector](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ndesconnector-get?view=graph-rest-beta) | [ndesConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ndesconnector?view=graph-rest-beta) | Read properties and relationships of the [ndesConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ndesconnector?view=graph-rest-beta) object. |
| [Create ndesConnector](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ndesconnector-create?view=graph-rest-beta) | [ndesConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ndesconnector?view=graph-rest-beta) | Create a new [ndesConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ndesconnector?view=graph-rest-beta) object. |
| [Delete ndesConnector](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ndesconnector-delete?view=graph-rest-beta) | None | Deletes a [ndesConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ndesconnector?view=graph-rest-beta). |
| [Update ndesConnector](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-ndesconnector-update?view=graph-rest-beta) | [ndesConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ndesconnector?view=graph-rest-beta) | Update the properties of a [ndesConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ndesconnector?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The key of the NDES Connector. |
| lastConnectionDateTime | DateTimeOffset | Last connection time for the Ndes Connector |
| state | [ndesConnectorState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-ndesconnectorstate?view=graph-rest-beta) | Ndes Connector Status. Possible values are: `none`, `active`, `inactive`. |
| displayName | String | The friendly name of the Ndes Connector. |
| machineName | String | Name of the machine running on-prem certificate connector service. |
| enrolledDateTime | DateTimeOffset | Timestamp when on-prem certificate connector was enrolled in Intune. |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. |
| connectorVersion | String | The build version of the Ndes Connector. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.ndesConnector",
  "id": "String (identifier)",
  "lastConnectionDateTime": "String (timestamp)",
  "state": "String",
  "displayName": "String",
  "machineName": "String",
  "enrolledDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
  "connectorVersion": "String"
}
```
