<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# authenticationStrengthPolicy resource type

Namespace: microsoft.graph

A collection of settings that define specific combinations of authentication methods and metadata. The authentication strength policy, when applied to a given scenario using Microsoft Entra Conditional Access, defines which authentication methods must be used to authenticate in that scenario. An authentication strength may be built-in or custom \(defined by the tenant\) and may or may not fulfill the requirements to grant an MFA claim.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthroot-list-policies?view=graph-rest-1.0) | [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) collection | Get a list of the [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthroot-post-policies?view=graph-rest-1.0) | [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) | Create a new custom [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthpolicy-get?view=graph-rest-1.0) | [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) | Read the properties and relationships of an [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthpolicy-update?view=graph-rest-1.0) | [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) | Update the properties of a custom [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) object. You can't update a built-in **authenticationStrengthPolicy** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthroot-delete-policies?view=graph-rest-1.0) | None | Delete a custom [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) object. You can't delete a built-in **authenticationStrengthPolicy** object. |
| [List usage](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthpolicy-usage?view=graph-rest-1.0) | [authenticationStrengthUsage](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthusage?view=graph-rest-1.0) | Find all [conditionalAccessPolicies](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0) that reference an authentication strength. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedCombinations | [authenticationMethodModes](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodmodes?view=graph-rest-1.0) collection | A collection of authentication method modes that are required be used to satify this authentication strength. |
| createdDateTime | DateTimeOffset | The datetime when this policy was created. |
| description | String | The human-readable description of this policy. |
| displayName | String | The human-readable display name of this policy.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `not` , and `in`\). |
| id | String | The system-generated identifier for this mode. |
| modifiedDateTime | DateTimeOffset | The datetime when this policy was last modified. |
| policyType | authenticationStrengthPolicyType | A descriptor of whether this policy is built into Microsoft Entra ID or created by an admin for the tenant. The possible values are: `builtIn`, `custom`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`, `ne`, `not` , and `in`\). |
| requirementsSatisfied | authenticationStrengthRequirements | A descriptor of whether this authentication strength grants the MFA claim upon successful satisfaction. The possible values are: `none`, `mfa`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| combinationConfigurations | [authenticationCombinationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/authenticationcombinationconfiguration?view=graph-rest-1.0) collection | Settings that may be used to require specific types or instances of an authentication method to be used when authenticating with a specified combination of authentication methods. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationStrengthPolicy",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "modifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "description": "String",
  "policyType": "String",
  "requirementsSatisfied": "String",
  "allowedCombinations": [
    "String"
  ]
}
```
