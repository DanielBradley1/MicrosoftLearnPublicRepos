<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/smsauthenticationmethodconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# smsAuthenticationMethodConfiguration resource type

Namespace: microsoft.graph

Represents a text message authentication methods policy. Authentication methods policies define configuration settings and users or groups that are enabled to use the authentication method.

Inherits from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/smsauthenticationmethodconfiguration-get?view=graph-rest-1.0) | [smsAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/smsauthenticationmethodconfiguration?view=graph-rest-1.0) | Read the properties and relationships of an smsAuthenticationMethodConfiguration object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/smsauthenticationmethodconfiguration-update?view=graph-rest-1.0) | None | Update the properties of an smsAuthenticationMethodConfiguration object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/smsauthenticationmethodconfiguration-delete?view=graph-rest-1.0) | None | Reverts the smsAuthenticationMethodConfiguration object to its default configuration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups of users that are excluded from the policy. |
| id | String | The authentication method policy identifier. |
| state | authenticationMethodState | The possible values are: `enabled`, `disabled`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includeTargets | [smsAuthenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/smsauthenticationmethodtarget?view=graph-rest-1.0) collection | A collection of groups that are enabled to use the authentication method. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.smsAuthenticationMethodConfiguration",
  "id": "String (identifier)",
  "state": "String",
  "excludeTargets": [
    {
      "@odata.type": "microsoft.graph.excludeTarget"
    }
  ]
}
```
