<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/updateallowedcombinationsresult?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# updateAllowedCombinationsResult resource type

Namespace: microsoft.graph

The results of an attempt to update an authentication strength's [allowedCombinations](https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthpolicy?view=graph-rest-1.0) property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalInformation | String | Information about why the [updateAllowedCombinations](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthpolicy-updateallowedcombinations?view=graph-rest-1.0) action was successful or failed. |
| conditionalAccessReferences | String collection | References to existing Conditional Access policies that use this authentication strength. |
| currentCombinations | authenticationMethodModes collection | The list of current authentication method combinations allowed by the authentication strength. |
| previousCombinations | authenticationMethodModes collection | The list of former authentication method combinations allowed by the authentication strength before they were updated through the [updateAllowedCombinations](https://learn.microsoft.com/en-us/graph/api/authenticationstrengthpolicy-updateallowedcombinations?view=graph-rest-1.0) action. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.updateAllowedCombinationsResult",
  "previousCombinations": [
    "String"
  ],
  "currentCombinations": [
    "String"
  ],
  "conditionalAccessReferences": [
    "String"
  ],
  "additionalInformation": "String"
}
```
