<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# host resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents a [hostname](https://learn.microsoft.com/en-us/graph/api/resources/security-hostname?view=graph-rest-1.0) or [IP address](https://learn.microsoft.com/en-us/graph/api/resources/security-ipaddress?view=graph-rest-1.0) that is currently or was previously available on the internet and Microsoft Defender Threat Intelligence has detected.

This is an abstract type. Implementations of this type include:

- [hostname](https://learn.microsoft.com/en-us/graph/api/resources/security-hostname?view=graph-rest-1.0)
- [ipAddress](https://learn.microsoft.com/en-us/graph/api/resources/security-ipaddress?view=graph-rest-1.0)

Inherits from [artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get host](https://learn.microsoft.com/en-us/graph/api/security-host-get?view=graph-rest-1.0) | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) | Read the properties and relationships of a [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) object. |
| [Get whoisRecord](https://learn.microsoft.com/en-us/graph/api/security-whoisrecord-get?view=graph-rest-1.0) | [microsoft.graph.security.whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) | Get the specified [whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) resource. |
| [List childHostPairs for a host as parent](https://learn.microsoft.com/en-us/graph/api/security-host-list-childhostpairs?view=graph-rest-1.0) | [microsoft.graph.security.hostPair](https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0) collection | Get a list of **hostPair** resources. |
| [List hostPairs for a host](https://learn.microsoft.com/en-us/graph/api/security-host-list-hostpairs?view=graph-rest-1.0) | [microsoft.graph.security.hostPair](https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0) collection | Get a list of **hostPair** resources. |
| [List components](https://learn.microsoft.com/en-us/graph/api/security-host-list-components?view=graph-rest-1.0) | [microsoft.graph.security.hostComponent](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcomponent?view=graph-rest-1.0) collection | Get a list of **hostComponent** resources. |
| [List cookies](https://learn.microsoft.com/en-us/graph/api/security-host-list-cookies?view=graph-rest-1.0) | [microsoft.graph.security.hostCookie](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcookie?view=graph-rest-1.0) collection | Get a list of **hostCookie** resources. |
| [List parentHostPairs for a host as child](https://learn.microsoft.com/en-us/graph/api/security-host-list-parenthostpairs?view=graph-rest-1.0) | [microsoft.graph.security.hostPair](https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0) collection | Get a list of **hostPairs** resources. |
| [List passiveDns](https://learn.microsoft.com/en-us/graph/api/security-host-list-passivedns?view=graph-rest-1.0) | [microsoft.graph.security.passivednsrecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0) collection | Get a list of **passiveDnsRecord** resources. |
| [List passiveDnsReverse](https://learn.microsoft.com/en-us/graph/api/security-host-list-passivednsreverse?view=graph-rest-1.0) | [microsoft.graph.security.passivednsrecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0) collection | Get a list of **passiveDnsRecord** resources from a reverse passive DNS retrieval. |
| [List ports](https://learn.microsoft.com/en-us/graph/api/security-host-list-ports?view=graph-rest-1.0) | [microsoft.graph.security.hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0) collection | Get a list of **hostPort** resources. |
| [Get reputation](https://learn.microsoft.com/en-us/graph/api/security-host-get-reputation?view=graph-rest-1.0) | [microsoft.graph.security.hostReputation](https://learn.microsoft.com/en-us/graph/api/resources/security-hostreputation?view=graph-rest-1.0) | Get the properties and relationships of a **hostReputation** object. |
| [List subdomains](https://learn.microsoft.com/en-us/graph/api/security-host-list-subdomains?view=graph-rest-1.0) | [microsoft.graph.security.subdomain](https://learn.microsoft.com/en-us/graph/api/resources/security-subdomain?view=graph-rest-1.0) collection | Get a list of **subdomain** resources. |
| [List trackers](https://learn.microsoft.com/en-us/graph/api/security-host-list-trackers?view=graph-rest-1.0) | [microsoft.graph.security.hostTracker](https://learn.microsoft.com/en-us/graph/api/resources/security-hosttracker?view=graph-rest-1.0) collection | Get a list of **hostTracker** resources. |
| [List hostSslCertificates](https://learn.microsoft.com/en-us/graph/api/security-host-list-sslcertificates?view=graph-rest-1.0) | [microsoft.graph.security.hostSslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0) collection | Get a list of [hostSslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0) objects from the [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) navigation property. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| firstSeenDateTime | DateTimeOffset | The first date and time when this host was observed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | Unique identifier for the host. Read-only. Inherited from [microsoft.graph.security.artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0). |
| lastSeenDateTime | DateTimeOffset | The most recent date and time when this host was observed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| childHostPairs | [microsoft.graph.security.hostPair](https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0) collection | The **hostPairs** that are resources associated with a host, where that host is the **parentHost** and has an outgoing pairing to a **childHost**. |
| components | [microsoft.graph.security.hostComponent](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcomponent?view=graph-rest-1.0) collection | The **hostComponents** that are associated with this host. |
| cookies | [microsoft.graph.security.hostCookie](https://learn.microsoft.com/en-us/graph/api/resources/security-hostcookie?view=graph-rest-1.0) collection | The **hostCookies** that are associated with this host. |
| hostPairs | [microsoft.graph.security.hostPair](https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0) collection | The **hostPairs** that are associated with this host, where this host is either the **parentHost** or **childHost**. |
| parentHostPairs | [microsoft.graph.security.hostPair](https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0) collection | The **hostPairs** that are associated with a host, where that host is the **childHost** and has an incoming pairing with a **parentHost**. |
| passiveDns | [microsoft.graph.security.passiveDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0) collection | Passive DNS retrieval about this host. |
| passiveDnsReverse | [microsoft.graph.security.passiveDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-passivednsrecord?view=graph-rest-1.0) collection | Reverse passive DNS retrieval about this host. |
| ports | [microsoft.graph.security.hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0) collection | The **hostPorts** associated with a host. |
| reputation | [microsoft.graph.security.hostReputation](https://learn.microsoft.com/en-us/graph/api/resources/security-hostreputation?view=graph-rest-1.0) | Represents a calculated reputation of this host. |
| sslCertificates | [microsoft.graph.security.hostSslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0) collection | The **hostSslCertificates** that are associated with this host. |
| subdomains | [microsoft.graph.security.subdomain](https://learn.microsoft.com/en-us/graph/api/resources/security-subdomain?view=graph-rest-1.0) collection | The **subdomains** that are associated with this host. |
| trackers | [microsoft.graph.security.hostTracker](https://learn.microsoft.com/en-us/graph/api/resources/security-hosttracker?view=graph-rest-1.0) collection | The **hostTrackers** that are associated with this host. |
| whois | [microsoft.graph.security.whoisRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-whoisrecord?view=graph-rest-1.0) | The most recent **whoisRecord** for this host. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.host",
  "firstSeenDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastSeenDateTime": "String (timestamp)"
}
```
