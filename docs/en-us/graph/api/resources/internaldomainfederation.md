<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/internaldomainfederation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-03-28 -->

# internalDomainFederation resource type

Namespace: microsoft.graph

Represents configurations of tenant domains that are federated and verified with Microsoft Entra ID. Use this resource to configure federation settings when you set up federation with Microsoft Entra ID. For information about federation, see [What is federation with Microsoft Entra ID?](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/whatis-fed).

Inherits from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/domain-list-federationconfiguration?view=graph-rest-1.0) | [internalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/internaldomainfederation?view=graph-rest-1.0) collection | Read the properties of the [internalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/internaldomainfederation?view=graph-rest-1.0) object for the domain. |
| [Create](https://learn.microsoft.com/en-us/graph/api/domain-post-federationconfiguration?view=graph-rest-1.0) | [internalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/internaldomainfederation?view=graph-rest-1.0) | Create a new [internalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/internaldomainfederation?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/internaldomainfederation-get?view=graph-rest-1.0) | [internalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/internaldomainfederation?view=graph-rest-1.0) | Read the properties and relationships of an [internalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/internaldomainfederation?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/internaldomainfederation-update?view=graph-rest-1.0) | [internalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/internaldomainfederation?view=graph-rest-1.0) | Update the properties of an [internalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/internaldomainfederation?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/internaldomainfederation-delete?view=graph-rest-1.0) | None | Delete an [internalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/internaldomainfederation?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activeSignInUri | String | URL of the endpoint used by active clients when authenticating with federated domains set up for single sign-on in Microsoft Entra ID. Corresponds to the **ActiveLogOnUri** property of the [Set-EntraDomainFederationSettings PowerShell cmdlet](https://learn.microsoft.com/en-us/powershell/module/microsoft.entra.directorymanagement/set-entradomainfederationsettings). |
| displayName | String | The display name of the federated identity Provider \(IdP\). Inherited from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0). |
| federatedIdpMfaBehavior | federatedIdpMfaBehavior | Determines whether Microsoft Entra ID accepts the MFA performed by the federated IdP when a federated user accesses an application that is governed by a conditional access policy that requires MFA. The possible values are: `acceptIfMfaDoneByFederatedIdp`, `enforceMfaByFederatedIdp`, `rejectMfaByFederatedIdp`, `unknownFutureValue`. For more information, see [federatedIdpMfaBehavior values](#federatedidpmfabehavior-values). |
| id | String | The identifier of the federated identity provider. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isSignedAuthenticationRequestRequired | Boolean | If `true`, when SAML authentication requests are sent to the federated SAML IdP, Microsoft Entra ID will sign those requests using the OrgID signing key. If `false` \(default\), the SAML authentication requests sent to the federated IdP aren't signed. |
| issuerUri | String | Issuer URI of the federation server. Inherited from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0). |
| metadataExchangeUri | String | URI of the metadata exchange endpoint used for authentication from rich client applications. Inherited from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0). |
| nextSigningCertificate | String | Fallback token signing certificate that can also be used to sign tokens, for example when the primary signing certificate expires. Formatted as Base64 encoded strings of the public portion of the federated IdP's token signing certificate. Needs to be compatible with the X509Certificate2 class. Much like the signingCertificate, the nextSigningCertificate property is used if a rollover is required outside of the auto-rollover update, a new federation service is being set up, or if the new token signing certificate isn't present in the federation properties after the federation service certificate has been updated. |
| passiveSignInUri | String | URI that web-based clients are directed to when signing into Microsoft Entra services. Inherited from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0). |
| preferredAuthenticationProtocol | authenticationProtocol | Preferred authentication protocol. This parameter must be configured explicitly for the federation passive authentication flow to work. The possible values are: `wsFed`, `saml`, `unknownFutureValue`. Inherited from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0). |
| promptLoginBehavior | promptLoginBehavior | Sets the preferred behavior for the sign-in prompt. The possible values are: `translateToFreshPasswordAuthentication`, `nativeSupport`, `disabled`, `unknownFutureValue`. |
| signingCertificate | String | Current certificate used to sign tokens passed to the Microsoft identity platform. The certificate is formatted as a Base64 encoded string of the public portion of the federated IdP's token signing certificate and must be compatible with the X509Certificate2 class.  <br>This property is used in the following scenarios:<br><br><li> If a rollover is required outside of the autorollover update </li><br><br><li> A new federation service is being set up </li><br><br><li> If the new token signing certificate isn&#39;t present in the federation properties after the federation service certificate has been updated.<br>Microsoft Entra ID updates certificates via an autorollover process in which it attempts to retrieve a new certificate from the federation service metadata, 30 days before expiry of the current certificate. If a new certificate isn&#39;t available, Microsoft Entra ID monitors the metadata daily and will update the federation settings for the domain when a new certificate is available. Inherited from <a href="https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0" data-linktype="relative-path">samlOrWsFedProvider</a>.</li> |
| signingCertificateUpdateStatus | [signingCertificateUpdateStatus](https://learn.microsoft.com/en-us/graph/api/resources/signingcertificateupdatestatus?view=graph-rest-1.0) | Provides status and timestamp of the last update of the signing certificate. |
| signOutUri | String | URI that clients are redirected to when they sign out of Microsoft Entra services. Corresponds to the **LogOffUri** property of the [Set-EntraDomainFederationSettings PowerShell cmdlet](https://learn.microsoft.com/en-us/powershell/module/microsoft.entra.directorymanagement/set-entradomainfederationsettings). |

### federatedIdpMfaBehavior values

| Member | Description |
| :--- | :--- |
| acceptIfMfaDoneByFederatedIdp | Microsoft Entra ID accepts MFA that's performed by the federated identity provider. If the federated identity provider didn't perform MFA, Microsoft Entra ID performs the MFA. |
| enforceMfaByFederatedIdp | Microsoft Entra ID accepts MFA that's performed by federated identity provider. If the federated identity provider didn't perform MFA, it redirects the request to federated identity provider to perform MFA. |
| rejectMfaByFederatedIdp | Microsoft Entra ID always performs MFA and rejects MFA that's performed by the federated identity provider. |

Note

**federatedIdpMfaBehavior** is an evolved version of the **SupportsMfa** property of the **Domain Federation setting**.

- Switching between **federatedIdpMfaBehavior** and **SupportsMfa** is not supported.
- When **federatedIdpMfaBehavior** property is set, Microsoft Entra ID ignores the **SupportsMfa** setting.
- If the **federatedIdpMfaBehavior** property is never set, Microsoft Entra ID will continue to honor the **SupportsMfa** setting.
- If neither **federatedIdpMfaBehavior** nor **SupportsMfa** is set, Microsoft Entra ID will default to `acceptIfMfaDoneByFederatedIdp` behavior.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.internalDomainFederation",
  "id": "String (identifier)",
  "displayName": "String",
  "issuerUri": "String",
  "metadataExchangeUri": "String",
  "signingCertificate": "String",
  "passiveSignInUri": "String",
  "preferredAuthenticationProtocol": "String",
  "activeSignInUri": "String",
  "signOutUri": "String",
  "promptLoginBehavior": "String",
  "isSignedAuthenticationRequestRequired": "Boolean",
  "nextSigningCertificate": "String",
  "signingCertificateUpdateStatus": {
    "certificateUpdateResult": "String",
    "@odata.type": "microsoft.graph.signingCertificateUpdateStatus"
  },
  "federatedIdpMfaBehavior": "String"
}
```
