<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/x509certificaterule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-16 -->

# x509CertificateRule resource type

Namespace: microsoft.graph

Defines the strong authentication configuration rules for the X.509 certificate. Rules are configured in addition to the authentication mode.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifier | String | The identifier of the X.509 certificate. Required. |
| x509CertificateAuthenticationMode | x509CertificateAuthenticationMode | The type of strong authentication mode. The possible values are: `x509CertificateSingleFactor`, `x509CertificateMultiFactor`, `unknownFutureValue`. Required. |
| x509CertificateRuleType | x509CertificateRuleType | The type of the X.509 certificate mode configuration rule. The possible values are: `issuerSubject`, `policyOID`, `unknownFutureValue`. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.x509CertificateRule",
  "identifier": "String",
  "x509CertificateRuleType": "String",
  "x509CertificateAuthenticationMode": "String"
}
```
