<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# accessReviewScheduleDefinition resource type

Namespace: microsoft.graph

Represents the scheduling of a Microsoft Entra [access review](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-1.0).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). An accessReviewScheduleDefinition contains a list of [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) objects. Each recurrence of the schedule definition creates an instance. Instances also represent each unique resource being reviewed. If a schedule definition reviews multiple resources \(including multiple groups\), each resource has a unique instance per each recurrence. In the case of a one-time review, only one instance is created per resource.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/accessreviewset-list-definitions?view=graph-rest-1.0) | [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) collection | Lists every accessReviewScheduleDefinition. Doesn't include associated accessReviewInstance objects in the results. |
| [Get](https://learn.microsoft.com/en-us/graph/api/accessreviewscheduledefinition-get?view=graph-rest-1.0) | [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) | Get an accessReviewScheduleDefinition with a specified **id**. Doesn't include associated accessReviewInstance objects in the results. |
| [Create](https://learn.microsoft.com/en-us/graph/api/accessreviewset-post-definitions?view=graph-rest-1.0) | [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) | Create a new accessReviewScheduleDefinition. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/accessreviewscheduledefinition-delete?view=graph-rest-1.0) | None. | Delete an accessReviewScheduleDefinition with a specified **id**. |
| [Update](https://learn.microsoft.com/en-us/graph/api/accessreviewscheduledefinition-update?view=graph-rest-1.0) | None. | Update properties of an accessReviewScheduleDefinition with a specified **id**. |
| [Filter by current user](https://learn.microsoft.com/en-us/graph/api/accessreviewscheduledefinition-filterbycurrentuser?view=graph-rest-1.0) | [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) collection | Retrieves all definitions for which the calling user is a reviewer on one or more instances. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalNotificationRecipients | [accessReviewNotificationRecipientItem](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewnotificationrecipientitem?view=graph-rest-1.0) collection | Defines the list of additional users or group members to be notified of the access review progress. |
| backupReviewers \(deprecated\) | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | This collection of reviewer scopes is used to define the list of fallback reviewers. These fallback reviewers are notified to take action if no users are found from the list of reviewers specified. This could occur when either the group owner is specified as the reviewer but the group owner doesn't exist, or manager is specified as reviewer but a user's manager doesn't exist. Supports `$select`.  <br>**Note:** This property has been replaced by **fallbackReviewers**. However, specifying either **backupReviewers** or **fallbackReviewers** automatically populates the same values to the other property. |
| createdBy | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-1.0) | User who created this review. Read-only. |
| createdDateTime | DateTimeOffset | Timestamp when the access review series was created. Supports `$select`. Read-only. |
| descriptionForAdmins | String | Description provided by review creators to provide more context of the review to admins. Supports `$select`. |
| descriptionForReviewers | String | Description provided by review creators to provide more context of the review to reviewers. Reviewers see this description in the email sent to them requesting their review. Email notifications support up to 256 characters. Supports `$select`. |
| displayName | String | Name of the access review series. Supports `$select` and `$orderby`. Required on create. |
| fallbackReviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | This collection of reviewer scopes is used to define the list of fallback reviewers. These fallback reviewers are notified to take action if no users are found from the list of reviewers specified. This could occur when either the group owner is specified as the reviewer but the group owner doesn't exist, or manager is specified as reviewer but a user's manager doesn't exist. See [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0). Replaces **backupReviewers**. Supports `$select`.  <br>  <br>**NOTE:** The value of this property will be ignored if fallback reviewers are assigned through the **stageSettings** property. |
| id | String | The feature-assigned unique identifier of an access review. Supports `$select`. Read-only. |
| instanceEnumerationScope | [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0) | This property is required when scoping a review to guest users' access across all Microsoft 365 groups and determines which Microsoft 365 groups are reviewed. Each group becomes a unique **accessReviewInstance** of the access review series. For supported scopes, see [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0). Supports `$select`. For examples of options for configuring instanceEnumerationScope, see [Configure the scope of your access review definition using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/accessreviews-scope-concept). |
| lastModifiedDateTime | DateTimeOffset | Timestamp when the access review series was last modified. Supports `$select`. Read-only. |
| reviewers | [accessReviewReviewerScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewreviewerscope?view=graph-rest-1.0) collection | This collection of access review scopes is used to define who are the reviewers. The reviewers property is only updatable if individual users are assigned as reviewers. Required on create. Supports `$select`. For examples of options for assigning reviewers, see [Assign reviewers to your access review definition using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/accessreviews-reviewers-concept).  <br>  <br>**NOTE:** The value of this property will be ignored if reviewers are assigned through the **stageSettings** property. |
| scope | [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0) | Defines the entities whose access is reviewed. For supported scopes, see [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0). Required on create. Supports `$select` and `$filter` \(`contains` only\). For examples of options for configuring scope, see [Configure the scope of your access review definition using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/accessreviews-scope-concept). |
| settings | [accessReviewScheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewschedulesettings?view=graph-rest-1.0) | The settings for an access review series, see type definition below. Supports `$select`. Required on create. |
| stageSettings | [accessReviewStageSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewstagesettings?view=graph-rest-1.0) collection | Required only for a multi-stage access review to define the stages and their settings. You can break down each review instance into up to three sequential stages, where each stage can have a different set of reviewers, fallback reviewers, and settings. Stages are created sequentially based on the **dependsOn** property. Optional.  <br>  <br>When this property is defined, its settings are used instead of the corresponding settings in the [accessReviewScheduleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscheduledefinition?view=graph-rest-1.0) object and its **settings**, **reviewers**, and **fallbackReviewers** properties. |
| status | String | This read-only field specifies the status of an access review. The typical states include `Initializing`, `NotStarted`, `Starting`, `InProgress`, `Completing`, `Completed`, `AutoReviewing`, and `AutoReviewed`.  <br>Supports `$select`, `$orderby`, and `$filter` \(`eq` only\). Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| instances | [accessReviewInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewinstance?view=graph-rest-1.0) collection | If the **accessReviewScheduleDefinition** is a recurring access review, instances represent each recurrence. A review that doesn't recur will have exactly one instance. Instances also represent each unique resource under review in the **accessReviewScheduleDefinition**. If a review has multiple resources and multiple instances, each resource has a unique instance for each recurrence. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewScheduleDefinition",
  "id": "String (identifier)",
  "displayName": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "status": "String",
  "descriptionForAdmins": "String",
  "descriptionForReviewers": "String",
  "createdBy": {
    "@odata.type": "microsoft.graph.userIdentity"
  },
  "scope": {
    "@odata.type": "microsoft.graph.accessReviewScope"
  },
  "reviewers": [
    {
      "@odata.type": "microsoft.graph.accessReviewReviewerScope"
    }
  ],
  "fallbackReviewers": [
    {
      "@odata.type": "microsoft.graph.accessReviewReviewerScope"
    }
  ],
  "instanceEnumerationScope": {
    "@odata.type": "microsoft.graph.accessReviewScope"
  },
  "stageSettings": [
    {
      "@odata.type": "microsoft.graph.accessReviewStageSettings"
    }
  ],
  "settings": {
    "@odata.type": "microsoft.graph.accessReviewScheduleSettings"
  },
  "additionalNotificationRecipients": [
    {
        "@odata.type": "microsoft.graph.accessReviewNotificationRecipientItem"
    }
  ]
}
```
