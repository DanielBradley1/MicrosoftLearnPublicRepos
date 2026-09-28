<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpndnsrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# vpnDnsRule resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

VPN DNS Rule definition.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name. |
| servers | String collection | Servers. |
| proxyServerUri | String | Proxy Server Uri. |
| autoTrigger | Boolean | Automatically connect to the VPN when the device connects to this domain: Default False. |
| persistent | Boolean | Keep this rule active even when the VPN is not connected: Default False |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.vpnDnsRule",
  "name": "String",
  "servers": [
    "String"
  ],
  "proxyServerUri": "String",
  "autoTrigger": true,
  "persistent": true
}
```
