<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationflow?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-28 -->

# authenticationFlow resource type

Namespace: microsoft.graph

Authentication flow used during the sign-in, as defined in [Conditional Access What If evaluation](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-evaluate?view=graph-rest-1.0). Contains properties for deviceCodeFlow and authenticationTransfer for admins to leverage when creating policies.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| transferMethod | conditionalAccessTransferMethods | Represents the transfer methods in scope for the policy. The possible values are: `none`, `deviceCodeFlow`, `authenticationTransfer`, `unknownFutureValue`. Default value is `none`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationFlow",
  "transferMethod": "String"
}
```
