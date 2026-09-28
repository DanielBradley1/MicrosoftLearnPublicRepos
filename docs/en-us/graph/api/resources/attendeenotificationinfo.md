<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attendeenotificationinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-01 -->

# attendeeNotificationInfo resource type

Namespace: microsoft.graph

Represents information about an external attendee.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| phoneNumber | String | The phone number of the external attendee. Required. |
| timeZone | String | The time zone of the external attendee. The timeZone property can be set to any of the time zones currently supported by [Windows](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/default-time-zones). Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
 "phoneNumber": "String",
 "timeZone": "String"
}
```
