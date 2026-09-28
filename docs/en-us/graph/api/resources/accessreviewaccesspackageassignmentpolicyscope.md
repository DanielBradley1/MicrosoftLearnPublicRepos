<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewaccesspackageassignmentpolicyscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# accessReviewAccessPackageAssignmentPolicyScope resource type

Namespace: microsoft.graph

The **accessReviewAccessPackageAssignmentPolicyScope** object defines the scope of the resource in an [access review](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-1.0) when the review is an access package assignment review.

Inherits from [accessReviewResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewresourcescope?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessPackageDisplayName | String | The display name of the access package. |
| accessPackageId | String | The access package identifier. |
| catalogDisplayName | String | The display name of the catalog. |
| catalogId | String | The catalog identifier. |
| displayName | String | The display name of the access package. Inherited from [accessReviewResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewresourcescope?view=graph-rest-1.0). |
| resourceId | String | The identifier of the access package assignment policy. Inherited from [accessReviewResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewresourcescope?view=graph-rest-1.0). |
| scopeType | accessReviewResourceScopeType | The scope type. Inherited from [accessReviewResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewresourcescope?view=graph-rest-1.0). The value is `accessPackageAssignmentPolicy`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewAccessPackageAssignmentPolicyScope",
  "resourceId": "String",
  "scopeType": "String",
  "displayName": "String",
  "accessPackageId": "String",
  "accessPackageDisplayName": "String",
  "catalogId": "String",
  "catalogDisplayName": "String"
}
```
