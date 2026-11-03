<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/voiceauthenticationmethodconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# voiceAuthenticationMethodConfiguration resource type

Namespace: microsoft.graph

Represents a voice call authentication methods policy. Authentication methods policies define configuration settings and users or groups that are enabled to use the authentication method.

Inherits from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/voiceauthenticationmethodconfiguration-get?view=graph-rest-1.0) | [voiceAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/voiceauthenticationmethodconfiguration?view=graph-rest-1.0) | Read the properties and relationships of a [voiceAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/voiceauthenticationmethodconfiguration?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/voiceauthenticationmethodconfiguration-update?view=graph-rest-1.0) | None | Update the properties of a [voiceAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/voiceauthenticationmethodconfiguration?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/voiceauthenticationmethodconfiguration-delete?view=graph-rest-1.0) | None | Revert the [voiceAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/voiceauthenticationmethodconfiguration?view=graph-rest-1.0) object to its default configuration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups of users that are excluded from the policy. |
| id | String | The authentication method policy identifier. |
| isOfficePhoneAllowed | Boolean | `true` if users can register office phones, otherwise, `false`. |
| state | authenticationMethodState | Represents whether users can register this authentication method. The possible values are: `enabled`, `disabled`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includeTargets | [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-1.0) collection | A collection of groups that are enabled to use the authentication method. Expanded by default. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.voiceAuthenticationMethodConfiguration",
  "id": "String (identifier)",
  "state": "String",
  "excludeTargets": [
    {
      "@odata.type": "microsoft.graph.excludeTarget"
    }
  ],
  "isOfficePhoneAllowed": "Boolean"
}
```
