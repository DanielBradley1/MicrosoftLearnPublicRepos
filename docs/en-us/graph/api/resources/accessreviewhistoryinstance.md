<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistoryinstance?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-20 -->

# accessReviewHistoryInstance resource type

Namespace: microsoft.graph

Represents a recurrence of an [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) object. A history definition that doesn't recur will have exactly one instance.

Every **accessReviewHistoryInstance** along with its associated **accessReviewHistoryDefinition** contain the properties **reviewHistoryPeriodStartDateTime**, **reviewHistoryPeriodEndDateTime**, **decisions**, **scheduleSettings**, and **scopes**. These properties are used when scheduling recurrences and selecting review data and can be modified. Each **accessReviewHistoryInstance** object and data is only available for 30 days. When, an **accessReviewHistoryInstance** status has been moved to `done` a link can be generated to retrieve the instance's data by calling [generateDownloadUri](https://learn.microsoft.com/en-us/graph/api/accessreviewhistoryinstance-generatedownloaduri?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/accessreviewhistorydefinition-list-instances?view=graph-rest-1.0) | [accessReviewHistoryInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistoryinstance?view=graph-rest-1.0) collection | Retrieve a list of the [accessReviewHistoryInstance](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistoryinstance?view=graph-rest-1.0) objects and their properties. |
| [Generate download URI](https://learn.microsoft.com/en-us/graph/api/accessreviewhistoryinstance-generatedownloaduri?view=graph-rest-1.0) | [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0) | Generates a URI that can be used to retrieve the instance's review history data. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| downloadUri | String | Uri that can be used to retrieve review history data. This URI will be active for 24 hours after being generated. Required. |
| expirationDateTime | DateTimeOffset | Timestamp when this instance and associated data expires and the history is deleted. Required. |
| fulfilledDateTime | DateTimeOffset | Timestamp when all of the available data for this instance was collected and is set after this instance's status is set to `done`. Required. |
| id | String | The assigned unique identifier of an access review history instance. Read-only. Required. |
| reviewHistoryPeriodEndDateTime | DateTimeOffset | Timestamp reviews ending on or before this date will be included in the fetched history data. |
| reviewHistoryPeriodStartDateTime | DateTimeOffset | Timestamp reviews starting on or after this date will be included in the fetched history data. |
| runDateTime | DateTimeOffset | Timestamp when the instance's history data is scheduled to be generated. |
| status | accessReviewHistoryStatus | Represents the status of the review history data collection. The possible values are: `done`, `inProgress`, `error`, `requested`, `unknownFutureValue`. Once the **status** has been marked as `done`, a link can be generated to retrieve the instance's data by calling [generateDownloadUri](https://learn.microsoft.com/en-us/graph/api/accessreviewhistoryinstance-generatedownloaduri?view=graph-rest-1.0) method. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewHistoryInstance",
  "downloadUri": "String",
  "expirationDateTime": "String (timestamp)",
  "fulfilledDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "reviewHistoryPeriodEndDateTime": "String (timestamp)",
  "reviewHistoryPeriodStartDateTime": "String (timestamp)",
  "runDateTime": "String (timestamp)",
  "status": "String"
  
}
```
