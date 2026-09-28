<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/openidconnectidentityprovider?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-01-11 -->

# openIdConnectIdentityProvider resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents OpenID Connect identity providers in an Azure Active Directory \(Azure AD\) B2C tenant.

Configuring an OpenID Connect provider in an Azure AD B2C tenant enables users to sign up and sign in to any application using their custom identity provider.

Inherits from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-beta).

For more information, see [Add Azure AD B2C tenant as an OpenID Connect identity provider \(preview\)](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-b2c-federation-customers).

## Methods

None.

For the list of API operations for managing OpenID Connect identity providers in Azure AD B2C, see the [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-beta) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientId | String | The client identifier for the application obtained when registering the application with the identity provider. Required. |
| clientSecret | String | The client secret for the application obtained when registering the application with the identity provider. The clientSecret has a dependency on **responseType**.<br><br>- When **responseType** is `code`, a secret is required for the auth code exchange.<br>- When **responseType** is `id_token`, the secret isn't required because there's no code exchange. The id\_token is returned directly from the authorization response.<br><br>This is write-only. A read operation returns `****`. |
| id | String | The identifier of the identity provider.Required. Inherited from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-beta). Read-only. |
| displayName | String | The display name of the identity provider. |
| claimsMapping | [claimsMapping](https://learn.microsoft.com/en-us/graph/api/resources/claimsmapping?view=graph-rest-beta) | After the OIDC provider sends an ID token back to Microsoft Entra ID, Microsoft Entra ID needs to be able to map the claims from the received token to the claims that Microsoft Entra ID recognizes and uses. This complex type captures that mapping. Required. |
| domainHint | String | The domain hint can be used to skip directly to the sign-in page of the specified identity provider instead of having the user make a selection among the list of available identity providers. |
| metadataUrl | String | The URL for the metadata document of the OpenID Connect identity provider. Every OpenID Connect identity provider describes a metadata document that contains most of the information required to perform sign-in. This includes information such as the URLs to use and the location of the service's public signing keys. The OpenID Connect metadata document is always located at an endpoint that ends in `.well-known/openid-configuration`. Provide the metadata URL for the OpenID Connect identity provider you add. Read-only. Required. |
| responseMode | [openIdConnectResponseMode](#openidconnectresponsemode-values) | The response mode defines the method used to send data back from the custom identity provider to Azure AD B2C. Possible values: `form_post`, `query`. Required. |
| responseType | [openIdConnectResponseTypes](#openidconnectresponsetypes-values) | The response type describes the type of information sent back in the initial call to the authorization\_endpoint of the custom identity provider. Possible values: `code` , `id_token` , `token`. Required. |
| scope | String | Scope defines the information and permissions you're looking to gather from your custom identity provider. OpenID Connect requests must contain the openid scope value in order to receive the ID token from the identity provider. Without the ID token, users aren't able to sign in to Azure AD B2C using the custom identity provider. Other scopes can be appended, separated by a space. For more information about the scope limitations, see [RFC6749 Section 3.3](https://tools.ietf.org/html/rfc6749#section-3.3). Required. |

### openIdConnectResponseMode values

| Member | Description |
| :--- | :--- |
| form\_post | This response mode is recommended for best security. The response is transmitted via the HTTP POST method, with the code or token being encoded in the body using the application/x-www-form-urlencoded format. |
| query | The code or token is returned as a query parameter. |
| unknownFutureValue | A sentinel value to indicate future values. |

### openIdConnectResponseTypes values

| Member | Description |
| :--- | :--- |
| code | As per the authorization code flow, a code is returned back to Azure AD B2C. Azure AD B2C proceeds to call the token\_endpoint to exchange the code for the token. |
| id\_token | An ID token is returned back to Azure AD B2C from the custom identity provider. |
| token | An access token is returned back to Azure AD B2C from the custom identity provider. \(This value isn't supported by Azure AD B2C at the moment\) |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.openIdConnectIdentityProvider",
  "id": "String (identifier)",
  "displayName": "String",
  "clientId": "String",
  "clientSecret": "String",
  "scope": "String",
  "metadataUrl": "String",
  "domainHint": "String",
  "responseType": "String",
  "responseMode": "String",
  "claimsMapping": {
    "@odata.type": "microsoft.graph.claimsMapping"
  }
}
```
