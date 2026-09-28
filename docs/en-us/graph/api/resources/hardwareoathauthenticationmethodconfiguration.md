<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathauthenticationmethodconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-10-01 -->

# hardwareOathAuthenticationMethodConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Hardware OATH authentication method policy. Authentication method policies define configuration settings and users or groups that are enabled to use the authentication method.

Inherits from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/hardwareoathauthenticationmethodconfiguration-get?view=graph-rest-beta) | [hardwareOathAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathauthenticationmethodconfiguration?view=graph-rest-beta) | Read the properties and relationships of a [hardwareOathAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathauthenticationmethodconfiguration?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/hardwareoathauthenticationmethodconfiguration-update?view=graph-rest-beta) | [hardwareOathAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathauthenticationmethodconfiguration?view=graph-rest-beta) | Update the properties of a [hardwareOathAuthenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathauthenticationmethodconfiguration?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/hardwareoathauthenticationmethodconfiguration-delete?view=graph-rest-beta) | None | Reverts the hardwareOathAuthenticationMethodConfiguration object to its default configuration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-beta) collection | Groups of users that are excluded from the policy. Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-beta). |
| id | String | The authentication method policy identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| state | authenticationMethodState | The possible values are: `enabled`, `disabled`. Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includeTargets | [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-beta) collection | A collection of groups that are enabled to use the authentication method. Expanded by default. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.hardwareOathAuthenticationMethodConfiguration",
  "id": "String (identifier)",
  "state": "String",
  "excludeTargets": [
    {
      "@odata.type": "microsoft.graph.excludeTarget"
    }
  ]
}
```
