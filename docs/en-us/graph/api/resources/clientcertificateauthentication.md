<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/clientcertificateauthentication?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# clientCertificateAuthentication resource type

Namespace: microsoft.graph

A type derived from apiAuthenticationConfigurationBase that is used to represent a Pkcs12-based client certificate authentication. This is used to retrieve the public properties of uploaded certificates.

Inherits from [apiAuthenticationConfigurationBase](https://learn.microsoft.com/en-us/graph/api/resources/apiauthenticationconfigurationbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| certificateList | [pkcs12CertificateInformation](https://learn.microsoft.com/en-us/graph/api/resources/pkcs12certificateinformation?view=graph-rest-1.0) collection | The list of certificates uploaded for this API connector. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.clientCertificateAuthentication",
  "certificateList": "Collection(microsoft.graph.pkcs12CertificateInformation)",
}
```
