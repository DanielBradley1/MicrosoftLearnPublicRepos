<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificateport?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# hostSslCertificatePort resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents the ports of a [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) where a [hostSslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0) is currently or was previously related.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| firstSeenDateTime | DateTimeOffset | The first date and time when this port was observed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| lastSeenDateTime | DateTimeOffset | The most recent date and time when this port was observed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| port | Int32 | The port number. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.hostSslCertificatePort",
  "firstSeenDateTime": "String (timestamp)",
  "lastSeenDateTime": "String (timestamp)",
  "port": "Int32"
}
```
