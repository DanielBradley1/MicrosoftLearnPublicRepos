<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applemanagedidentityprovider?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# appleManagedIdentityProvider resource type

Namespace: microsoft.graph

Represents the Apple identity provider in an Azure AD B2C tenant.

You can configure Apple as a social identity provider for an Azure AD B2C tenant. Based on the information, Apple provides, the API generates a client secret. Apple needs the secret to be renewed every six months. You have to manually rotate the secret.

Inherits from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing Apple-managed identity providers, see the [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| certificateData | String | The certificate data, which is a long string of text from the certificate. Can be null. |
| developerId | String | The Apple developer identifier. Required. |
| displayName | String | The display name of the identity provider. Inherited from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0). |
| id | String | The identifier of the identity provider. Inherited from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0). Read-only. |
| keyId | String | The Apple key identifier. Required. |
| serviceId | String | The Apple service identifier. Required. |

Retrieve the **developerId**, **serviceId**, **keyId**, and the **certificateData** from the Apple developer portal. For more information, follow the guide to [create an Apple ID application](https://learn.microsoft.com/en-us/azure/active-directory-b2c/identity-provider-apple-id?pivots=b2c-user-flow#create-an-apple-id-application).

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "certificateData": "String",
    "displayName": "String",
    "developerId": "String",
    "id": "String",
    "keyId": "String",
    "serviceId": "String"
}
```
