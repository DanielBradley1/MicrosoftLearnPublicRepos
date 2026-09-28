<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callactivitystatistics?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# callActivityStatistics resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents data about the user's time spent in call activities on Microsoft Teams or Skype for Business. This is based on [activityStatistics](https://learn.microsoft.com/en-us/graph/api/resources/activitystatistics?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activity | analyticsActivityType | Call activity for which statistics are returned. |
| duration | Duration | Total hours spent on calls. The value is represented in ISO 8601 format for durations. |
| endDate | Date | Date when the call activity ended. The value is represented in ISO 8601 format for calendar dates. For example, the property value could be "2019-07-04" that follows the YYYY-MM-DD format. |
| id | String | Read-only ID for the call activity. |
| startDate | Date | Date when the call activity started. The value is represented in ISO 8601 format for calendar dates. For example, the property value could be "2019-07-03" that follows the YYYY-MM-DD format. |
| timeZoneUsed | String | The time zone that the user sets in Microsoft Outlook calendar is used for the computation. For example, the property value could be "Pacific Standard Time." |
| afterHours | Duration | Time spent on calls outside of working hours, which is based on the user's Outlook calendar setting for work hours. The value is represented in ISO 8601 format for durations. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "activity": "string",
  "duration": "String (ISO 8601 duration)",
  "endDate": "String (ISO 8601)",
  "id": "String (identifier)",
  "startDate": "String (ISO 8601)",
  "timeZoneUsed": "String",
  "afterHours": "String (ISO 8601 duration)"
}
```
