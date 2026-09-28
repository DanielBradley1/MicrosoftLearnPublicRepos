<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workinghours?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# workingHours resource type

Namespace: microsoft.graph

Represents the days of the week and hours in a specific time zone that the user works.

Having access to a user's working hours is useful in scenarios that handle activity or resource planning. You can [get](https://learn.microsoft.com/en-us/graph/api/user-get-mailboxsettings?view=graph-rest-1.0#example-3-get-specifically-the-working-hour-settings-of-the-signed-in-users-mailbox) and [set](https://learn.microsoft.com/en-us/graph/api/user-update-mailboxsettings?view=graph-rest-1.0#example-2) the working hours of a user as part of the user's [mailbox settings](https://learn.microsoft.com/en-us/graph/api/resources/mailboxsettings?view=graph-rest-1.0).

You can choose to set a time zone for your working hours differently from the time zone you have set on your Outlook client. This can be useful in cases like when you travel to a different time zone than you usually work in. You can set the Outlook client to the destination time zone so that Outlook time values are displayed in local time while you are there. When other people request work meetings with you in your usual place of work, they can still respect your working hours in the appropriate time zone.

> **Note:** The [working hours experience](https://support.microsoft.com/office/set-your-work-hours-and-location-in-outlook-af2fddf9-249e-4710-9c95-5911edfd76f6#articleFooterSupportBridge=communityBridge) in new Outlook and Outlook on the web isn't currently supported.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| daysOfWeek | dayOfWeek collection | The days of the week on which the user works. |
| endTime | Edm.TimeOfDay | The time of the day that the user stops working. |
| startTime | Edm.TimeOfDay | The time of the day that the user starts working. |
| timeZone | [timeZoneBase](https://learn.microsoft.com/en-us/graph/api/resources/timezonebase?view=graph-rest-1.0) | The time zone to which the working hours apply. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "daysOfWeek": ["string"],
  "endTime": "String (timeofday)",
  "startTime": "String (timeofday)",
  "timeZone": {"@odata.type": "microsoft.graph.timeZoneBase"}
}
```
