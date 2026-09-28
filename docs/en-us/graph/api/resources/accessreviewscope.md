<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# accessReviewScope resource type

Namespace: microsoft.graph

Use **accessReviewScope** to configure what is reviewed in the following properties:

- [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0): **scope**, **instanceEnumerationScope**
- [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0): **scope**
- [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0): **scopes**

This abstract type is inherited by [accessReviewQueryScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewqueryscope?view=graph-rest-1.0), [principalResourceMembershipsScope](https://learn.microsoft.com/en-us/graph/api/resources/principalresourcemembershipsscope?view=graph-rest-1.0), [accessReviewPrincipalScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewprincipalscope?view=graph-rest-1.0), [accessReviewResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewresourcescope?view=graph-rest-1.0), and [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0).

Specifying the OData type in **scope** is highly recommended for all types but required for [principalResourceMembershipsScope](https://learn.microsoft.com/en-us/graph/api/resources/principalresourcemembershipsscope?view=graph-rest-1.0) and [accessReviewInactiveUsersQueryScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinactiveusersqueryscope?view=graph-rest-1.0).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewScope"
}
```
