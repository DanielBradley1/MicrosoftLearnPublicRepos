<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthenticationmodeconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# x509CertificateAuthenticationModeConfiguration resource type

Namespace: microsoft.graph

Defines the strong authentication configurations for the X.509 certificate. This configuration includes the default authentication mode and the different rules of strong authentication bindings.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| rules | [x509CertificateRule](https://learn.microsoft.com/en-us/graph/api/resources/x509certificaterule?view=graph-rest-1.0) collection | Rules are configured in addition to the authentication mode to bind a specific **x509CertificateRuleType** to an **x509CertificateAuthenticationMode**. For example, bind the `policyOID` with identifier `1.32.132.343` to `x509CertificateMultiFactor` authentication mode. |
| x509CertificateAuthenticationDefaultMode | x509CertificateAuthenticationMode | The type of strong authentication mode. The possible values are: `x509CertificateSingleFactor`, `x509CertificateMultiFactor`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.x509CertificateAuthenticationModeConfiguration",
  "rules": [
    {
      "@odata.type": "microsoft.graph.x509CertificateRule"
    }
  ],
  "x509CertificateAuthenticationDefaultMode": "String",
}
```
