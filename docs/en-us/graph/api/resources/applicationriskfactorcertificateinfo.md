<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactorcertificateinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-04 -->

# applicationRiskFactorCertificateInfo resource type

Namespace: microsoft.graph

Provides SSL/TLS certificate validation and risk assessment details for an application, highlighting potential security misconfigurations or trust issues. The **certificate** property of the [applicationRiskFactorSecurityInfo](https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactorsecurityinfo?view=graph-rest-1.0) resource is an **applicationRiskFactorCertificateInfo** object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hasBadCommonName | Boolean | Indicates whether the certificate's common name doesn't match the expected domain name. |
| hasInsecureSignature | Boolean | Indicates whether the certificate uses a weak or insecure signature algorithm \(for example, MD5 or SHA-1\). |
| hasNoChainOfTrust | Boolean | Indicates whether the certificate chain of trust is incomplete or invalid. |
| isDenylisted | Boolean | Indicates whether the certificate is on a known denylist or associated with compromised issuers. |
| isHostnameMismatch | Boolean | Indicates whether the certificate's hostname doesn't match the domain it was issued for. |
| isNotAfter | Boolean | Indicates whether the certificate is expired and no longer valid. |
| isNotBefore | Boolean | Indicates whether the certificate isn't yet valid based on its activation date. |
| isRevoked | Boolean | Indicates whether the issuing certificate authority revoked the certificate. |
| isSelfSigned | Boolean | Indicates whether the certificate is self-signed rather than issued by a trusted certificate authority. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.applicationRiskFactorCertificateInfo",
  "hasBadCommonName": "Boolean",
  "isHostnameMismatch": "Boolean",
  "hasInsecureSignature": "Boolean",
  "isDenylisted": "Boolean",
  "isRevoked": "Boolean",
  "hasNoChainOfTrust": "Boolean",
  "isNotAfter": "Boolean",
  "isNotBefore": "Boolean",
  "isSelfSigned": "Boolean"
}
```
