<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-26 -->

# sslCertificate resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

Represents an SSL certificate that is a digital certificate that enables secure and encrypted communication between a website and its users, protecting sensitive information. It verifies the identity of a website and encrypts data to ensure privacy and build user trust. When Microsoft Defender Threat Intelligence crawls a website, it indexes SSL certificates so users can search them. Malicious actors can exploit SSL certificates by using fraudulent certificates to create deceptive websites or compromising legitimate certificates to intercept encrypted communications.

Inherits from [artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-threatintelligence-list-sslcertificates?view=graph-rest-1.0) | [microsoft.graph.security.sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) collection | Get a list of [sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-sslcertificate-get?view=graph-rest-1.0) | [microsoft.graph.security.sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) | Get the properties and relationships of an [sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0) object. |
| [List related hosts](https://learn.microsoft.com/en-us/graph/api/security-sslcertificate-list-relatedhosts?view=graph-rest-1.0) | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) collection | Get a list of related [host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) resources associated with an [sslCertificate](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificate?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expirationDateTime | DateTimeOffset | The date and time when a certificate expires. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| fingerprint | String | A hash of the certificate calculated on the data and signature. |
| firstSeenDateTime | DateTimeOffset | The first date and time when this **sslCertificate** was observed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| id | String | The system-generated ID for this **sslCertificate**. Inherited from [artifact](https://learn.microsoft.com/en-us/graph/api/resources/security-artifact?view=graph-rest-1.0). |
| issueDateTime | DateTimeOffset | The date and time when a certificate was issued. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| issuer | [microsoft.graph.security.sslCertificateEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificateentity?view=graph-rest-1.0) | The entity that grants this certificate. |
| lastSeenDateTime | DateTimeOffset | The most recent date and time when this **sslCertificate** was observed. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| serialNumber | String | The serial number associated with an SSL certificate. |
| sha1 | String | A SHA-1 hash of the certificate. **Note:** This is not the signature. |
| subject | [microsoft.graph.security.sslCertificateEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-sslcertificateentity?view=graph-rest-1.0) | The person, site, machine, and so on, this certificate is for. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| relatedHosts | [microsoft.graph.security.host](https://learn.microsoft.com/en-us/graph/api/resources/security-host?view=graph-rest-1.0) collection | The **host** resources related with this **sslCertificate**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.sslCertificate",
  "expirationDateTime": "String (timestamp)",
  "fingerprint": "String",
  "firstSeenDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "issueDateTime": "String (timestamp)",
  "issuer": {"@odata.type": "microsoft.graph.security.sslCertificateEntity"},
  "lastSeenDateTime": "String (timestamp)",
  "serialNumber": "String",
  "sha1": "String",
  "subject": {"@odata.type": "microsoft.graph.security.sslCertificateEntity"}
}
```
