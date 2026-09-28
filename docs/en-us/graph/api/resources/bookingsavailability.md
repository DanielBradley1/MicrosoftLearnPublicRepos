<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingsavailability?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# bookingsAvailability resource type

Namespace: microsoft.graph

Represents the availability details of a booking service in a scheduling policy.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| availabilityType | bookingsServiceAvailabilityType | Availability type defined by the given **bookingsAvailability**. The possible values are: `bookWhenStaffAreFree`, `notBookable`, `customWeeklyHours`, `unknownFutureValue`. |
| businessHours | [bookingWorkHours](https://learn.microsoft.com/en-us/graph/api/resources/bookingworkhours?view=graph-rest-1.0) collection | The hours of operation in a week. The business hours value is set to `null` if the availability type isn't `customWeeklyHours`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.bookingsAvailability",
  "availabilityType": "String",
  "businessHours": [{"@odata.type": "microsoft.graph.bookingWorkHours"}]
}
```
