<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-enterprisecodesigningcertificate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# enterpriseCodeSigningCertificate resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Not yet documented

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List enterpriseCodeSigningCertificates](https://learn.microsoft.com/en-us/graph/api/intune-apps-enterprisecodesigningcertificate-list?view=graph-rest-1.0) | [enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-enterprisecodesigningcertificate?view=graph-rest-1.0) collection | List properties and relationships of the [enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-enterprisecodesigningcertificate?view=graph-rest-1.0) objects. |
| [Get enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/intune-apps-enterprisecodesigningcertificate-get?view=graph-rest-1.0) | [enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-enterprisecodesigningcertificate?view=graph-rest-1.0) | Read properties and relationships of the [enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-enterprisecodesigningcertificate?view=graph-rest-1.0) object. |
| [Create enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/intune-apps-enterprisecodesigningcertificate-create?view=graph-rest-1.0) | [enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-enterprisecodesigningcertificate?view=graph-rest-1.0) | Create a new [enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-enterprisecodesigningcertificate?view=graph-rest-1.0) object. |
| [Delete enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/intune-apps-enterprisecodesigningcertificate-delete?view=graph-rest-1.0) | None | Deletes a [enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-enterprisecodesigningcertificate?view=graph-rest-1.0). |
| [Update enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/intune-apps-enterprisecodesigningcertificate-update?view=graph-rest-1.0) | [enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-enterprisecodesigningcertificate?view=graph-rest-1.0) | Update the properties of a [enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-enterprisecodesigningcertificate?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the certificate, assigned upon creation. Supports: $filter, $select, $top, $OrderBy, $skip. $Search is not supported. Read-only. |
| content | Binary | The Windows Enterprise Code-Signing Certificate in the raw data format. Set to null once certificate has been uploaded and other properties have been populated. |
| status | certificateStatus | Whether the Certificate Status Provisioned or not Provisioned. The possible values are: notProvisioned, provisioned. Default is notProvisioned. Uploading a valid cert file through the Intune admin console will automatically populate this value in the HTTP response. Supports: $filter, $select, $top, $OrderBy, $skip. $Search is not supported. The possible values are: `notProvisioned`, `provisioned`. |
| subjectName | String | The subject name for the cert. This might contain information such as country \(C\), state or province \(S\), locality \(L\), common name of the cert \(CN\), organization \(O\), and organizational unit \(OU\). Uploading a valid cert file through the Intune admin console will automatically populate this value in the HTTP response. Supports: $filter, $select, $top, $OrderBy, $skip. $Search is not supported. |
| subject | String | The subject value for the cert. This might contain information such as country \(C\), state or province \(S\), locality \(L\), common name of the cert \(CN\), organization \(O\), and organizational unit \(OU\). Uploading a valid cert file through the Intune admin console will automatically populate this value in the HTTP response. Supports: $filter, $select, $top, $OrderBy, $skip. $Search is not supported. |
| issuerName | String | The issuer name for the cert. This might contain information such as country \(C\), state or province \(S\), locality \(L\), common name of the cert \(CN\), organization \(O\), and organizational unit \(OU\). Uploading a valid cert file through the Intune admin console will automatically populate this value in the HTTP response. Supports: $filter, $select, $top, $OrderBy, $skip. $Search is not supported. |
| issuer | String | The issuer value for the cert. This might contain information such as country \(C\), state or province \(S\), locality \(L\), common name of the cert \(CN\), organization \(O\), and organizational unit \(OU\). Uploading a valid cert file through the Intune admin console will automatically populate this value in the HTTP response. Supports: $filter, $select, $top, $OrderBy, $skip. $Search is not supported. |
| expirationDateTime | DateTimeOffset | The cert expiration date and time \(using ISO 8601 format, in UTC time\). Uploading a valid cert file through the Intune admin console will automatically populate this value in the HTTP response. Supports: $filter, $select, $top, $OrderBy, $skip. $Search is not supported. |
| uploadDateTime | DateTimeOffset | The date time of CodeSigning Cert when it is uploaded \(using ISO 8601 format, in UTC time\). Uploading a valid cert file through the Intune admin console will automatically populate this value in the HTTP response. Supports: $filter, $select, $top, $OrderBy, $skip. $Search is not supported. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.enterpriseCodeSigningCertificate",
  "id": "String (identifier)",
  "content": "binary",
  "status": "String",
  "subjectName": "String",
  "subject": "String",
  "issuerName": "String",
  "issuer": "String",
  "expirationDateTime": "String (timestamp)",
  "uploadDateTime": "String (timestamp)"
}
```
