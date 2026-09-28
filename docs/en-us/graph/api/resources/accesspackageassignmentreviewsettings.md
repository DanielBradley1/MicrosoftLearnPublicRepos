<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentreviewsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageAssignmentReviewSettings resource type

Namespace: microsoft.graph

Settings configured in the **reviewSettings** property of an [accessPackageAssignmentPolicy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0) for the access reviews of assignments to an access package that were made through that policy. Provides settings to select reviewers of those assignments, and how often the assignments must be reviewed.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| expirationBehavior | accessReviewExpirationBehavior | The default decision to apply if the access is not reviewed. The possible values are: `keepAccess`, `removeAccess`, `acceptAccessRecommendation`, `unknownFutureValue`. |
| fallbackReviewers | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | This collection specifies the users who will be the fallback reviewers when the primary reviewers don't respond. |
| isEnabled | Boolean | If `true`, access reviews are required for assignments through this policy. |
| isRecommendationEnabled | Boolean | Specifies whether to display recommendations to the reviewer. The default value is `true`. |
| isReviewerJustificationRequired | Boolean | Specifies whether the reviewer must provide justification for the approval. The default value is `true`. |
| isSelfReview | Boolean | Specifies whether the principals can review their own assignments. |
| primaryReviewers | [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0) collection | This collection specifies the users or group of users who will review the access package assignments. |
| schedule | [entitlementManagementSchedule](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagementschedule?view=graph-rest-1.0) | When the first review should start and how often it should recur. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageAssignmentReviewSettings",
  "expirationBehavior": "String",
  "fallbackReviewers": [
    {
      "@odata.type": "microsoft.graph.singleUser"
    }
  ],
  "isEnabled": "Boolean",
  "isRecommendationEnabled": "Boolean",
  "isReviewerJustificationRequired": "Boolean",
  "isSelfReview": "Boolean",
  "primaryReviewers": [
    {
      "@odata.type": "microsoft.graph.singleUser"
    }
  ],
  "schedule": {
    "@odata.type": "microsoft.graph.entitlementManagementSchedule"
  }
  
}
```
