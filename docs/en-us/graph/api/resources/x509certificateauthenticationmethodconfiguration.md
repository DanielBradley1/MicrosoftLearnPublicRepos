<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthenticationmethodconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-08 -->

# x509CertificateAuthenticationMethodConfiguration resource type

Namespace: microsoft.graph

Represents the details of the Microsoft Entra native Certificate-Based Authentication \(CBA\) in the tenant, including whether the authentication method is enabled or disabled and the users and groups who can register and use it.

Inherits from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/x509certificateauthenticationmethodconfiguration-get?view=graph-rest-1.0) | [x509CertificateAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthenticationmethodconfiguration?view=graph-rest-1.0) | Read the properties and relationships of a x509CertificateAuthenticationMethodConfiguration object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/x509certificateauthenticationmethodconfiguration-update?view=graph-rest-1.0) | [x509CertificateAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthenticationmethodconfiguration?view=graph-rest-1.0) | Update the properties of a x509CertificateAuthenticationMethodConfiguration object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/x509certificateauthenticationmethodconfiguration-delete?view=graph-rest-1.0) | None | Delete the tenant-customized x509CertificateAuthenticationMethodConfiguration object and restore the default configuration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationModeConfiguration | [x509CertificateAuthenticationModeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthenticationmodeconfiguration?view=graph-rest-1.0) | Defines strong authentication configurations. This configuration includes the default authentication mode and the different rules for strong authentication bindings. |
| certificateAuthorityScopes | [x509CertificateAuthorityScope](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateauthorityscope?view=graph-rest-1.0) collection | Defines configuration to allow a group of users to use certificates from specific issuing certificate authorities to successfully authenticate. |
| certificateUserBindings | [x509CertificateUserBinding](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateuserbinding?view=graph-rest-1.0) collection | Defines fields in the X.509 certificate that map to attributes of the Microsoft Entra user object in order to bind the certificate to the user. The **priority** of the object determines the order in which the binding is carried out. The first binding that matches will be used and the rest ignored. |
| crlValidationConfiguration | [x509CertificateCRLValidationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/x509certificatecrlvalidationconfiguration?view=graph-rest-1.0) | Determines whether certificate based authentication should fail if the issuing CA doesn't have a valid certificate revocation list configured. |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups of users that are excluded from the policy. |
| id | String | The identifier for the authentication method policy. The value is always `X509Certificate`. Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0). |
| issuerHintsConfiguration | [x509CertificateIssuerHintsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/x509certificateissuerhintsconfiguration?view=graph-rest-1.0) | Determines whether issuer\(CA\) hints are sent back to the client side to filter the certificates shown in certificate picker. |
| state | authenticationMethodState | The possible values are: `enabled`, `disabled`. Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includeTargets | [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-1.0) collection | A collection of groups that are enabled to use the authentication method. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.x509CertificateAuthenticationMethodConfiguration",
  "id": "String (identifier)",
  "state": "String",
  "excludeTargets": [
    {
      "@odata.type": "microsoft.graph.excludeTarget"
    }
  ],
  "certificateUserBindings": [
    {
      "@odata.type": "microsoft.graph.x509CertificateUserBinding"
    }
  ],
  "authenticationModeConfiguration": {
    "@odata.type": "microsoft.graph.x509CertificateAuthenticationModeConfiguration"
  },
  "issuerHintsConfiguration": {
    "@odata.type": "microsoft.graph.x509CertificateIssuerHintsConfiguration"
  },
  "certificateAuthorityScopes": [
    {
      "@odata.type": "microsoft.graph.x509CertificateAuthorityScope"
    }
  ],
  "crlValidationConfiguration": {
    "@odata.type": "microsoft.graph.x509CertificateCRLValidationConfiguration"
  }
}
```
