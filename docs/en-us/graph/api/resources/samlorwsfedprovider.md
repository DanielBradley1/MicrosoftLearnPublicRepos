<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/samlorwsfedprovider?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# samlOrWsFedProvider resource type

Namespace: microsoft.graph

An abstract type that provides configuration details for setting up a SAML or WS-Fed external domain-based identity provider \(IdP\).

Inherits from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the SAML/WS-Fed based identity provider. Inherited from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0). |
| id | String | The identifier of the identity provider. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| issuerUri | String | Issuer URI of the federation server. |
| metadataExchangeUri | String | URI of the metadata exchange endpoint used for authentication from rich client applications. |
| passiveSignInUri | String | URI that web-based clients are directed to when signing in to Microsoft Entra services. |
| preferredAuthenticationProtocol | authenticationProtocol | Preferred authentication protocol. The possible values are: `wsFed`, `saml`, `unknownFutureValue`. |
| signingCertificate | String | Current certificate used to sign tokens passed to the Microsoft identity platform. The certificate is formatted as a Base64 encoded string of the public portion of the federated IdP's token signing certificate and must be compatible with the X509Certificate2 class.  <br>  <br>This property is used in the following scenarios:<br><br>- if a rollover is required outside of the autorollover update<br>- a new federation service is being set up<br>- if the new token signing certificate isn't present in the federation properties after the federation service certificate has been updated.<br><br>  <br>  <br>Microsoft Entra ID updates certificates via an autorollover process in which it attempts to retrieve a new certificate from the federation service metadata, 30 days before expiry of the current certificate. If a new certificate isn't available, Microsoft Entra ID monitors the metadata daily and will update the federation settings for the domain when a new certificate is available. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.samlOrWsFedProvider",
  "id": "String (identifier)",
  "displayName": "String",
  "issuerUri": "String",
  "metadataExchangeUri": "String",
  "signingCertificate": "String",
  "passiveSignInUri": "String",
  "preferredAuthenticationProtocol": "String"
}
```
