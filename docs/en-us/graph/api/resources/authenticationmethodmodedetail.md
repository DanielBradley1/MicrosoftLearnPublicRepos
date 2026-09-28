<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodmodedetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-13 -->

# authenticationMethodModeDetail resource type

Namespace: microsoft.graph

The details of the **authenticationMethodModes** objects that can be defined for the **allowedCombinations** property of the [authenticationstrengthpolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0).

For more information on authentication methods, see the [authentication methods overview](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethods-overview?view=graph-rest-1.0)

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List authentication combinations and method modes](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthroot-list-authenticationmethodmodes?view=graph-rest-1.0) | [authenticationMethodModeDetail](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodmodedetail?view=graph-rest-1.0) collection | Get a list of the [authenticationMethodModeDetail](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodmodedetail?view=graph-rest-1.0) objects and their properties. |
| [Get authentication method modes](https://learn.microsoft.com/en-us/graph/api/authenticationmethodmodedetail-get?view=graph-rest-1.0) | [authenticationMethodModeDetail](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodmodedetail?view=graph-rest-1.0) | Read the properties and relationships of an [authenticationMethodModeDetail](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodmodedetail?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationMethod | [baseAuthenticationMethod](https://learn.microsoft.com/en-us/graph/api/resources/baseauthenticationmethod?view=graph-rest-1.0) | The authentication method that this mode modifies. |
| displayName | String | The display name of this mode |
| id | String | The system-generated identifier for this mode. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationMethodModeDetail",
  "id": "String (identifier)",
  "displayName": "String",
  "authenticationMethod": "String"
}
```
