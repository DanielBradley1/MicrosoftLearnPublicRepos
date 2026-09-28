<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-ipaddress?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# ipAddress resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents an IP address, which is \(or has been\) addressable over the internet. This resource acts as a grouping mechanism for related details about the hostname or IP address, such as the reputation, any related trackers or cookies, and so on.

You cannot retrieve this type directly. To access it, retrieve the [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) resource.

Inherits from [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List components](https://learn.microsoft.com/en-us/graph/api/security-host-list-components?view=graph-rest-1.0) | [microsoft.graph.security.hostComponent](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcomponent?view=graph-rest-1.0) collection | Get a list of **hostComponent** resources. |
| [List cookies](https://learn.microsoft.com/en-us/graph/api/security-host-list-cookies?view=graph-rest-1.0) | [microsoft.graph.security.hostCookie](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcookie?view=graph-rest-1.0) collection | Get a list of **hostCookie** resources. |
| [List passiveDns](https://learn.microsoft.com/en-us/graph/api/security-host-list-passivedns?view=graph-rest-1.0) | [microsoft.graph.security.passiveDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0) collection | Get a list of **passiveDnsRecord** resources. |
| [List passiveDnsReverse](https://learn.microsoft.com/en-us/graph/api/security-host-list-passivednsreverse?view=graph-rest-1.0) | [microsoft.graph.security.passiveDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0) collection | Get a list of **passiveDnsRecord** resources. |
| [Get reputation](https://learn.microsoft.com/en-us/graph/api/security-host-get-reputation?view=graph-rest-1.0) | [microsoft.graph.security.hostReputation](https://learn.microsoft.com/en-us/graph/api/resources/security-hostreputation?view=graph-rest-1.0) | Get a list of **hostReputation** resources. |
| [List trackers](https://learn.microsoft.com/en-us/graph/api/security-host-list-trackers?view=graph-rest-1.0) | [microsoft.graph.security.hostTracker](https://learn.microsoft.com/en-us/graph/api/resources/security-hosttracker?view=graph-rest-1.0) collection | Get a list of **hostTracker** resources. |
| [Get whoisRecord](https://learn.microsoft.com/en-us/graph/api/security-whoisrecord-get?view=graph-rest-1.0) | [microsoft.graph.security.whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) | Get the specified [whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) resource. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| autonomousSystem | [microsoft.graph.security.autonomousSystem](https://learn.microsoft.com/en-us/graph/api/resources/security-autonomoussystem?view=graph-rest-1.0) | The details about the autonomous system to which this IP address belongs. |
| countryOrRegion | String | The country/region for this IP address. |
| firstSeenDateTime | DateTimeOffset | The first date and time when this [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) was observed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0). |
| hostingProvider | String | The hosting company listed for this [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0). |
| id | String | The IP Address for this [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0). Read-only. Inherited from [microsoft.graph.security.artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0). |
| lastSeenDateTime | DateTimeOffset | The most recent date and time when this [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) was observed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Inherited from [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0). |
| netblock | String | The block of IP addresses this IP address belongs to. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| components | [microsoft.graph.security.hostComponent](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcomponent?view=graph-rest-1.0) collection | The **hostComponents** that are associated with this host. Inherited from [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0). |
| cookies | [microsoft.graph.security.hostCookie](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcookie?view=graph-rest-1.0) collection | The **hostCookies** that are associated with this host. Inherited from [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0). |
| passiveDns | [microsoft.graph.security.passiveDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0) collection | Passive DNS retrieval about this host. Inherited from [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0). |
| passiveDnsReverse | [microsoft.graph.security.passiveDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0) collection | Reverse passive DNS retrieval about this host. Inherited from [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0). |
| reputation | [microsoft.graph.security.hostReputation](https://learn.microsoft.com/en-us/graph/api/resources/security-hostreputation?view=graph-rest-1.0) | Represents a calculated reputation of this host. Inherited from [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0). |
| trackers | [microsoft.graph.security.hostTracker](https://learn.microsoft.com/en-us/graph/api/resources/security-hosttracker?view=graph-rest-1.0) collection | The **hostTrackers** that are associated with this host. Inherited from [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0). |
| whois | [microsoft.graph.security.whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) | The most recent **whoisRecord** for this host. Inherited from [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.ipAddress",
  "autonomousSystem": {
    "@odata.type": "microsoft.graph.security.autonomousSystem"
  },
  "countryOrRegion": "String",
  "firstSeenDateTime": "String (timestamp)",
  "hostingProvider": "String",
  "id": "String (identifier)",
  "lastSeenDateTime": "String (timestamp)",
  "netblock": "String"
}
```
