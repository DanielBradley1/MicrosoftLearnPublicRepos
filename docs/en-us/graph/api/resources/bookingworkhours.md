<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingworkhours?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# bookingWorkHours resource type

Namespace: microsoft.graph

Represents the set of working hours in a single day of the week, for a [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0) or [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| day | String | The day of the week represented by this instance. The possible values are: `sunday`, `monday`, `tuesday`, `wednesday`, `thursday`, `friday`, `saturday`. |
| timeSlots | [bookingWorkTimeSlot](https://learn.microsoft.com/en-us/graph/api/resources/bookingworktimeslot?view=graph-rest-1.0) collection | A list of start/end times during a day. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "day": "String",
  "timeSlots": [{"@odata.type": "microsoft.graph.bookingWorkTimeSlot"}]
}
```
