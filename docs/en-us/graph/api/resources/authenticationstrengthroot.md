<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# authenticationStrengthRoot resource type

Namespace: microsoft.graph

The **authenticationStrengthRoot** resource is the entry point for the authentication strengths object model.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authenticationCombinations | [authenticationMethodModes](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodmodes?view=graph-rest-1.0) collection | A collection of all valid authentication method combinations in the system. |
| id | String | A system-generated identifier. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authenticationMethodModes | [authenticationMethodModeDetail](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethodmodedetail?view=graph-rest-1.0) collection | Names and descriptions of all valid authentication method modes in the system. |
| policies | [authenticationStrengthPolicy](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) collection | A collection of [authentication strength policies](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) that exist for this tenant, including both built-in and custom policies. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationStrengthRoot",
  "id": "String (identifier)",
  "authenticationCombinations": [
    "String"
  ]
}
```
