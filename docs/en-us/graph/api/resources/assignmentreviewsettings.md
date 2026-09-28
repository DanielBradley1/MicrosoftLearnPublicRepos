<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/assignmentreviewsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# assignmentReviewSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Used for the **accessReviewSettings** property of an [access package assignment policy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-beta). Provides additional settings to select who must review access package assignments from this policy, and how often they must be reviewed.

## Properties

This type has the following properties:

| Property | Type | Description |
| :--- | :--- | :--- |
| accessReviewTimeoutBehavior | [accessReviewTimeoutBehavior](#accessreviewtimeoutbehavior-values) | The default decision to apply if the request isn't reviewed within the period specified in **durationInDays**. The possible values are: `acceptAccessRecommendation`, `keepAccess`, `removeAccess`, and `unknownFutureValue`. |
| durationInDays | Int32 | The number of days within which reviewers should provide input. |
| isAccessRecommendationEnabled | Boolean | Specifies whether to display recommendations to the reviewer. The default value is `true` |
| isApprovalJustificationRequired | Boolean | Specifies whether the reviewer must provide justification for the approval. The default value is `true`. |
| isEnabled | Boolean | If true, access reviews are required for assignments from this policy. |
| recurrenceType | String | The interval for recurrence, such as `monthly` or `quarterly`. |
| reviewerType | String | Who should be asked to do the review, either `Self`, `Reviewers` or `Manager`. |
| reviewers | [userSet](https://learn.microsoft.com/en-us/graph/api/resources/userset?view=graph-rest-beta) collection | If the reviewerType is `Reviewers`, this collection specifies the users who will be reviewers, either by ID or as members of a group, using a collection of [singleUser](https://learn.microsoft.com/en-us/graph/api/resources/singleuser?view=graph-rest-beta) and [groupMembers](https://learn.microsoft.com/en-us/graph/api/resources/groupmembers?view=graph-rest-beta). |
| startDateTime | DateTimeOffset | When the first review should start. |

### accessReviewTimeoutBehavior values

| Member | Description |
| :--- | :--- |
| acceptAccessRecommendation | The review decision to take recommendations from access review to accept/remove access to access package. The general rule for AR recommendations is if last user sign in more than 30 days, it's recommended to remove access to that user. |
| keepAccess | The review decision is to keep current access. |
| removeAccess | The review decision is to remove access to access package. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.assignmentReviewSettings",
  "isEnabled": "Boolean",
  "recurrenceType": "String",
  "reviewerType": "String",
  "startDateTime": "String (timestamp)",
  "durationInDays": "Integer",
  "reviewers": [
    {
      "@odata.type": "microsoft.graph.singleUser"
    }
  ],
  "isAccessRecommendationEnabled": "Boolean",
  "isApprovalJustificationRequired": "Boolean",
  "accessReviewTimeoutBehavior": "String"
}
```
