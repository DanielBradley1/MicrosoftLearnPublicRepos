<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# accessReviewSettings resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

This version of the access review API is deprecated and will stop returning data on May 19, 2023. Please use [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-beta&preserve-view=true).

Provides more settings when creating an access review, to control the feature behavior when starting an access review.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| mailNotificationsEnabled | Boolean | Indicates whether sending mails to reviewers and the review creator is enabled. |
| remindersEnabled | Boolean | Indicates whether sending reminder emails to reviewers is enabled. |
| justificationRequiredOnApproval | Boolean | Indicates whether reviewers are required to provide a justification when reviewing access. |
| activityDurationInDays | Int64 | The number of days of user activities to show to reviewers. |
| autoReviewEnabled | Boolean | Indicates whether a decision should be set if the reviewer didn't supply one. For use when, auto-apply is enabled. If you don't want to have a review decision recorded unless the reviewer makes an explicit choice, set it to `false`. |
| autoReviewSettings | [autoReviewSettings](https://learn.microsoft.com/en-us/graph/api/resources/autoreviewsettings?view=graph-rest-beta) | Detailed settings for how the feature should set the review decision. For use when, auto-apply is enabled. |
| recurrenceSettings | [accessReviewRecurrenceSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewrecurrencesettings?view=graph-rest-beta) | Detailed settings for recurrence. |
| autoApplyReviewResultsEnabled | Boolean | Indicates whether the auto-apply capability, to automatically change the target object access resource, is enabled. If not enabled, a user must, after the review completes, apply the access review. |
| accessRecommendationsEnabled | Boolean | Indicates whether showing recommendations to reviewers is enabled. |

## Relationships

None.

## JSON representation

```json
{
  "mailNotificationsEnabled": true,
  "remindersEnabled": true,  
  "justificationRequiredOnApproval": true,
  "activityDurationInDays": 1024,
  "autoReviewEnabled": false,
  "autoReviewSettings": {"@odata.type": "microsoft.graph.autoReviewSettings"},
  "recurrenceSettings": {"@odata.type": "microsoft.graph.accessReviewRecurrenceSettings"},
  "autoApplyReviewResultsEnabled": false,
  "accessRecommendationsEnabled": false
}
```
