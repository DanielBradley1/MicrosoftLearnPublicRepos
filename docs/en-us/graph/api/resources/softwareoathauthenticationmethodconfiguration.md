<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/softwareoathauthenticationmethodconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# softwareOathAuthenticationMethodConfiguration resource type

Namespace: microsoft.graph

Represents the authentication policy for a third-party software OATH authentication method. Authentication methods policies define configuration settings and users or groups that are enabled to use the authentication method.

Inherits from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/softwareoathauthenticationmethodconfiguration-get?view=graph-rest-1.0) | [softwareOathAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/softwareoathauthenticationmethodconfiguration?view=graph-rest-1.0) | Read the properties and relationships of a [softwareOathAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/softwareoathauthenticationmethodconfiguration?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/softwareoathauthenticationmethodconfiguration-update?view=graph-rest-1.0) | None | Update the properties of a [softwareOathAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/softwareoathauthenticationmethodconfiguration?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/softwareoathauthenticationmethodconfiguration-delete?view=graph-rest-1.0) | None | Reverts the [softwareOathAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/softwareoathauthenticationmethodconfiguration?view=graph-rest-1.0) object to its default configuration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups of users that are excluded from the policy. |
| id | String | The authentication method policy identifier. |
| state | authenticationMethodState | Represents whether users can register this authentication method. The possible values are: `enabled`, `disabled`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includeTargets | [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-1.0) collection | A collection of groups that are enabled to use the authentication method. Expanded by default. |

The following JSON representation shows the resource type. The following is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.softwareOathAuthenticationMethodConfiguration",
  "id": "String (identifier)",
  "state": "String",
  "excludeTargets": [
    {
      "@odata.type": "microsoft.graph.excludeTarget"
    }
  ]
}
```
