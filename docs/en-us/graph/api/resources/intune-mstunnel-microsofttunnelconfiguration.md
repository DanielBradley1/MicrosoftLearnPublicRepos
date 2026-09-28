<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# microsoftTunnelConfiguration resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that represents a collection of Microsoft Tunnel settings

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List microsoftTunnelConfigurations](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelconfiguration-list?view=graph-rest-beta) | [microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelconfiguration?view=graph-rest-beta) collection | List properties and relationships of the [microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelconfiguration?view=graph-rest-beta) objects. |
| [Get microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelconfiguration-get?view=graph-rest-beta) | [microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelconfiguration?view=graph-rest-beta) | Read properties and relationships of the [microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelconfiguration?view=graph-rest-beta) object. |
| [Create microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelconfiguration-create?view=graph-rest-beta) | [microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelconfiguration?view=graph-rest-beta) | Create a new [microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelconfiguration?view=graph-rest-beta) object. |
| [Delete microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelconfiguration-delete?view=graph-rest-beta) | None | Deletes a [microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelconfiguration?view=graph-rest-beta). |
| [Update microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/intune-mstunnel-microsofttunnelconfiguration-update?view=graph-rest-beta) | [microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelconfiguration?view=graph-rest-beta) | Update the properties of a [microsoftTunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-microsofttunnelconfiguration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the configuration id. Supports: $delete, $update. $Insert, $skip, $top is not supported. Read-only. |
| displayName | String | The display name for the server configuration. This property is required when a server is created. |
| description | String | The configuration's description \(optional\) |
| network | String | The IPv4 subnet that will be used to allocate virtual address for the clients |
| ipv6Network | String | The IPv6 subnet that will be used to allocate virtual address for the clients |
| dnsServers | String collection | The DNS servers that will be used by the clients |
| defaultDomainSuffix | String | The Default Domain appendix that will be used by the clients |
| routesInclude | String collection | The routes that will be routed by the server. This property is going to be deprecated with the option of using the new property, 'RouteIncludes'. |
| routesExclude | String collection | Subsets of the routes that will not be routed by the server. This property is going to be deprecated with the option of using the new property, 'RouteExcludes'. |
| routeIncludes | String collection | The routes that will be routed by the server |
| routeExcludes | String collection | Subsets of the routes that will not be routed by the server |
| splitDNS | String collection | The domains that will be resolved using the provided dns servers |
| listenPort | Int32 | The port that both TCP and UPD will listen over on the server |
| advancedSettings | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-mstunnel-keyvaluepair?view=graph-rest-beta) collection | Additional settings that may be applied to the server |
| lastUpdateDateTime | DateTimeOffset | When the configuration was last updated |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance |
| disableUdpConnections | Boolean | When DisableUdpConnections is set, the clients and VPN server will not use DTLS connections to transfer data. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.microsoftTunnelConfiguration",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "network": "String",
  "ipv6Network": "String",
  "dnsServers": [
    "String"
  ],
  "defaultDomainSuffix": "String",
  "routesInclude": [
    "String"
  ],
  "routesExclude": [
    "String"
  ],
  "routeIncludes": [
    "String"
  ],
  "routeExcludes": [
    "String"
  ],
  "splitDNS": [
    "String"
  ],
  "listenPort": 1024,
  "advancedSettings": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "String",
      "value": "String"
    }
  ],
  "lastUpdateDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
  "disableUdpConnections": true
}
```
