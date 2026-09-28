<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessexternaltenants?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# conditionalAccessExternalTenants resource type

Namespace: microsoft.graph

An abstract type that represents external tenants in a policy scope.

Base type of [conditionalAccessAllExternalTenants](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessallexternaltenants?view=graph-rest-1.0) and [conditionalAccessEnumeratedExternalTenants](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessenumeratedexternaltenants?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| membershipKind | conditionalAccessExternalTenantsMembershipKind | The membership kind. The possible values are: `all`, `enumerated`, `unknownFutureValue`. The `enumerated` member references an [conditionalAccessEnumeratedExternalTenants](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessenumeratedexternaltenants?view=graph-rest-1.0) object. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conditionalAccessExternalTenants",
  "membershipKind": "String"
}
```
