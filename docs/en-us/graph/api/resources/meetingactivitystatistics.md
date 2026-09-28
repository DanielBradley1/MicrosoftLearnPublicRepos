<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingactivitystatistics?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# meetingActivityStatistics resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents data about the user's time spent in meetings in Microsoft Outlook, Microsoft Teams, or Skype for Business. This is based on [activityStatistics](https://learn.microsoft.com/en-us/graph/api/resources/activitystatistics?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activity | analyticsActivityType | Meeting activity for which statistics are returned. |
| duration | Duration | Total hours spent on meetings. The value is represented in ISO 8601 format for durations. |
| endDate | Date | Date when the meeting activity ended. The value is represented in ISO 8601 format for calendar dates. For example, the property value could be "2019-07-04" that follows the YYYY-MM-DD format. |
| id | String | Read-only ID for the meeting activity. |
| startDate | Date | Date when the meeting activity started. The value is represented in ISO 8601 format for calendar dates. For example, the property value could be "2019-07-03" that follows the YYYY-MM-DD format. |
| timeZoneUsed | String | The Outlook time zone that the user sets in Outlook calendar is used for the computation. For example, the property value could be "Pacific Standard Time." |
| afterHours | Duration | Time spent on meetings outside of working hours, which is based on the user's Outlook calendar setting for work hours. The value is represented in ISO 8601 format for durations. |
| conflicting | Duration | Time spent in conflicting meetings \(meetings that overlap with other meetings that the person accepted and where the person’s status is set to Busy\). The value is represented in ISO 8601 format for durations. |
| long | Duration | Time spent in long meetings \(more than an hour in duration\). The value is represented in ISO 8601 format for durations. |
| multitasking | Duration | Time spent in meetings where the person was multitasking \(read/sent more than a minimum number of emails and/or sent more than a minimum number of messages in Teams or in Skype for Business\). The value is represented in ISO 8601 format for durations. |
| organized | Duration | Time spent in meetings organized by the user. The value is represented in ISO 8601 format for durations. |
| recurring | Duration | Time spent on recurring meetings. The value is represented in ISO 8601 format for durations. |

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
  "afterHours": "String (ISO 8601 duration)",
  "conflicting": "String (ISO 8601 duration)",
  "long": "String (ISO 8601 duration)",
  "multitasking": "String (ISO 8601 duration)",
  "organized": "String (ISO 8601 duration)",
  "recurring": "String (ISO 8601 duration)"
}
```
