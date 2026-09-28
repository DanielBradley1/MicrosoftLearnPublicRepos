<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-10 -->

# accessReviewInstanceDecisionItem resource type

Namespace: microsoft.graph

Represents a Microsoft Entra [access review](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-1.0) decision on an instance of a review. This decision is the determination of an identity's access to a resource for a given [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0). accessReviewInstanceDecisionItem is an open type and allows other properties to be passed in.

Each decision item is system-generated based off of the parent [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List instance decisions](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-list-decisions?view=graph-rest-1.0) \(from an access review instance\) | [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) collection | Get a list of the [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) objects and their properties. |
| [List stage decisions](https://learn.microsoft.com/en-us/graph/api/accessreviewstage-list-decisions?view=graph-rest-1.0) \(from a stage of an access review instance\) | [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) collection | Get a list of the [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) objects for a stage of an acecss review instance. |
| [Get](https://learn.microsoft.com/en-us/graph/api/accessreviewinstancedecisionitem-get?view=graph-rest-1.0) | [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) | Read the properties and relationships of an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/accessreviewinstancedecisionitem-update?view=graph-rest-1.0) | [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) | Update the properties of an [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) object. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/accessreviewinstancedecisionitem-filterbycurrentuser?view=graph-rest-1.0) | [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) collection | Returns the decision items for which the calling user is the reviewer. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessReviewId | String | The identifier of the accessReviewInstance parent. Supports `$select`. Read-only. |
| appliedBy | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-1.0) | The identifier of the user who applied the decision. Read-only. |
| appliedDateTime | DateTimeOffset | The timestamp when the approval decision was applied.`00000000-0000-0000-0000-000000000000` if the assigned reviewer hasn't applied the decision or it was automatically applied. The DatetimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Supports `$select`. Read-only. |
| applyDescription | String | The description of the apply result. Read-only. |
| applyResult | String | The result of applying the decision. Possible values: `New`, `AppliedSuccessfully`, `AppliedWithUnknownFailure`, `AppliedSuccessfullyButObjectNotFound` and `ApplyNotSupported`. Supports `$select`, `$orderby`, and `$filter` \(`eq` only\). Read-only. |
| decision | String | Result of the review. Possible values: `Approve`, `Deny`, `NotReviewed`, or `DontKnow`. Supports `$select`, `$orderby`, and `$filter` \(`eq` only\). |
| id | String | The identifier of the decision. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). Supports `$select`. Read-only. |
| justification | String | Justification left by the reviewer when they made the decision. |
| permission | [accessReviewInstanceDecisionItemPermission](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitempermission?view=graph-rest-1.0) | The permission that grants the principal access to a resource. Read-only. |
| principal | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) | Every decision item in an access review represents a principal's access to a resource. This property represents details of the principal. For example, if a decision item represents access of User "Bob" to Group "Sales" - The principal is "Bob" and the resource is "Sales". Principals can be of two types - userIdentity and servicePrincipalIdentity. Supports `$select`. Read-only. |
| principalLink | String | A link to the principal object. For example, `https://graph.microsoft.com/v1.0/users/a6c7aecb-cbfd-4763-87ef-e91b4bd509d9`. Read-only. |
| recommendation | String | A system-generated recommendation for the approval decision based off last interactive sign-in to tenant. The value is `Approve` if the sign-in is fewer than 30 days after the start of review, `Deny` if the sign-in is greater than 30 days after, or `NoInfoAvailable`. Possible values: `Approve`, `Deny`, or `NoInfoAvailable`. Supports `$select`, `$orderby`, and `$filter` \(`eq` only\). Read-only. |
| resource | [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0) | Every decision item in an access review represents a principal's access to a resource. This property represents details of the resource. For example, if a decision item represents access of User "Bob" to Group "Sales" - The principal is Bob and the resource is "Sales". Resources can be of multiple types. See [accessReviewInstanceDecisionItemResource](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitemresource?view=graph-rest-1.0). Read-only. |
| resourceLink | String | A link to the resource. For example, `https://graph.microsoft.com/v1.0/servicePrincipals/c86300f3-8695-4320-9f6e-32a2555f5ff8`. Supports `$select`. Read-only. |
| reviewedBy | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-1.0) | The identifier of the reviewer.`00000000-0000-0000-0000-000000000000` if the assigned reviewer hasn't reviewed. Supports `$select`. Read-only. |
| reviewedDateTime | DateTimeOffset | The timestamp when the review decision occurred. Supports `$select`. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| insights | [governanceInsight](https://learn.microsoft.com/en-us/graph/api/resources/governanceinsight?view=graph-rest-1.0) collection | Insights are recommendations to reviewers on whether to approve or deny a decision. There can be multiple insights associated with an **accessReviewInstanceDecisionItem**. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewInstanceDecisionItem",
  "accessReviewId": "String",
  "appliedBy": {
    "@odata.type": "microsoft.graph.userIdentity"
  },
  "appliedDateTime": "String (timestamp)",
  "applyDescription": "String",
  "applyResult": "String",
  "decision": "String",
  "id": "String (identifier)",
  "justification": "String",
  "permission": {
    "@odata.type": "microsoft.graph.accessReviewInstanceDecisionItemPermission"
  },
  "principal": {
    "@odata.type": "microsoft.graph.identity"
  },
  "principalLink": "String",
  "reviewedBy": {
    "@odata.type": "microsoft.graph.userIdentity"
  },
  "reviewedDateTime": "String (timestamp)",
  "recommendation": "String",
  "resource": {
    "@odata.type": "microsoft.graph.accessReviewInstanceDecisionItemResource"
  },
  "resourceLink": "String"
}
```
