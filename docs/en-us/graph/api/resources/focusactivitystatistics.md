<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/focusactivitystatistics?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# focusActivityStatistics resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents data about the user's time available for focus work. This is based on [activityStatistics](https://learn.microsoft.com/en-us/graph/api/resources/activitystatistics?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activity | analyticsActivityType | Focus activity for which statistics are returned. |
| duration | Duration | Total sum of focus hours, which is equal to all time blocks of at least two consecutive hours, in a user's Microsoft Outlook calendar without a meeting with other people within the user's set work hours. The value is represented in ISO 8601 format for durations. |
| endDate | Date | Date when the focus activity ended. The value is represented in ISO 8601 format for calendar dates. For example, the property value could be "2019-07-04" that follows the YYYY-MM-DD format. |
| id | String | Read-only ID for the focus activity. |
| startDate | Date | Date when the focus activity started. The value is represented in ISO 8601 format for calendar dates. For example, the property value could be "2019-07-03" that follows the YYYY-MM-DD format. |
| timeZoneUsed | String | The time zone that the user sets in Outlook calendar is used for the computation. For example, the property value could be "Pacific Standard Time." |

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
  "timeZoneUsed": "String"
  }
```
