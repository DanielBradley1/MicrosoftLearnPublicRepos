<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# hostSslCertificate resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents an observed relationship between a [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) and an [sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0).

Inherits from [artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-host-list-sslcertificates?view=graph-rest-1.0) | [microsoft.graph.security.hostSslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0) collection | Get a list of [hostSslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0) objects from the [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) navigation property. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-hostsslcertificate-get?view=graph-rest-1.0) | [microsoft.graph.security.hostSslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0) | Get the properties and relationships of a [hostSslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificate?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| firstSeenDateTime | DateTimeOffset | The first date and time when this **hostSslCertificate** was observed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The system-generated ID for this **hostSslCertificate**. Inherited from [artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0). |
| lastSeenDateTime | DateTimeOffset | The most recent date and time when this **hostSslCertificate** was observed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| ports | [microsoft.graph.security.hostSslCertificatePort](https://learn.microsoft.com/en-us/graph/api/resources/security-hostsslcertificateport?view=graph-rest-1.0) collection | The ports related with this **hostSslCertificate**. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| host | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) | The **host** for this **hostSslCertificate**. |
| sslCertificate | [microsoft.graph.security.sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) | The **sslCertificate** for this **hostSslCertificate**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.hostSslCertificate",
  "firstSeenDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastSeenDateTime": "String (timestamp)",
  "ports": [{"@odata.type": "microsoft.graph.security.hostSslCertificatePort"}]
}
```
