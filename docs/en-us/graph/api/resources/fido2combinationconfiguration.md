<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/fido2combinationconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-19 -->

# fido2CombinationConfiguration resource type

Namespace: microsoft.graph

Configuration to require specific FIDO2 keys in an authentication strength. Use this entity to specify which Authenticator Attestation GUIDs \(AAGUIDs\) are allowed, as part of certain authentication method combinations, in an [authentication strength](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0).

Inherits and derived from [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAAGUIDs | String collection | A list of AAGUIDs allowed to be used as part of the specified authentication method combinations. |
| appliesToCombinations | authenticationMethodModes collection | Which authentication method combinations this configuration applies to. The only possible value is `"fido2"`. Inherited from [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0). |
| id | String | A system-generated identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.fido2CombinationConfiguration",
  "id": "String (identifier)",
  "appliesToCombinations": [
    "String"
  ],
  "allowedAAGUIDs": [
    "String"
  ]
}
```
