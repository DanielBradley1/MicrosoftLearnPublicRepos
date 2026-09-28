<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# accessReviewInstance resource type

Namespace: microsoft.graph

Represents a Microsoft Entra [access review](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-1.0) recurrence. If the parent [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) is a recurring access review, instances represent each recurrence. A review that does not recur will have exactly one instance. Instances also represent each unique group being reviewed in the schedule definition. If a schedule definition reviews multiple groups, each group will have a unique instance for each recurrence.

Every **accessReviewInstance** contains a list of [decisions](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) that reviewers can take action on. There is one decision per identity being reviewed.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/accessreviewscheduledefinition-list-instances?view=graph-rest-1.0) | [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) collection | Get a list of the [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-get?view=graph-rest-1.0) | [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) | Read the properties and relationships of an [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-update?view=graph-rest-1.0) | [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) | Update the reviewers of an [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) object. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-filterbycurrentuser?view=graph-rest-1.0) | [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) collection | Returns all instances of a given [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) for which the calling user is the reviewer of one or more decisions. |
| [List contacted reviewers](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-list-contactedreviewers?view=graph-rest-1.0) | [accessReviewReviewer](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewer?view=graph-rest-1.0) collection | Get the reviewers who received notifications for an access review instance. |
| [Send reminder](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-sendreminder?view=graph-rest-1.0) | None | Send a reminder to the reviewers of an accessReviewInstance. |
| [Stop](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-stop?view=graph-rest-1.0) | None | Manually stop an accessReviewInstance. |
| [Accept recommendations](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-acceptrecommendations?view=graph-rest-1.0) | None | Allows the calling user to accept the decision recommendation for each **accessReviewInstanceDecisionItem** that is marked as `NotReviewed` and for which the caller is a reviewer of the associated **accessReviewInstance**. |
| [Apply decisions](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-applydecisions?view=graph-rest-1.0) | None | Manually apply decisions on an **accessReviewInstance**. |
| [Apply custom data provided resource decisions](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-batchapplycustomdataprovidedresourcedecisions?view=graph-rest-1.0) | None | Set the `applyResult` on all decisions for a specific custom data provided resource in one call. |
| [Batch record decisions](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-batchrecorddecisions?view=graph-rest-1.0) | None | Review batches of principals or resources in one call. |
| [Reset decisions](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-resetdecisions?view=graph-rest-1.0) | None | Resets all decision items on an instance to `notReviewed`. |
| [List stages](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-list-stages?view=graph-rest-1.0) | [accessReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstage?view=graph-rest-1.0) collection | Retrieve the stages in a multi-stage access review instance. |
| [List decisions](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-list-decisions?view=graph-rest-1.0) | [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) collection | Get the accessReviewInstanceDecisionItem resources from the decisions navigation property. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endDateTime | DateTimeOffset | DateTime when review instance is scheduled to end.The DatetimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Supports `$select`. Read-only. |
| errors | [accessReviewError](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewerror?view=graph-rest-1.0) collection | Collection of errors in an access review instance lifecycle. Read-only. |
| fallbackReviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | This collection of reviewer scopes is used to define the list of fallback reviewers. These fallback reviewers will be notified to take action if no users are found from the list of reviewers specified. This could occur when either the group owner is specified as the reviewer but the group owner does not exist, or manager is specified as reviewer but a user's manager does not exist. Supports `$select`. |
| id | String | Unique identifier of the instance. Supports `$select`. Read-only. |
| reviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | This collection of access review scopes is used to define who the reviewers are. Supports `$select`. For examples of options for assigning reviewers, see [Assign reviewers to your access review definition using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/accessreviews-scope-concept). |
| scope | [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0) | Created based on **scope** and **instanceEnumerationScope** at the accessReviewScheduleDefinition level. Defines the scope of users reviewed in a group. Supports `$select` and `$filter` \(`contains` only\). Read-only. |
| startDateTime | DateTimeOffset | DateTime when review instance is scheduled to start. May be in the future. The DateTimeOffset type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Supports `$select`. Read-only. |
| status | String | Specifies the status of an accessReview. Possible values: `Initializing`, `NotStarted`, `Starting`, `InProgress`, `Completing`, `Completed`, `AutoReviewing`, and `AutoReviewed`. Supports `$select`, `$orderby`, and `$filter` \(`eq` only\). Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| contactedReviewers | [accessReviewReviewer](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewer?view=graph-rest-1.0) collection | Returns the collection of reviewers who were contacted to complete this review. While the **reviewers** and **fallbackReviewers** properties of the **accessReviewScheduleDefinition** might specify group owners or managers as **reviewers**, **contactedReviewers** returns their individual identities. Supports `$select`. Read-only. |
| decisions | [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) collection | Each user reviewed in an **accessReviewInstance** has a decision item representing if they were approved, denied, or not yet reviewed. |
| stages | [accessReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstage?view=graph-rest-1.0) collection | If the instance has multiple stages, this returns the collection of stages. A new stage will only be created when the previous stage ends. The existence, number, and settings of stages on a review instance are created based on the [accessReviewStageSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstagesettings?view=graph-rest-1.0) on the parent [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
 "@odata.type": "#microsoft.graph.accessReviewInstance",
 "contactedReviewers": [
    {
      "@odata.type": "microsoft.graph.accessReviewReviewer"
    }
  ],
 "endDateTime": "string (timestamp)",
 "errors": [
    {
      "@odata.type": "microsoft.graph.accessReviewError"
    }
  ],
 "fallbackReviewers": [
    {
      "@odata.type": "microsoft.graph.accessReviewReviewerScope"
    }
  ],
  "id": "string (identifier)",
  "reviewers": [
    {
      "@odata.type": "microsoft.graph.accessReviewReviewerScope"
    }
  ],
  "scope": {
    "@odata.type": "microsoft.graph.accessReviewScope"
  },
  "startDateTime": "string (timestamp)",
  "status": "string"
  
}
```
