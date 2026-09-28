<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnondemandrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# vpnOnDemandRule resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

VPN On-Demand Rule definition.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ssids | String collection | Network Service Set Identifiers \(SSIDs\). |
| dnsSearchDomains | String collection | DNS Search Domains. |
| probeUrl | String | A URL to probe. If this URL is successfully fetched \(returning a 200 HTTP status code\) without redirection, this rule matches. |
| action | [vpnOnDemandRuleConnectionAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnondemandruleconnectionaction?view=graph-rest-beta) | Action. Possible values are: `connect`, `evaluateConnection`, `ignore`, `disconnect`. |
| domainAction | [vpnOnDemandRuleConnectionDomainAction](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnondemandruleconnectiondomainaction?view=graph-rest-beta) | Domain Action \(Only applicable when Action is evaluate connection\). Possible values are: `connectIfNeeded`, `neverConnect`. |
| domains | String collection | Domains \(Only applicable when Action is evaluate connection\). |
| probeRequiredUrl | String | Probe Required Url \(Only applicable when Action is evaluate connection and DomainAction is connect if needed\). |
| interfaceTypeMatch | [vpnOnDemandRuleInterfaceTypeMatch](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnondemandruleinterfacetypematch?view=graph-rest-beta) | Network interface to trigger VPN. Possible values are: `notConfigured`, `ethernet`, `wiFi`, `cellular`. |
| dnsServerAddressMatch | String collection | DNS Search Server Address. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.vpnOnDemandRule",
  "ssids": [
    "String"
  ],
  "dnsSearchDomains": [
    "String"
  ],
  "probeUrl": "String",
  "action": "String",
  "domainAction": "String",
  "domains": [
    "String"
  ],
  "probeRequiredUrl": "String",
  "interfaceTypeMatch": "String",
  "dnsServerAddressMatch": [
    "String"
  ]
}
```
