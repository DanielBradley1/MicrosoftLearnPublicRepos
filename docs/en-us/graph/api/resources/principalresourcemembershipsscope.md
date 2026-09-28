<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/principalresourcemembershipsscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# principalResourceMembershipsScope resource type

Namespace: microsoft.graph

In an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0), the **scope** property can be configured with a **principalResourceMembershipsScope** object to review selected principals' access to selected resources.

Inherits from [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| principalScopes | [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0) collection | Defines the scopes of the principals whose access to resources are reviewed in the access review. Use an [accessReviewPrincipalScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewprincipalscope?view=graph-rest-1.0) object to select a well-known population of principals, such as all guest users. |
| resourceScopes | [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0) collection | Defines the scopes of the resources for which access is reviewed. Use an [accessReviewResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewresourcescope?view=graph-rest-1.0) object to identify the resource, or an [accessReviewAccessPackageAssignmentPolicyScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewaccesspackageassignmentpolicyscope?view=graph-rest-1.0) object when the resource is an access package assignment policy. |

You must also specify the **@odata.type** type property with the value `#microsoft.graph.principalResourceMembershipsScope`. For more about configuration options for **scope** using **principalResourceMembershipsScope**, see [Configure the scope of your access review definition using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/accessreviews-scope-concept).

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.principalResourceMembershipsScope",
  "principalScopes": [
    {
      "@odata.type": "microsoft.graph.accessReviewScope"
    }
  ],
  "resourceScopes": [
    {
      "@odata.type": "microsoft.graph.accessReviewScope"
    }
  ]
}
```
