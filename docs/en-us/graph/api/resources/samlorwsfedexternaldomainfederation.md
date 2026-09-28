<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedexternaldomainfederation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# samlOrWsFedExternalDomainFederation resource type

Namespace: microsoft.graph

Allows a Microsoft Entra tenant to federate with an external organization whose identity provider \(IdP\) supports either the SAML or WS-Fed protocol. This enables the Microsoft Entra tenant to allow guest users to access its resources. For more information on SAML or WS-Fed IdP federation, see [Federation with SAML or WS-Fed identity providers for guest users](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/direct-federation).

Inherits from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/samlorwsfedexternaldomainfederation-list?view=graph-rest-1.0) | [samlOrWsFedExternalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedexternaldomainfederation?view=graph-rest-1.0) collection | Get a list of the [samlOrWsFedExternalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedexternaldomainfederation?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/samlorwsfedexternaldomainfederation-post?view=graph-rest-1.0) | [samlOrWsFedExternalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedexternaldomainfederation?view=graph-rest-1.0) | Create a new [samlOrWsFedExternalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedexternaldomainfederation?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/samlorwsfedexternaldomainfederation-get?view=graph-rest-1.0) | [samlOrWsFedExternalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedexternaldomainfederation?view=graph-rest-1.0) | Read the properties and relationships of a [samlOrWsFedExternalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedexternaldomainfederation?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/samlorwsfedexternaldomainfederation-update?view=graph-rest-1.0) | [samlOrWsFedExternalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedexternaldomainfederation?view=graph-rest-1.0) | Update the properties of a [samlOrWsFedExternalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedexternaldomainfederation?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/samlorwsfedexternaldomainfederation-delete?view=graph-rest-1.0) | None | Deletes a [samlOrWsFedExternalDomainFederation](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedexternaldomainfederation?view=graph-rest-1.0) object. |
| [List domains](https://learn.microsoft.com/en-us/graph/api/samlorwsfedexternaldomainfederation-list-domains?view=graph-rest-1.0) | [externalDomainName](https://learn.microsoft.com/en-us/graph/api/resources/externaldomainname?view=graph-rest-1.0) collection | Get the externalDomainName resources from the domains navigation property. |
| [Create external domain name](https://learn.microsoft.com/en-us/graph/api/samlorwsfedexternaldomainfederation-post-domains?view=graph-rest-1.0) | [externalDomainName](https://learn.microsoft.com/en-us/graph/api/resources/externaldomainname?view=graph-rest-1.0) | Create a new externalDomainName object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the SAML or WS-Fed based IdP. Inherited from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0). |
| id | String | The identifier of the identity provider. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| issuerUri | String | Issuer URI of the federation server. Inherited from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0). |
| metadataExchangeUri | String | URI of the metadata exchange endpoint used for authentication from rich client applications. Inherited from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0). |
| passiveSignInUri | String | URI that web-based clients are directed to when signing in to Microsoft Entra services. Inherited from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0). |
| preferredAuthenticationProtocol | authenticationProtocol | Preferred authentication protocol. The possible values are: `wsFed`, `saml`, `unknownFutureValue`. Inherited from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0). |
| signingCertificate | String | Current certificate used to sign tokens passed to the Microsoft identity platform. The certificate is formatted as a Base64 encoded string of the public portion of the federated IdP's token signing certificate and must be compatible with the X509Certificate2 class.  <br>  <br>This property is used in the following scenarios:<br><br>- if a rollover is required outside of the autorollover update<br>- a new federation service is being set up<br>- if the new token signing certificate isn't present in the federation properties after the federation service certificate has been updated.<br><br>  <br>  <br>Microsoft Entra ID updates certificates via an autorollover process in which it attempts to retrieve a new certificate from the federation service metadata, 30 days before expiry of the current certificate. If a new certificate isn't available, Microsoft Entra ID monitors the metadata daily and will update the federation settings for the domain when a new certificate is available.  <br>  <br>Inherited from [samlOrWsFedProvider](https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| domains | [externalDomainName](https://learn.microsoft.com/en-us/graph/api/resources/externaldomainname?view=graph-rest-1.0) collection | Collection of domain names of the external organizations that the tenant is federating with. Supports `$filter` \(`eq`\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.samlOrWsFedExternalDomainFederation",
  "id": "String (identifier)",
  "displayName": "String",
  "issuerUri": "String",
  "metadataExchangeUri": "String",
  "signingCertificate": "String",
  "passiveSignInUri": "String",
  "preferredAuthenticationProtocol": "String"
}
```
