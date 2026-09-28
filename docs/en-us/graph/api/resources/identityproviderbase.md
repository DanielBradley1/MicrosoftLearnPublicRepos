<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-23 -->

# identityProviderBase resource type

Namespace: microsoft.graph

Represents identity providers with [External Identities](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/) for both Microsoft Entra ID and Azure AD B2C tenants.

For Microsoft Entra B2B scenarios in a Microsoft Entra directory, the identity provider can be a [socialIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider?view=graph-rest-1.0) or a [builtinIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/builtinidentityprovider?view=graph-rest-1.0), both of which inherit from the identityProviderBase resource type.

Configuring an identity provider in your Microsoft Entra directory enables new Microsoft Entra B2B guest scenarios. For example, an organization has resources in Microsoft 365 that need to be shared with a Gmail user. The Gmail user will use their Google account credentials to authenticate and access the documents.

In an Azure AD B2C directory, the identity provider type can be a [socialIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider?view=graph-rest-1.0) or an [appleManagedIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/applemanagedidentityprovider?view=graph-rest-1.0), all which inherit from the identityProviderBase resource type.

Configuring an identity provider in your Azure AD B2C directory enables users to sign up and sign in using a social account or a custom OpenID Connect supported provider in an application. For example, an application can use Azure AD B2C to allow users to sign up for the service using a Facebook account or their own custom identity provider that complies with OIDC protocol.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List configured identity providers](https://learn.microsoft.com/en-us/graph/api/identitycontainer-list-identityproviders?view=graph-rest-1.0) | [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0) collection | Retrieve all identity providers configured in a tenant. |
| [Create identity provider](https://learn.microsoft.com/en-us/graph/api/identitycontainer-post-identityproviders?view=graph-rest-1.0) | [socialidentityprovider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider?view=graph-rest-1.0) or [appleManagedIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/applemanagedidentityprovider?view=graph-rest-1.0) | Create a new object of one of the following object types:  <br><br><br>- [socialidentityprovider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider?view=graph-rest-1.0) \(Microsoft Entra ID or Azure AD B2C\)<br>- [appleManagedIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/applemanagedidentityprovider?view=graph-rest-1.0) \(Azure AD B2C\) |
| [Get](https://learn.microsoft.com/en-us/graph/api/identityproviderbase-get?view=graph-rest-1.0) | [socialidentityprovider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider?view=graph-rest-1.0), [builtInIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/builtinidentityprovider?view=graph-rest-1.0) or [appleManagedIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/applemanagedidentityprovider?view=graph-rest-1.0) | Retrieve properties of one of the following object types:  <br><br><br>- [socialidentityprovider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider?view=graph-rest-1.0) \(Microsoft Entra ID or Azure AD B2C\)<br>- [builtInIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/builtinidentityprovider?view=graph-rest-1.0) \(Microsoft Entra ID or Azure AD B2C\)<br>- [appleManagedIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/applemanagedidentityprovider?view=graph-rest-1.0) \(Azure AD B2C\) |
| [Update](https://learn.microsoft.com/en-us/graph/api/identityproviderbase-update?view=graph-rest-1.0) | None | Update one of the following object types:  <br><br><br>- [socialidentityprovider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider?view=graph-rest-1.0) \(Microsoft Entra ID or Azure AD B2C\)<br>- [appleManagedIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/applemanagedidentityprovider?view=graph-rest-1.0) \(Azure AD B2C\) |
| [Delete](https://learn.microsoft.com/en-us/graph/api/identityproviderbase-delete?view=graph-rest-1.0) | None | Delete one of the following object types:  <br><br><br>- [socialidentityprovider](https://learn.microsoft.com/en-us/graph/api/resources/socialidentityprovider?view=graph-rest-1.0) \(Microsoft Entra ID or Azure AD B2C\)<br>- [appleManagedIdentityProvider](https://learn.microsoft.com/en-us/graph/api/resources/applemanagedidentityprovider?view=graph-rest-1.0) \(Azure AD B2C\) \(Azure AD B2C\) |
| [List available identity providers](https://learn.microsoft.com/en-us/graph/api/identityproviderbase-availableprovidertypes?view=graph-rest-1.0) | String collection | Retrieve all supported identity provider types in the tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the identity provider. |
| id | String | The identifier of the identity provider. |

## JSON representation

The following JSON representation shows the resource type. The following JSON representation shows the resource type.

```json
{
    "id": "String",
    "displayName": "String"
}
```
