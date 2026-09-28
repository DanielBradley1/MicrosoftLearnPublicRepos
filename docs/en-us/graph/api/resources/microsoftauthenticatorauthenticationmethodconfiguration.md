<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethodconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# microsoftAuthenticatorAuthenticationMethodConfiguration resource type

Namespace: microsoft.graph

Represents a Microsoft Authenticator authentication methods policy. Authentication methods policies define configuration settings and users or groups that are enabled to use the authentication method.

Inherits from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/microsoftauthenticatorauthenticationmethodconfiguration-get?view=graph-rest-1.0) | [microsoftAuthenticatorAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethodconfiguration?view=graph-rest-1.0) | Read the properties and relationships of a microsoftAuthenticatorAuthenticationMethodConfiguration object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/microsoftauthenticatorauthenticationmethodconfiguration-update?view=graph-rest-1.0) | [microsoftAuthenticatorAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethodconfiguration?view=graph-rest-1.0) | Update the properties of a microsoftAuthenticatorAuthenticationMethodConfiguration object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/microsoftauthenticatorauthenticationmethodconfiguration-delete?view=graph-rest-1.0) | None | Reverts the microsoftAuthenticatorAuthenticationMethodConfiguration object to its default configuration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups of users that are excluded from the policy. |
| id | String | The authentication method policy identifier. |
| featureSettings | [microsoftAuthenticatorFeatureSettings](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorfeaturesettings?view=graph-rest-1.0) | A collection of Microsoft Authenticator settings such as application context and location context, and whether they are enabled for all users or specific users only. |
| state | authenticationMethodState | The possible values are: `enabled`, `disabled`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includeTargets | [microsoftAuthenticatorAuthenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/microsoftauthenticatorauthenticationmethodtarget?view=graph-rest-1.0) collection | A collection of groups that are enabled to use the authentication method. Expanded by default. |

The following JSON representation shows the resource type. The following is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.microsoftAuthenticatorAuthenticationMethodConfiguration",
  "id": "String (identifier)",
  "state": "String",
  "excludeTargets": [
    {
      "@odata.type": "microsoft.graph.excludeTarget"
    }
  ],
  "featureSettings": {
    "@odata.type": "microsoft.graph.microsoftAuthenticatorFeatureSettings"
  }
}
```
