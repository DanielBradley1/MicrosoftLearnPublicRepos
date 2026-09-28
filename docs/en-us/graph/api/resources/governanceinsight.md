<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/governanceinsight?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# governanceInsight resource type

Namespace: microsoft.graph

Represents insights presented to the reviewer for an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0). Insights are recommendations to reviewers to help them complete access reviews.

This complex type is the abstract type for the following derived types:

- [userSignInInsight](https://learn.microsoft.com/en-us/graph/api/resources/usersignininsight?view=graph-rest-1.0) derived type.
- [membershipOutlierInsight](https://learn.microsoft.com/en-us/graph/api/resources/membershipoutlierinsight?view=graph-rest-1.0) derived type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier of the insight. Read-only. |
| insightCreatedDateTime | DateTimeOffset | Indicates when the insight was created. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.governanceinsight",
  "id": "String",
  "insightCreatedDateTime": "DateTimeOffset"
}
```
