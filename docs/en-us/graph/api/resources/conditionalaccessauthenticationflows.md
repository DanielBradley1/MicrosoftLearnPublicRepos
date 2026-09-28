<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessauthenticationflows?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-04 -->

# conditionalAccessAuthenticationFlows resource type

Namespace: microsoft.graph

Represents the authentication flows in scope for the policy.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| transferMethods | conditionalAccessTransferMethods | Represents the transfer methods in scope for the policy. The possible values are: `none`, `deviceCodeFlow`, `authenticationTransfer`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "transferMethods": "String",
}
```
