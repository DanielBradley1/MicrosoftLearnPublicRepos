<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# accessReviewStage resource type

Namespace: microsoft.graph

Represents a stage of a Microsoft Entra [access review](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-1.0). If the parent [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) has defined the **stageSettings** property, the [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) is comprised of up to three subsequent stages. Each stage may have a different set of reviewers who can act on the stage decisions, and settings determining which decisions pass from stage to stage.

Every **accessReviewStage** contains a list of [decision items](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) for reviewers. There's only one decision per identity being reviewed.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/accessreviewinstance-list-stages?view=graph-rest-1.0) | [accessReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstage?view=graph-rest-1.0) collection | Get a list of the [accessReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstage?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/accessreviewstage-get?view=graph-rest-1.0) | [accessReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstage?view=graph-rest-1.0) | Read the properties and relationships of an [accessReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstage?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/accessreviewstage-update?view=graph-rest-1.0) | [accessReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstage?view=graph-rest-1.0) | Update the properties of an [accessReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstage?view=graph-rest-1.0) object. |
| [Stop](https://learn.microsoft.com/en-us/graph/api/accessreviewstage-stop?view=graph-rest-1.0) | None | Manually stop an accessReviewStage. |
| [Accept recommendations](https://learn.microsoft.com/en-us/graph/api/accessreviewstage-acceptrecommendations?view=graph-rest-1.0) | None | Accept the recommendations on all decision items that haven't been reviewed within a single accessReviewStage. |
| [Batch record decisions](https://learn.microsoft.com/en-us/graph/api/accessreviewstage-batchrecorddecisions?view=graph-rest-1.0) | None | Record decisions in bulk for all decision items within a single accessReviewStage. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/accessreviewstage-filterbycurrentuser?view=graph-rest-1.0) | [accessReviewStage](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstage?view=graph-rest-1.0) collection | Returns all stages on a given [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) for which the calling user is a reviewer. |
| [List decisions from a stage of an instance](https://learn.microsoft.com/en-us/graph/api/accessreviewstage-list-decisions?view=graph-rest-1.0) | [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) collection | Get the decisions made in an accessReviewStage. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| endDateTime | DateTimeOffset | The date and time in ISO 8601 format and UTC time when the review stage is scheduled to end. This property is the cumulative total of the **durationInDays** for all stages. Read-only. |
| fallbackReviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | This collection of reviewer scopes is used to define the list of fallback reviewers. These fallback reviewers are notified to take action if no users are found from the list of reviewers specified. This could occur when either the group owner is specified as the reviewer but the group owner doesn't exist, or manager is specified as reviewer but a user's manager doesn't exist. |
| id | String | Unique identifier of the stage. Read-only. |
| reviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | This collection of access review scopes is used to define who the reviewers are. For examples of options for assigning reviewers, see [Assign reviewers to your access review definition using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/accessreviews-scope-concept). |
| startDateTime | DateTimeOffset | The date and time in ISO 8601 format and UTC time when the review stage is scheduled to start. Read-only. |
| status | String | Specifies the status of an accessReviewStage. Possible values: `Initializing`, `NotStarted`, `Starting`, `InProgress`, `Completing`, `Completed`, `AutoReviewing`, and `AutoReviewed`. Supports `$orderby`, and `$filter` \(`eq` only\). Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| decisions | [accessReviewInstanceDecisionItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstancedecisionitem?view=graph-rest-1.0) collection | Each user reviewed in an accessReviewStage has a decision item representing if they were approved, denied, or not yet reviewed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewStage",
  "endDateTime": "String (timestamp)",
  "fallbackReviewers": [
    {
      "@odata.type": "microsoft.graph.accessReviewReviewerScope"
    }
  ],
  "id": "String (identifier)",
  "reviewers": [
    {
      "@odata.type": "microsoft.graph.accessReviewReviewerScope"
    }
  ],
  "startDateTime": "String (timestamp)",
  
  "status": "String"
  
}
```
