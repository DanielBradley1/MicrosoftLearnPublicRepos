<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-symanteccodesigningcertificate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# symantecCodeSigningCertificate resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get symantecCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/intune-apps-symanteccodesigningcertificate-get?view=graph-rest-beta) | [symantecCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-symanteccodesigningcertificate?view=graph-rest-beta) | Read properties and relationships of the [symantecCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-symanteccodesigningcertificate?view=graph-rest-beta) object. |
| [Update symantecCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/intune-apps-symanteccodesigningcertificate-update?view=graph-rest-beta) | [symantecCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-symanteccodesigningcertificate?view=graph-rest-beta) | Update the properties of a [symantecCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-symanteccodesigningcertificate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The key of the entity. This property is read-only. |
| content | Binary | The Windows Symantec Code-Signing Certificate in the raw data format. |
| status | [certificateStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-certificatestatus?view=graph-rest-beta) | The Cert Status Provisioned or not Provisioned. Possible values are: `notProvisioned`, `provisioned`. |
| password | String | The Password required for .pfx file. |
| subjectName | String | The Subject Name for the cert. |
| subject | String | The Subject value for the cert. |
| issuerName | String | The Issuer Name for the cert. |
| issuer | String | The Issuer value for the cert. |
| expirationDateTime | DateTimeOffset | The Cert Expiration Date. |
| uploadDateTime | DateTimeOffset | The Type of the CodeSigning Cert as Symantec Cert. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.symantecCodeSigningCertificate",
  "id": "String (identifier)",
  "content": "binary",
  "status": "String",
  "password": "String",
  "subjectName": "String",
  "subject": "String",
  "issuerName": "String",
  "issuer": "String",
  "expirationDateTime": "String (timestamp)",
  "uploadDateTime": "String (timestamp)"
}
```
