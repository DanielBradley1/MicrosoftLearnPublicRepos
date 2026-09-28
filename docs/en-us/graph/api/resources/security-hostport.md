<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# hostPort resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents the connection endpoints that direct data to and from the services that run on a [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-host-list-ports?view=graph-rest-1.0) | [microsoft.graph.security.hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0) collection | Get a list of **hostPort** objects assoicated with a **host**. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-hostport-get?view=graph-rest-1.0) | [microsoft.graph.security.hostPort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostport?view=graph-rest-1.0) | Read the properties and relationships of a **hostPort** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| banners | [microsoft.graph.security.hostPortBanner](https://learn.microsoft.com/en-us/graph/api/resources/security-hostportbanner?view=graph-rest-1.0) collection | The **hostPortBanners** retrieved from scanning the port. |
| firstSeenDateTime | DateTimeOffset | The first date and time when Microsoft Defender Threat Intelligence observed the **hostPort**. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. |
| id | String | A system-generated ID for the **hostPort**. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| lastScanDateTime | DateTimeOffset | The last date and time when Microsoft Defender Threat Intelligence scanned the **hostPort**. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. |
| lastSeenDateTime | DateTimeOffset | The last date and time when Microsoft Defender Threat Intelligence observed the **hostPort**. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014, is `2014-01-01T00:00:00Z`. |
| port | Int32 | The numerical identifier of the port which is standardized across the internet. |
| protocol | microsoft.graph.security.hostPortProtocol | The general protocol used to scan the port. The possible values are: `tcp`, `udp`, `unknownFutureValue`. |
| services | [microsoft.graph.security.hostPortComponent](https://learn.microsoft.com/en-us/graph/api/resources/security-hostportcomponent?view=graph-rest-1.0) collection | The **hostPortComponents** retrieved from scanning the port. |
| status | microsoft.graph.security.hostPortStatus | The status of the port. The possible values are: `open`, `filtered`, `closed`, `unknownFutureValue`. |
| timesObserved | Int32 | The total amount of times that Microsoft Defender Threat Intelligence has observed the **hostPort** in all its scans. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| host | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) | The **host** related to this **hostPort**. This is a reverse navigation property. When you navigate to **hostPorts** from a **host**, assume that this is a return reference. |
| mostRecentSslCertificate | [microsoft.graph.security.sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) | The most recent **sslCertificate** used to communicate on the port. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.hostPort",
  "banners": [{"@odata.type": "microsoft.graph.security.hostPortBanner"}],
  "firstSeenDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastScanDateTime": "String (timestamp)",
  "lastSeenDateTime": "String (timestamp)",
  "port": "Int32",
  "protocol": "String",
  "services": [{"@odata.type": "microsoft.graph.security.hostPortComponent"}],
  "status": "String",
  "timesObserved": "Int32"
}
```
