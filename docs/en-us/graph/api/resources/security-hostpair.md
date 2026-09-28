<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# hostPair resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents a pair of parent-child hosts in which the child host is able to be reached via the parent host. For example, if contoso.com redirects to microsoft.com, then contoso.com represents the parent host and microsoft.com the child host.

Host pair relationships shared at an earlier point, or currently share a connection observed from a Microsoft crawl. A parent host leads to the child host perhaps through a simple top-level redirect \(HTTP 302\), or something more complex like an iframe or script source reference. In other instances, a web crawl may reveal odd behaviors such as host pair relationships between IP addresses and domains/hosts that go against DNS standards.

The **linkKind** property notes the reason to identify the hosts as a parent-child pair. An example of this may be `redirect`.

For more information about host pairs, see the Microsoft Defender Threat Intelligence documentation for [data sets](https://learn.microsoft.com/en-us/defender/threat-intelligence/data-sets#host-pairs).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-hostpair-get?view=graph-rest-1.0) | [microsoft.graph.security.hostPair](https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0) | Read the properties and relationships of a **hostPair** object. |
| [List for a host](https://learn.microsoft.com/en-us/graph/api/security-host-list-hostpairs?view=graph-rest-1.0) | [microsoft.graph.security.hostPair](https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0) collection | Get a list of **hostPair** objects associated with a specified host, where the host is either the parent *or* child. |
| [List for a host as child](https://learn.microsoft.com/en-us/graph/api/security-host-list-parenthostpairs?view=graph-rest-1.0) | [microsoft.graph.security.hostPair](https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0) collection | Get a list of **hostPair** objects associated with a host, where that host is the *child* and has an incoming pairing with a *parent*. |
| [List for a host as parent](https://learn.microsoft.com/en-us/graph/api/security-host-list-childhostpairs?view=graph-rest-1.0) | [microsoft.graph.security.hostPair](https://learn.microsoft.com/en-us/graph/api/resources/security-hostpair?view=graph-rest-1.0) collection | Get a list of **hostPair** objects associated with a host, where that host is the *parent* and has an outgoing pairing to a *child*. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| firstSeenDateTime | DateTimeOffset | The date and time when Microsoft Defender Threat Intelligence first observed the **hostPair**. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | A system-generated ID for the **hostPair**. |
| lastSeenDateTime | DateTimeOffset | The date and time when Microsoft Defender Threat Intelligence last observed the **hostPair**. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| linkKind | String | The reason that two hosts are identified as **hostPair**. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| childHost | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) | Host reached via the **parentHost**. |
| parentHost | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) | Host used to reach the **childHost**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.hostPair",
  "firstSeenDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastSeenDateTime": "String (timestamp)",
  "linkKind": "String"
}
```
