<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/socialidentitysource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# socialIdentitySource resource type

Namespace: microsoft.graph

Used in the identity sources of an [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0). The `@odata.type` value `#microsoft.graph.socialIdentitySource` identifies a social identity as an identity source for a connected organization.

Inherits from [identitySource](https://learn.microsoft.com/en-us/graph/api/resources/identitysource?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the identity source. Typically the same value as the **socialIdentitySourceType**. |
| socialIdentitySourceType | [microsoft.graph.socialIdentitySourceType](https://learn.microsoft.com/en-us/graph/api/resources/socialidentitysource?view=graph-rest-1.0) | The possible values are: `facebook`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.socialIdentitySourceType",
  "displayName": "String",
  "socialIdentitySourceType": "String"
}
```
