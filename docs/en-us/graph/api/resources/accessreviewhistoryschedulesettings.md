<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistoryschedulesettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# accessReviewHistoryScheduleSettings resource type

Namespace: microsoft.graph

In an [accessReviewHistoryDefinition](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewhistorydefinition?view=graph-rest-1.0), the **scheduleSettings** property configures the schedule settings for a recurring access review history definition series.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| recurrence | [patternedRecurrence](https://learn.microsoft.com/en-us/graph/api/resources/patternedrecurrence?view=graph-rest-1.0) | Detailed settings for recurrence using the standard Outlook recurrence object.  <br>  <br>**Note:** Only **dayOfMonth**, **interval**, and **type** \(`weekly`, `absoluteMonthly`\) properties are supported. Use the property **startDate** on **recurrenceRange** to determine the day the review starts. Required. |
| reportRange | String | A duration string in ISO 8601 duration format specifying the lookback period of the generated review history data. For example, if a history definition is scheduled to run on the first of every month, the **reportRange** is `P1M`. In this case, on the first of every month, access review history data is collected containing only the previous month's review data.  <br>  <br>**Note:** Only **years**, **months**, and **days** ISO 8601 properties are supported. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessReviewHistoryScheduleSettings",
  "recurrence": {
    "@odata.type": "microsoft.graph.patternedRecurrence"
  },
  "reportRange": "String"
  
}
```
