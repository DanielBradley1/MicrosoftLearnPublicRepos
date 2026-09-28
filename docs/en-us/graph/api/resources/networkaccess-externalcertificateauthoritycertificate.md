<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-externalcertificateauthoritycertificate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-24 -->

# externalCertificateAuthorityCertificate resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a customer's Certificate Authority \(CA\) certificate used for TLS inspection in Global Secure Access. This resource enables secure TLS termination at the edge while using customer-managed certificates for traffic inspection. When creating a new CA, the service generates a Certificate Signing Request \(CSR\) that customers can sign using their PKI infrastructure, providing a secure way to use customer certificates without sharing private keys.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta)

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-tlstermination-list-externalcertificateauthoritycertificates?view=graph-rest-beta) | [microsoft.graph.networkaccess.externalCertificateAuthorityCertificate](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-externalcertificateauthoritycertificate?view=graph-rest-beta) collection | Get a list of the externalCertificateAuthorityCertificate objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/networkaccess-tlstermination-post-externalcertificateauthoritycertificates?view=graph-rest-beta) | [microsoft.graph.networkaccess.externalCertificateAuthorityCertificate](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-externalcertificateauthoritycertificate?view=graph-rest-beta) | Create a new externalCertificateAuthorityCertificate object and receive a Certificate Signing Request \(CSR\). |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-externalcertificateauthoritycertificate-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.externalCertificateAuthorityCertificate](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-externalcertificateauthoritycertificate?view=graph-rest-beta) | Get an externalCertificateAuthorityCertificate object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-externalcertificateauthoritycertificate-update?view=graph-rest-beta) | None | Update the properties of an externalCertificateAuthorityCertificate object, including uploading the signed certificate. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/networkaccess-externalcertificateauthoritycertificate-delete?view=graph-rest-beta) | None | Delete an externalCertificateAuthorityCertificate object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| certificate | String | The signed X.509 certificate in PEM format. |
| certificateSigningRequest | String | The Certificate Signing Request \(CSR\) generated when creating the CA. This CSR should be signed using the customer's PKI infrastructure. Read-only. |
| chain | String | The certificate chain in PEM format, containing all intermediate certificates up to the root CA. |
| commonName | String | The common name \(CN\) field of the certificate. Supports `$filter` \(`eq`, `ne`, `startsWith`\) |
| id | String | The unique identifier for the CA. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Read-only. |
| name | String | The display name of the CA. Supports `$filter` \(`eq`, `ne`, `startsWith`\) |
| organizationName | String | The organization name \(OU\) field of the certificate. Supports `$filter` \(`eq`, `ne`, `startsWith`\) |
| status | microsoft.graph.networkaccess.tlsCertificateStatus | The current status of the certificate. The possible values are: `csrGenerated`, `enrolling`, `active`, `unknownFutureValue`, `expiring`, `expired`, `enabled`, `disabled`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this {evolvable enum}\(/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations\): `expiring`, `expired`, `enabled`, `disabled`. Read-only. Supports `$filter` \(`eq`, `ne`\). |
| validity | [microsoft.graph.networkaccess.validityDate](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-validitydate?view=graph-rest-beta) | The validity period of the certificate, including start and end dates. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.externalCertificateAuthorityCertificate",
  "id": "String (identifier)",
  "name": "String",
  "commonName": "String",
  "organizationName": "String",
  "validity": {
    "@odata.type": "microsoft.graph.networkaccess.validityDate"
  },
  "status": "String",
  "certificateSigningRequest": "String",
  "certificate": "String",
  "chain": "String"
}
```
