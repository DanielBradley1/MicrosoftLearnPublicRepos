<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewresourcescope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# accessReviewResourceScope resource type

Namespace: microsoft.graph

An **accessReviewResourceScope** object defines the type of resource that users have access to in an [access review](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-1.0).

Use it in the **resourceScopes** collection of a [principalResourceMembershipsScope](https://learn.microsoft.com/en-us/graph/api/resources/principalresourcemembershipsscope?view=graph-rest-1.0) object to identify the resource whose access is reviewed.

Inherits from [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0).

This type is inherited by [accessReviewAccessPackageAssignmentPolicyScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewaccesspackageassignmentpolicyscope?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the resource. |
| resourceId | String | The identifier of the resource. |
| scopeType | accessReviewResourceScopeType | The type of the resource. The possible values are: `group`, `catalog`, `servicePrincipal`, `directoryRole`, `accessPackageAssignmentPolicy`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewResourceScope",
  "resourceId": "String",
  "scopeType": "String",
  "displayName": "String"
}
```
