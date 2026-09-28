<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/reminder?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# reminder resource type

Namespace: microsoft.graph

A reminder for an [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) in a user [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| changeKey | String | Identifies the version of the reminder. Every time the reminder is changed, **changeKey** changes as well. This allows Exchange to apply changes to the correct version of the object. |
| eventEndTime | [DateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date, time and time zone that the event ends. |
| eventId | String | The unique ID of the event. Read-only. |
| eventLocation | [Location](https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0) | The location of the event. |
| eventStartTime | [DateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date, time, and time zone that the event starts. |
| eventSubject | String | The text of the event's subject line. |
| eventWebLink | String | The URL to open the event in Outlook on the web.  <br>  <br>The event opens in the browser if you're logged in to your mailbox via Outlook on the web. You're prompted to log in if you aren't already logged in with the browser.  <br>  <br>This URL can't be accessed from within an iFrame. |
| reminderFireTime | [DateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date, time, and time zone that the reminder is set to occur. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "changeKey": "string",
  "eventEndTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "eventId": "string",
  "eventLocation": {"@odata.type": "microsoft.graph.location"},
  "eventStartTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "eventSubject": "string",
  "eventWebLink": "string",
  "reminderFireTime": {"@odata.type": "microsoft.graph.dateTimeTimeZone"}
}
```
