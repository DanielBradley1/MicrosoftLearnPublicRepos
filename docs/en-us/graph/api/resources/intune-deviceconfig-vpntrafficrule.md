<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpntrafficrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# vpnTrafficRule resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

VPN Traffic Rule definition.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | Name. |
| protocols | Int32 | Protocols \(0-255\). Valid values 0 to 255 |
| localPortRanges | [numberRange](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-numberrange?view=graph-rest-beta) collection | Local port range can be set only when protocol is either TCP or UDP \(6 or 17\). This collection can contain a maximum of 500 elements. |
| remotePortRanges | [numberRange](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-numberrange?view=graph-rest-beta) collection | Remote port range can be set only when protocol is either TCP or UDP \(6 or 17\). This collection can contain a maximum of 500 elements. |
| localAddressRanges | [iPv4Range](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ipv4range?view=graph-rest-beta) collection | Local address range. This collection can contain a maximum of 500 elements. |
| remoteAddressRanges | [iPv4Range](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ipv4range?view=graph-rest-beta) collection | Remote address range. This collection can contain a maximum of 500 elements. |
| appId | String | App identifier, if this traffic rule is triggered by an app. |
| appType | [vpnTrafficRuleAppType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpntrafficruleapptype?view=graph-rest-beta) | App type, if this traffic rule is triggered by an app. Possible values are: `none`, `desktop`, `universal`. |
| routingPolicyType | [vpnTrafficRuleRoutingPolicyType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpntrafficruleroutingpolicytype?view=graph-rest-beta) | When app triggered, indicates whether to enable split tunneling along this route. Possible values are: `none`, `splitTunnel`, `forceTunnel`. |
| claims | String | Claims associated with this traffic rule. |
| vpnTrafficDirection | [vpnTrafficDirection](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpntrafficdirection?view=graph-rest-beta) | Specify whether the rule applies to inbound traffic or outbound traffic. Possible values are: `outbound`, `inbound`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.vpnTrafficRule",
  "name": "String",
  "protocols": 1024,
  "localPortRanges": [
    {
      "@odata.type": "microsoft.graph.numberRange",
      "lowerNumber": 1024,
      "upperNumber": 1024
    }
  ],
  "remotePortRanges": [
    {
      "@odata.type": "microsoft.graph.numberRange",
      "lowerNumber": 1024,
      "upperNumber": 1024
    }
  ],
  "localAddressRanges": [
    {
      "@odata.type": "microsoft.graph.iPv4Range",
      "lowerAddress": "String",
      "upperAddress": "String"
    }
  ],
  "remoteAddressRanges": [
    {
      "@odata.type": "microsoft.graph.iPv4Range",
      "lowerAddress": "String",
      "upperAddress": "String"
    }
  ],
  "appId": "String",
  "appType": "String",
  "routingPolicyType": "String",
  "claims": "String",
  "vpnTrafficDirection": "String"
}
```
