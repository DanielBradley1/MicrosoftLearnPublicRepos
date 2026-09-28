<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewprincipalscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# accessReviewPrincipalScope resource type

Namespace: microsoft.graph

An **accessReviewPrincipalScope** object defines the type of users to include in an [access review](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-1.0), without writing a query expression.

Use it in the **principalScopes** collection of a [principalResourceMembershipsScope](https://learn.microsoft.com/en-us/graph/api/resources/principalresourcemembershipsscope?view=graph-rest-1.0) object to state which population of principals has its access reviewed.

Inherits from [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| scopeType | accessReviewPrincipalScopeType | The type of users to include in the review. The possible values are: `allUsers`, `guestUsers`, `inactiveUsers`, `inactiveGuestUsers`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewPrincipalScope",
  "scopeType": "String"
}
```
