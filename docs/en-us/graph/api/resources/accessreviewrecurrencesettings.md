<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accessreviewrecurrencesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# accessReviewRecurrenceSettings resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

This version of the access review API is deprecated and will stop returning data on May 19, 2023. Please use [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-beta&preserve-view=true).

The **accessReviewRecurrenceSettings** resource type is used in the [accessReviewSettings](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsettings?view=graph-rest-beta) resource and specifies that the access review recurs at regular intervals.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| recurrenceType | String | The recurrence interval. Possible values: `onetime`, `weekly`, `monthly`, `quarterly`, `halfyearly` or `annual`. |
| recurrenceEndType | String | How the recurrence ends. Possible values: `never`, `endBy`, `occurrences`, or `recurrenceCount`. If it's `never`, then there's no explicit end of the recurrence series. If it's `endBy`, then the recurrence ends at a certain date. If it's `occurrences`, then the series ends after `recurrenceCount` instances of the review have completed. |
| durationInDays | Int32 | The duration in days for recurrence. |
| recurrenceCount | Int32 | The count of recurrences, if the value of **recurrenceEndType** is `occurrences`, or `0` otherwise. |

## Relationships

None.

## JSON representation

```json
{
  "recurrenceType": "string",
  "recurrenceEndType": "string",
  "durationInDays": 1024,
  "recurrenceCount": 1024
}
```
