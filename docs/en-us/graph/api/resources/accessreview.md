<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-19 -->

# accessReview resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

This version of the access review API is deprecated and will stop returning data on May 19, 2023. Please use [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-beta&preserve-view=true).

Represents a Microsoft Entra [access review](https://learn.microsoft.com/en-us/graph/api/resources/accessreviews-root?view=graph-rest-beta).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List access reviews](https://learn.microsoft.com/en-us/graph/api/accessreview-list?view=graph-rest-beta) | [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) collection | List accessReviews for a businessFlowTemplate. |
| [Get access review](https://learn.microsoft.com/en-us/graph/api/accessreview-get?view=graph-rest-beta) | [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) | Get an access review with a specific id. |
| [Create access review](https://learn.microsoft.com/en-us/graph/api/accessreview-create?view=graph-rest-beta) | [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) | Create a new accessReview. |
| [Update access review](https://learn.microsoft.com/en-us/graph/api/accessreview-update?view=graph-rest-beta) | [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) | Update an accessReview. |
| [Delete access review](https://learn.microsoft.com/en-us/graph/api/accessreview-delete?view=graph-rest-beta) | None. | Delete an accessReview. |
| [List reviewers](https://learn.microsoft.com/en-us/graph/api/accessreview-listreviewers?view=graph-rest-beta) | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-beta) collection | Get the reviewers of an accessReview. |
| [Add reviewer](https://learn.microsoft.com/en-us/graph/api/accessreview-addreviewer?view=graph-rest-beta) | None. | Add a reviewer to an accessReview. |
| [Remove reviewer](https://learn.microsoft.com/en-us/graph/api/accessreview-removereviewer?view=graph-rest-beta) | None. | Remove a reviewer from an accessReview. |
| [List decisions](https://learn.microsoft.com/en-us/graph/api/accessreview-listdecisions?view=graph-rest-beta) | [accessReviewDecision](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewdecision?view=graph-rest-beta) collection | Get the decisions of an accessReview. |
| [List my decisions](https://learn.microsoft.com/en-us/graph/api/accessreview-listmydecisions?view=graph-rest-beta) | [accessReviewDecision](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewdecision?view=graph-rest-beta) collection | As a reviewer, get my decisions of an accessReview. |
| [Send reminder](https://learn.microsoft.com/en-us/graph/api/accessreview-sendreminder?view=graph-rest-beta) | None. | Send a reminder to the reviewers of an accessReview. |
| [Stop](https://learn.microsoft.com/en-us/graph/api/accessreview-stop?view=graph-rest-beta) | None. | Stop an accessReview. |
| [Reset](https://learn.microsoft.com/en-us/graph/api/accessreview-reset?view=graph-rest-beta) | None. | Reset the decisions in an in-progress accessReview. |
| [Apply decisions](https://learn.microsoft.com/en-us/graph/api/accessreview-apply?view=graph-rest-beta) | None. | Apply the decisions from a completed accessReview. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The feature-assigned unique identifier of an access review. |
| displayName | String | The access review name. Required on create. |
| startDateTime | DateTimeOffset | The date and time when the review is scheduled to be start. This date can be in the future. Required on create. |
| endDateTime | DateTimeOffset | The DateTime when the review is scheduled to end. This must be at least one day later than the start date. Required on create. |
| status | String | This read-only field specifies the status of an accessReview. The typical states include `Initializing`, `NotStarted`, `Starting`,`InProgress`, `Completing`, `Completed`, `AutoReviewing`, and `AutoReviewed`. |
| description | String | The description provided by the access review creator, to show to the reviewers. |
| businessFlowTemplateId | String | The business flow template identifier. Required on create. This value is case sensitive. |
| reviewerType | String | The relationship type of reviewer to the target object, one of: `self`, `delegated`, `entityOwners`. Required on create. |
| createdBy | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-beta) | The user who created this review. |
| reviewedEntity | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | The object for which the access review is reviewing the access rights assignments. This identity can be the group for the review of memberships of users in a group, or the app for a review of assignments of users to an application. Required on create. |
| settings | [accessReviewSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsettings?view=graph-rest-beta) | The settings of an accessReview, see type definition below. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| reviewers | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-beta) collection | The collection of reviewers for an access review, if access review reviewerType is of type `delegated`. |
| decisions | [accessReviewDecision](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewdecision?view=graph-rest-beta) collection | The collection of decisions for this access review. |
| myDecisions | [accessReviewDecision](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewdecision?view=graph-rest-beta) collection | The collection of decisions for the caller, if the caller is a reviewer. |
| instances | [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) collection | The collection of access reviews instances past, present, and future, if this object is a recurring access review. |

Whether these relationships are present on an object, depends upon whether the object is a one-time access review, the series of a recurring access review, or an instance of a recurring access review.

| Scenario | Has reviewers? | Has decisions and myDecisions? | Has instances? |
| :--- | :--- | :--- | :--- |
| One-time access review | Yes | Yes, once started | No |
| Recurring access review | Yes | No | Yes |
| Instance of a recurring access review | Yes | Yes, once started | No |

## JSON representation

The following JSON representation shows the resource type.

```json
{
 "id": "string (identifier)",
 "displayName": "string",
 "startDateTime": "string (timestamp)",
 "endDateTime": "string (timestamp)",
 "status": "string",
 "description": "string",
 "businessFlowTemplateId": "string (identifier)",
 "reviewerType": "string",
 "createdBy": {"@odata.type": "microsoft.graph.userIdentity"},
 "reviewedEntity": {"@odata.type": "microsoft.graph.identity"},
 "settings": {"@odata.type": "microsoft.graph.accessReviewSettings"},
 "reviewers": [{"@odata.type": "microsoft.graph.userIdentity"}]
}
```
