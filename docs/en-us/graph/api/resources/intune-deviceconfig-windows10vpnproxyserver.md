<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows10vpnproxyserver?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windows10VpnProxyServer resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

VPN Proxy Server.

Inherits from [vpnProxyServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnproxyserver?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| automaticConfigurationScriptUrl | String | Proxy's automatic configuration script url. Inherited from [vpnProxyServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnproxyserver?view=graph-rest-beta) |
| address | String | Address. Inherited from [vpnProxyServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnproxyserver?view=graph-rest-beta) |
| port | Int32 | Port. Valid values 0 to 65535 Inherited from [vpnProxyServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnproxyserver?view=graph-rest-beta) |
| bypassProxyServerForLocalAddress | Boolean | Bypass proxy server for local address. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windows10VpnProxyServer",
  "automaticConfigurationScriptUrl": "String",
  "address": "String",
  "port": 1024,
  "bypassProxyServerForLocalAddress": true
}
```
