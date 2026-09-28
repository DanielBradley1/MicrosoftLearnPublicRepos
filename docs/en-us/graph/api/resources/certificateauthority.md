<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/certificateauthority?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# certificateAuthority resource type

Namespace: microsoft.graph

Used by the **certificateAuthorities** property of [certificateBasedAuthConfiguration resource type](https://learn.microsoft.com/en-us/graph/api/resources/certificatebasedauthconfiguration?view=graph-rest-1.0) to represent a certificate authority.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| certificate | Binary | Required. The base64 encoded string representing the public certificate. |
| certificateRevocationListUrl | String | The URL of the certificate revocation list. |
| deltaCertificateRevocationListUrl | String | The URL contains the list of all revoked certificates since the last time a full certificate revocaton list was created. |
| isRootAuthority | Boolean | Required. **true** if the trusted certificate is a root authority, **false** if the trusted certificate is an intermediate authority. |
| issuer | String | The issuer of the certificate, calculated from the **certificate** value. Read-only. |
| issuerSki | String | The subject key identifier of the certificate, calculated from the **certificate** value. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "certificate": "Binary",
  "certificateRevocationListUrl": "String",
  "deltaCertificateRevocationListUrl": "String",
  "isRootAuthority": true,
  "issuer": "String",
  "issuerSki": "String"
}
```
