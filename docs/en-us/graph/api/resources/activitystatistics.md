<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/activitystatistics?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# activityStatistics resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents time spent by a user on various work activities during and outside of working hours, for the specified time range in the request, which uses an aggregation period of one day.

The following types of statistics are derived from **activityStatistics**:

- [Call](https://learn.microsoft.com/en-us/graph/api/resources/callactivitystatistics?view=graph-rest-beta)
- [Chat](https://learn.microsoft.com/en-us/graph/api/resources/chatactivitystatistics?view=graph-rest-beta)
- [Email](https://learn.microsoft.com/en-us/graph/api/resources/emailactivitystatistics?view=graph-rest-beta)
- [Focus](https://learn.microsoft.com/en-us/graph/api/resources/focusactivitystatistics?view=graph-rest-beta)
- [Meeting](https://learn.microsoft.com/en-us/graph/api/resources/meetingactivitystatistics?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List activity statistics](https://learn.microsoft.com/en-us/graph/api/activitystatistics-list?view=graph-rest-beta) | [activityStatistics](https://learn.microsoft.com/en-us/graph/api/resources/activitystatistics?view=graph-rest-beta) | Retrieve the properties for the collection of activity statistics for a user, for the last complete week. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activity | analyticsActivityType | The type of activity for which statistics are returned. The possible values are: `call`, `chat`, `email`, `focus`, and `meeting`. |
| duration | Duration | Total hours spent on the activity. The value is represented in ISO 8601 format for durations. |
| endDate | Date | Date when the activity ended, expressed in ISO 8601 format for calendar dates. For example, the property value could be "2019-07-03" that follows the YYYY-MM-DD format. |
| id | String | Read-only ID for the activity. Do not parse or customize the value for your scenarios. |
| startDate | Date | Date when the activity started, expressed in ISO 8601 format for calendar dates. For example, the property value could be "2019-07-04" that follows the YYYY-MM-DD format. |
| timeZoneUsed | String | The time zone that the user sets in Microsoft Outlook is used for the computation. For example, the property value could be "Pacific Standard Time." |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "activity": "String",
  "duration": "String (ISO 8601 duration)",
  "endDate": "String (ISO 8601 format)",
  "id": "String (identifier)",
  "startDate": "String (ISO 8601 format)",
  "timeZoneUsed": "String"
}
```
