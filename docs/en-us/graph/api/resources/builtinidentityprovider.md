<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/builtinidentityprovider?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-23 -->

# builtInIdentityProvider resource type

Namespace: microsoft.graph

Represents built-in identity providers for a Microsoft Entra tenant.

For Microsoft Entra B2B scenarios in a Microsoft Entra tenant, the built-in identity provider type can be a Microsoft Entra ID, Microsoft account\(MSA\) or email one-time passcode \(EmailOTP\).

This type inherits from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0).

## Methods

None.

For the list of API operations for managing built-in identity providers, see the [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0) resource type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the identity provider. Inherited from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0). |
| id | String | The identifier of the identity provider. Inherited from [identityProviderBase](https://learn.microsoft.com/en-us/graph/api/resources/identityproviderbase?view=graph-rest-1.0). Read-only. |
| identityProviderType | String | The identity provider type. For a B2B scenario, possible values: `AADSignup`, `MicrosoftAccount`, `EmailOTP`. Required. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "displayName": "String",
    "id": "String",
    "identityProviderType": "String"
}
```
