<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# unifiedRoot resource type

Namespace: microsoft.graph

Container resource that groups the unified access review collections under the `identityGovernance/accessReviews/unified` path segment. The `unified` route is the entry point for **user-centric \(catalog-scope\) access reviews**, where an administrator reviews a user's access across all the resources contained in an [entitlement management catalog](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagecatalog?view=graph-rest-1.0) in a single review, rather than reviewing one resource at a time.

A catalog is a container that groups multiple resource types—currently groups and applications. With a user-centric review, a reviewer \(typically the user's manager\) evaluates a principal's access to every group and application in the catalog from a single, consolidated view. The collections reuse the same [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0), [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0), and [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) resource shapes as the generally available access reviews API; the catalog scope is expressed through the [principalResourceMembershipsScope](https://learn.microsoft.com/en-us/graph/api/resources/principalresourcemembershipsscope?view=graph-rest-1.0) of the review definition.

This resource is reached through the **unified** relationship on the [accessReviewSet](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewset?view=graph-rest-1.0) resource.

The following table summarizes how the unified route differs from the current access reviews API.

| Aspect | Current access reviews \(`accessReviews`\) | Unified access reviews \(`accessReviews/unified`\) |
| :--- | :--- | :--- |
| Review focus | Reviews a single resource at a time \(one group, application, directory role, or access package\). | User-centric: reviews a principal's access across all groups and applications in a catalog in one review. |
| Scope model | Typically an [accessReviewQueryScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewqueryscope?view=graph-rest-1.0) targeting one resource. | A [principalResourceMembershipsScope](https://learn.microsoft.com/en-us/graph/api/resources/principalresourcemembershipsscope?view=graph-rest-1.0) with a resource scope of `scopeType: catalog`. |
| Routing | Addressed under `identityGovernance/accessReviews`. | Addressed under `identityGovernance/accessReviews/unified`. The path segment is self-describing, discoverable in metadata, and works with the Microsoft Graph SDKs and Graph Explorer. |

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List definitions](https://learn.microsoft.com/en-us/graph/api/unifiedroot-list-definitions?view=graph-rest-1.0) | [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) collection | Retrieve the user-centric \(catalog-scope\) [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) objects through the unified route. |
| [Create definition](https://learn.microsoft.com/en-us/graph/api/unifiedroot-post-definitions?view=graph-rest-1.0) | [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) | Create a new user-centric \(catalog-scope\) [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object through the unified route. |

Only listing and creating definitions are documented as dedicated **unified** methods, because creating a catalog-scope review is the one operation that is specific to the unified route. After a definition is created, its instances, stages, and decisions are managed through the shared [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0), [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0), and [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) operations \(for example, get, update, delete, list instances, stop, and apply decisions\), addressed under the `identityGovernance/accessReviews/unified` path segment.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| decisions | [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) collection | Represents the unified \(vNext\) access review decisions on an instance of a review. |
| definitions | [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) collection | Represents the unified \(vNext\) template and scheduling for an access review. |
| instances | [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) collection | Represents the unified \(vNext\) instance of a review. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedRoot"
}
```
