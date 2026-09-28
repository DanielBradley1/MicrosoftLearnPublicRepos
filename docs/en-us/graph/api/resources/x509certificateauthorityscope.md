<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthorityscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-08 -->

# x509CertificateAuthorityScope resource type

Namespace: microsoft.graph

Defines configuration to allow a group of users to use certificates from specific issuing certificate authorities to successfully authenticate. Configured on the [x509CertificateAuthenticationMethodConfiguration resource type](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthenticationmethodconfiguration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| includeTargets | [includeTarget](https://learn.microsoft.com/en-us/graph/api/resources/includetarget?view=graph-rest-1.0) collection | A collection of groups that are enabled to be in scope to use certificates issued by specific certificate authority. |
| publicKeyInfrastructureIdentifier | String | Public Key Infrastructure container object under which the certificate authorities are stored in the Entra PKI based trust store. |
| subjectKeyIdentifier | String | Subject Key Identifier that identifies the certificate authority uniquely. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.x509CertificateAuthorityScope",
    "subjectKeyIdentifier": "String",
    "publicKeyInfrastructureIdentifier": "String",
    "includeTargets": [
    {
        "@odata.type": "microsoft.graph.includeTarget"
    }
    ]
}
```
