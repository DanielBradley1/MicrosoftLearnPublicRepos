<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingreminder?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# bookingReminder resource type

Namespace: microsoft.graph

Represents when and whom to send an email reminder.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| message | String | The message in the reminder. |
| offset | Duration | The amount of time before the start of an appointment that the reminder should be sent. It's denoted in [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) format. |
| recipients | bookingReminderRecipients | The persons who should receive the reminder. The possible values are: `allAttendees`, `staff`, `customer`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "message": "String",
  "offset": "String (timestamp)",
  "recipients": {"@odata.type": "microsoft.graph.bookingReminderRecipients"}
}
```
