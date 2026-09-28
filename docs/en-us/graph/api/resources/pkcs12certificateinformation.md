<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/pkcs12certificateinformation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# pkcs12CertificateInformation resource type

Namespace: microsoft.graph

Represents the public information of a Pkcs12 certificate.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isActive | Boolean | Represents whether the certificate is the active certificate to be used for calling the API connector. The active certificate is the most recently uploaded certificate that isn't yet expired but whose notBefore time is in the past. |
| notAfter | Integer | The certificate's expiry. This value is a NumericDate as defined in RFC 7519 \(A JSON numeric value representing the number of seconds from 1970-01-01T00:00:00Z UTC until the specified UTC date/time, ignoring leap seconds.\) |
| notBefore | Integer | The certificate's issue time \(not before\). This value is a NumericDate as defined in RFC 7519 \(A JSON numeric value representing the number of seconds from 1970-01-01T00:00:00Z UTC until the specified UTC date/time, ignoring leap seconds.\) |
| thumbprint | String | The certificate thumbprint. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "isActive": "Boolean",
    "thumbprint": "String",
    "notAfter": "DateTime",
    "notBefore": "DateTime"
}
```
