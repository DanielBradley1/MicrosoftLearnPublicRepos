<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethodconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# temporaryAccessPassAuthenticationMethodConfiguration resource type

Namespace: microsoft.graph

Represents a Temporary Access Pass authentication methods policy that defines the configuration settings and users or groups who are enabled to use the [Temporary Access Pass authentication method](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethod?view=graph-rest-1.0).

Inherits from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/temporaryaccesspassauthenticationmethodconfiguration-get?view=graph-rest-1.0) | [temporaryaccesspassauthenticationmethodconfiguration](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethodconfiguration?view=graph-rest-1.0) | Read the properties and relationships of a **temporaryAccessPassAuthenticationMethodConfiguration** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/temporaryaccesspassauthenticationmethodconfiguration-update?view=graph-rest-1.0) | None | Update the properties of a **temporaryAccessPassAuthenticationMethodConfiguration** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/temporaryaccesspassauthenticationmethodconfiguration-delete?view=graph-rest-1.0) | None | Reverts the **temporaryAccessPassAuthenticationMethodConfiguration** object to its default configuration. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultLength | Int | Default length in characters of a Temporary Access Pass object. Must be between 8 and 48 characters. |
| defaultLifetimeInMinutes | Int | Default lifetime in minutes for a Temporary Access Pass. Value can be any integer between the **minimumLifetimeInMinutes** and **maximumLifetimeInMinutes**. |
| excludeTargets | [excludeTarget](https://learn.microsoft.com/en-us/graph/api/resources/excludetarget?view=graph-rest-1.0) collection | Groups of users that are excluded from the policy. |
| id | String | The identifier of the authentication method policy. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| isUsableOnce | Boolean | If `true`, all the passes in the tenant will be restricted to one-time use. If `false`, passes in the tenant can be created to be either one-time use or reusable. |
| maximumLifetimeInMinutes | Int | Maximum lifetime in minutes for any Temporary Access Pass created in the tenant. Value can be between 10 and 43200 minutes \(equivalent to 30 days\). |
| minimumLifetimeInMinutes | Int | Minimum lifetime in minutes for any Temporary Access Pass created in the tenant. Value can be between 10 and 43200 minutes \(equivalent to 30 days\). |
| state | authenticationMethodState | Whether the Temporary Access Pass method is enabled in the tenant. The possible values are: `enabled`, `disabled`. Inherited from [authenticationMethodConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodconfiguration?view=graph-rest-1.0). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| includeTargets | [authenticationMethodTarget](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodtarget?view=graph-rest-1.0) collection | A collection of groups that are enabled to use the authentication method. |

The following JSON representation shows the resource type. The following is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.temporaryAccessPassAuthenticationMethodConfiguration",
  "id": "String (identifier)",
  "state": "String",
    "excludeTargets": [
    {
      "@odata.type": "microsoft.graph.excludeTarget"
    }
  ],
  "defaultLifetimeInMinutes": "Integer",
  "defaultLength": "Integer",
  "minimumLifetimeInMinutes": "Integer",
  "maximumLifetimeInMinutes": "Integer",
  "isUsableOnce": "Boolean",
  "includeTargets": [ { "@odata.type": "microsoft.graph.authenticationMethodTarget" } ]
}
```
