<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialsauthenticationmethodconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-15 -->

# verifiableCredentialsAuthenticationMethodConfiguration resource type

Namespace: microsoft.graph

Represents a Verifiable Credential authentication methods policy. Authentication methods policies define configuration settings and users or groups who are enabled to use the authentication method.

Inherits from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/verifiablecredentialsauthenticationmethodconfiguration-list?view=graph-rest-1.0) | [verifiableCredentialsAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialsauthenticationmethodconfiguration?view=graph-rest-1.0) collection | Get a list of the verifiableCredentialsAuthenticationMethodConfiguration objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/verifiablecredentialsauthenticationmethodconfiguration-get?view=graph-rest-1.0) | [verifiableCredentialsAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialsauthenticationmethodconfiguration?view=graph-rest-1.0) | Read the properties and relationships of [verifiableCredentialsAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialsauthenticationmethodconfiguration?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/verifiablecredentialsauthenticationmethodconfiguration-update?view=graph-rest-1.0) | None | Update the properties of a verifiableCredentialsAuthenticationMethodConfiguration object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/verifiablecredentialsauthenticationmethodconfiguration-delete?view=graph-rest-1.0) | None | Delete a verifiableCredentialsAuthenticationMethodConfiguration object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups of users that are excluded from the policy. Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0). |
| id | String | The authentication method policy identifier. |
| state | authenticationMethodState | Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0). The possible values are: `enabled`, `disabled`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includeTargets | [verifiableCredentialAuthenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/verifiablecredentialauthenticationmethodtarget?view=graph-rest-1.0) collection | A collection of groups that are enabled to use the authentication method. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.verifiableCredentialsAuthenticationMethodConfiguration",
  "id": "String (identifier)",
  "state": "String",
  "excludeTargets": [
    {
      "@odata.type": "microsoft.graph.excludeTarget"
    }
  ]
}
```
