<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/oidcidentityprovider?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-23 -->

# oidcIdentityProvider resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents OpenID Connect identity providers in a Microsoft Entra external tenant.

Configuring an OpenID Connect provider in an external tenant enables users to sign up and sign in to any application using their custom OpenID Connect identity provider.

Inherits from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-beta).

For more information, see [Add OpenID Connect as an external identity provider \(preview\)](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-custom-oidc-federation-customers).

## Methods

None.

For the list of API operations for managing the oidcIdentityProvider resource, see the [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-beta) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientAuthentication | [oidcClientAuthentication](https://learn.microsoft.com/en-us/graph/api/resources/oidcclientauthentication?view=graph-rest-beta) | The client authentication settings.<br><br>- Use the **oidcClientSecretAuthentication** derived complex type for setting up your identity provider with `client_secret_post` or `client_secret_jwt authentication` methods.<br>- Use the **oidcPrivateJwtKeyClientAuthentication** type for setting up your identity provider with `private_key_jwt` authentication method.  <br>    <br>  Due to security reasons, `client_secret_basic` authentication method isn't supported. |
| clientId | String | The client ID for the application obtained when registering the application with the identity provider. |
| displayName | String | The display name of the identity provider. Inherited from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-beta). |
| id | String | The identifier of the identity provider.Required. Inherited from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-beta). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| inboundClaimMapping | [oidcInboundClaimMappingOverride](https://learn.microsoft.com/en-us/graph/api/resources/oidcinboundclaimmappingoverride?view=graph-rest-beta) | After the OIDC provider sends an ID token back to Microsoft Entra External ID, Microsoft Entra External ID needs to be able to map the claims from the received token to the claims that Microsoft Entra ID recognizes and uses. This complex type captures that mapping. |
| issuer | String | The issuer URI. Issuer URI is a case-sensitive URL using https scheme contains scheme, host, and optionally, port number and path components and no query or fragment components.  <br>**Note:** Configuring other Microsoft Entra tenants as an external identity provider is currently not supported. As a result, the `microsoftonline.com` domain in the issuer URI is not accepted. |
| responseType | oidcResponseType | The response type describes the type of information sent back in the initial call to the authorization\_endpoint of the custom identity provider. Possible values:<br><br>- `code`: As per the authorization code flow, a code is returned back to Entra External ID. Entra External ID proceeds to call the token\_endpoint to exchange the code for the token.<br>- `id_token`: An ID token is returned back to Entra External ID from the custom identity provider. \(This value is not supported at the moment\).<br>- `token`: An access token is returned back to Entra External ID from the custom identity provider. This value is currently unsupported. |
| scope | String | Scope defines the information and permissions you are looking to gather from your custom identity provider. |
| wellKnownEndpoint | String | The URL for the metadata document of the OpenID Connect identity provider. Every OpenID Connect identity provider describes a metadata document that contains most of the information required to perform sign-in. This includes information such as the URLs to use and the location of the service's public signing keys. The OpenID Connect metadata document is always located at an endpoint that ends in `.well-known/openid-configuration`.  <br>**Note:** The metadata document should, at minimum, contain the following properties: `issuer`, `authorization_endpoint`, `token_endpoint`, `token_endpoint_auth_methods_supported`, `response_types_supported`, `subject_types_supported` and `jwks_uri`. Visit [OpenID Connect Discovery](https://openid.net/specs/openid-connect-discovery-1_0.html) specifications for more details. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.oidcIdentityProvider",
  "id": "String (identifier)",
  "displayName": "String",
  "supportedTenantTypes": "String",
  "clientId": "String",
  "issuer": "String",
  "wellKnownEndpoint": "String",
  "responseType": "String",
  "scope": "String",
  "clientAuthentication": {
    "@odata.type": "microsoft.graph.oidcClientAuthentication"
  },
  "inboundClaimMapping": {
    "@odata.type": "microsoft.graph.oidcInboundClaimMappingOverride"
  }
}
```
