<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstagesettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# accessReviewStageSettings resource type

Namespace: microsoft.graph

In an [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0), the **stageSettings** property configures the settings for each stage of a multi-stage access review.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| decisionsThatWillMoveToNextStage | String collection | Indicate which decisions will go to the next stage. Can be a subset of `Approve`, `Deny`, `Recommendation`, or `NotReviewed`. If not provided, all decisions will go to the next stage. Optional. |
| dependsOn | String collection | Defines the sequential or parallel order of the stages and depends on the **stageId**. Only sequential stages are currently supported. For example, if **stageId** is `2`, then **dependsOn** must be `1`. If **stageId** is `1`, don't specify **dependsOn**. Required if **stageId** isn't `1`. |
| durationInDays | Int32 | The duration of the stage. Required.  <br>  <br>**NOTE:** The cumulative value of this property across all stages  <br>1. Will override the [instanceDurationInDays setting](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0) on the [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object.  <br>2. Can't exceed the length of one recurrence. That is, if the review recurs weekly, the cumulative **durationInDays** can't exceed 7. |
| fallbackReviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | If provided, the fallback reviewers are asked to complete a review if the primary reviewers don't exist. For example, if managers are selected as **reviewers** and a principal under review doesn't have a manager in Microsoft Entra ID, the fallback reviewers are asked to review that principal.  <br>  <br>**NOTE:** The value of this property overrides the corresponding setting on the [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object. |
| recommendationsEnabled | Boolean | Indicates whether showing recommendations to reviewers is enabled. Required.  <br>  <br>**NOTE:** The value of this property overrides override the corresponding [setting](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0) on the [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object. |
| recommendationInsightsSettings | [accessReviewRecommendationInsightSetting](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewrecommendationinsightsetting?view=graph-rest-1.0) collection | Determines which recommendations to show to reviewers.  <br>  <br>**NOTE:** The value of this property overrides the corresponding [setting](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0) on the [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object. |
| recommendationLookBackDuration | Duration | Optional field. Indicates the time period of inactivity \(with respect to the start date of the review instance\) that recommendations will be configured from. The recommendation is to `deny` if the user is inactive during the look back duration. For reviews of groups and Microsoft Entra roles, any duration is accepted. For reviews of applications, 30 days is the maximum duration. If not specified, the duration is 30 days.  <br>  <br>**NOTE:** The value of this property overrides the corresponding [setting](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0) on the [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object. |
| reviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | Defines who the reviewers are. If none is specified, the review is a self-review \(users review their own access\). For examples of options for assigning reviewers, see [Assign reviewers to your access review definition using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/accessreviews-reviewers-concept).  <br>  <br>**NOTE:** The value of this property overrides the corresponding setting on the [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0). |
| stageId | String | Unique identifier of the **accessReviewStageSettings** object. The **stageId** is used by the **dependsOn** property to indicate the order of the stages. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewStageSettings",
  "stageId": "String",
  "dependsOn": [
    "String"
  ],
  "durationInDays": "Integer",
  "recommendationsEnabled": "Boolean",
  "recommendationLookBackDuration": "String (duration)",
  "decisionsThatWillMoveToNextStage": [
    "String"
  ],
  "reviewers": [
    {
      "@odata.type": "microsoft.graph.accessReviewReviewerScope"
    }
  ],
  "fallbackReviewers": [
    {
      "@odata.type": "microsoft.graph.accessReviewReviewerScope"
    }
  ]
}
```
