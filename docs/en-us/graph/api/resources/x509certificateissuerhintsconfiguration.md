<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/x509certificateissuerhintsconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-08 -->

# x509CertificateIssuerHintsConfiguration resource type

Namespace: microsoft.graph

Determines whether issuer\(CA\) hints are sent back to the client side to filter the certificates shown in certificate picker. Configured on the [x509CertificateAuthenticationMethodConfiguration resource type](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthenticationmethodconfiguration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| state | x509CertificateIssuerHintsState | The possible values are: `disabled`, `enabled`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.x509CertificateIssuerHintsConfiguration",
  "state": "String"
}
```
