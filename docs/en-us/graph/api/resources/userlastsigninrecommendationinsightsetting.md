<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userlastsigninrecommendationinsightsetting?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# userlastsignInrecommendationinsightsetting resource type

Namespace: microsoft.graph

Use **userLastSignInRecommendationInsightSetting** to configure last sign-in insights in the following properties:

- [accessReviewScheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0): **recommendationInsightSettings**
- [accessReviewStageSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstagesettings?view=graph-rest-1.0): **recommendationInsightsSettings**

Inherits from [accessReviewRecommendationInsightSetting](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewrecommendationinsightsetting?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| recommendationLookBackDuration | Duration | Optional. Indicates the time period of inactivity \(with respect to the start date of the review instance\) that recommendations will be configured from. The recommendation will be to `deny` if the user is inactive during the look-back duration. For reviews of groups and Microsoft Entra roles, any duration is accepted. For reviews of applications, 30 days is the maximum duration. If not specified, the duration is 30 days. |
| signInScope | userSignInRecommendationScope | Indicates whether inactivity is calculated based on the user's inactivity in the tenant or in the application. The possible values are `tenant`, `application`, `unknownFutureValue`. `application` is only relevant when the access review is a review of an assignment to an application. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userlastsignInrecommendationinsightsetting",
  "recommendationLookBackDuration": "String (duration)",
  "signInScope": "String"
}
```
