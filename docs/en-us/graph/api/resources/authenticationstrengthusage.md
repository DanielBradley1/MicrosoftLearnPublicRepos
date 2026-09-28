<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationstrengthusage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# authenticationStrengthUsage resource type

Namespace: microsoft.graph

An object containing two collections of Conditional Access policies that reference the specified authentication strength. One collection references Conditional Access policies that require an MFA claim; the other collection references Conditional Access policies that don't require such a claim.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| mfa | conditionalAccessPolicy collection | A collection of Conditional Access policies that reference the specified authentication strength policy and that require an MFA claim. |
| none | conditionalAccessPolicy collection | A collection of Conditional Access policies that reference the specified authentication strength policy and that do not require an MFA claim. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| mfa | [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0) collection | A collection of Conditional Access policies that reference the specified authentication strength policy and that require an MFA claim. |
| none | [conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicy?view=graph-rest-1.0) collection | A collection of Conditional Access policies that reference the specified authentication strength policy and that *do not* require an MFA claim. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationStrengthUsage",
  "mfa": ["String"],
  "none": ["String"]
}
```
