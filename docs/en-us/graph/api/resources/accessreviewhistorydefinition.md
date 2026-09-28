<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# accessReviewHistoryDefinition resource type

Namespace: microsoft.graph

Represents a collection of access review historical data and the scopes used to collect that data.

An **accessReviewHistoryDefinition** contains a list of [accessReviewHistoryInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistoryinstance?view=graph-rest-1.0) objects. Each recurrence of the history definition creates an instance. In the case of a one-time history definition, only one instance is created.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/accessreviewset-list-historydefinitions?view=graph-rest-1.0) | [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) collection | Get a list of the [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/accessreviewset-post-historydefinitions?view=graph-rest-1.0) | [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) | Create a new [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/accessreviewhistorydefinition-get?view=graph-rest-1.0) | [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) | Read the properties and relationships of an [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-1.0) | User who created this review history definition. |
| createdDateTime | DateTimeOffset | Timestamp when the access review definition was created. |
| decisions | String collection | Determines which review decisions will be included in the fetched review history data if specified. Optional on create. All decisions are included by default if no decisions are provided on create. The possible values are: `approve`, `deny`, `dontKnow`, `notReviewed`, and `notNotified`. |
| displayName | String | Name for the access review history data collection. Required. |
| id | String | The assigned unique identifier of an access review history definition. |
| reviewHistoryPeriodEndDateTime | DateTimeOffset | A timestamp. Reviews ending on or before this date will be included in the fetched history data. Only required if **scheduleSettings** isn't defined. |
| reviewHistoryPeriodStartDateTime | DateTimeOffset | A timestamp. Reviews starting on or before this date will be included in the fetched history data. Only required if **scheduleSettings** isn't defined. |
| scheduleSettings | [accessReviewHistoryScheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistoryschedulesettings?view=graph-rest-1.0) | The settings for a recurring access review history definition series. Only required if **reviewHistoryPeriodStartDateTime** or **reviewHistoryPeriodEndDateTime** aren't defined. Not supported yet. |
| scopes | [accessReviewScope](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewscope?view=graph-rest-1.0) collection | Used to scope what reviews are included in the fetched history data. Fetches reviews whose scope matches with this provided scope. Required. |
| status | accessReviewHistoryStatus | Represents the status of the review history data collection. The possible values are: `done`, `inProgress`, `error`, `requested`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| instances | [accessReviewHistoryInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistoryinstance?view=graph-rest-1.0) collection | If the **accessReviewHistoryDefinition** is a recurring definition, instances represent each recurrence. A definition that doesn't recur will have exactly one instance. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewHistoryDefinition",
  "createdBy": {
    "@odata.type": "microsoft.graph.userIdentity"
  },
  "createdDateTime": "String (timestamp)",
  "decisions": [
    "String"
  ],
  "displayName": "String",
  "id": "String (identifier)",
  "reviewHistoryPeriodEndDateTime": "String (timestamp)",
  "reviewHistoryPeriodStartDateTime": "String (timestamp)",
  "scopes": [
    {
      "@odata.type": "microsoft.graph.accessReviewScope"
    }
  ],
  "scheduleSettings": {
    "@odata.type": "microsoft.graph.accessReviewHistoryScheduleSettings"
  },
  "status": "String",
}
```
