<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessenumeratedexternaltenants?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# conditionalAccessEnumeratedExternalTenants resource type

Namespace: microsoft.graph

Represents a list of external tenants in a policy scope.

Inherits from [conditionalAccessExternalTenants](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessexternaltenants?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| members | String collection | A collection of tenant IDs that define the scope of a policy targeting conditional access for guests and external users. |
| membershipKind | conditionalAccessExternalTenantsMembershipKind | The membership kind. The possible values are: `all`, `enumerated`, `unknownFutureValue`. The `enumerated` member references an [conditionalAccessEnumeratedExternalTenants](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessenumeratedexternaltenants?view=graph-rest-1.0) object. Inherited from [conditionalAccessExternalTenants](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessexternaltenants?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conditionalAccessEnumeratedExternalTenants",
  "members": ["String"],
  "membershipKind": "String"
}
```
