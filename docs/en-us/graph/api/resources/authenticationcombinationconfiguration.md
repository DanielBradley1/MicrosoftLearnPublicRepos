<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# authenticationCombinationConfiguration resource type

Namespace: microsoft.graph

Sets restrictions on specific types, modes, or versions of an authentication method that is tied to specific auth method combinations used in an [authentication strength](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengths-overview?view=graph-rest-1.0).

The following resources inherit from this abstract type and define the various types of combination configurations:

- [fido2combinationConfigurations](https://learn.microsoft.com/en-us/graph/api/resources/fido2combinationconfiguration?view=graph-rest-1.0)
- [x509certificatecombinationconfiguration](https://learn.microsoft.com/en-us/graph/api/resources/x509certificatecombinationconfiguration?view=graph-rest-1.0)

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthpolicy-list-combinationconfigurations?view=graph-rest-1.0) | [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0) collection | Get a list of the [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthpolicy-post-combinationconfigurations?view=graph-rest-1.0) | [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0) | Create a new [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0) |
| [Get](https://learn.microsoft.com/en-us/graph/api/authenticationcombinationconfiguration-get?view=graph-rest-1.0) | [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0) | Read the properties and relationships of a [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/authenticationcombinationconfiguration-update?view=graph-rest-1.0) | [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0) | Update the properties of an [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthpolicy-delete-combinationconfigurations?view=graph-rest-1.0) | None | Delete an [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0) object. |
| [Update allowed combinations](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthpolicy-updateallowedcombinations?view=graph-rest-1.0) | [updateAllowedCombinationsResult](https://learn.microsoft.com/en-us/graph/api/resources/updateallowedcombinationsresult?view=graph-rest-1.0) | Update the allowed [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0) for a given [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| appliesToCombinations | authenticationMethodModes collection | Which authentication method combinations this configuration applies to. Must be an **allowedCombinations** object, part of the [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0). The only possible value for `fido2combinationConfigurations` is `"fido2"`. |
| id | String | A unique system-generated identifier. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationCombinationConfiguration",
  "id": "String (identifier)",
  "appliesToCombinations": [
    "String"
  ]
}
```
