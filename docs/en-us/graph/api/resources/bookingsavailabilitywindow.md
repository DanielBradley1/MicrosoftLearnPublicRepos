<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingsavailabilitywindow?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# bookingsAvailabilityWindow resource type

Namespace: microsoft.graph

Represents the availability details of a booking service in a scheduling policy between two dates.

Inherits from [bookingsAvailability](https://learn.microsoft.com/en-us/graph/api/resources/bookingsavailability?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| availabilityType | bookingsServiceAvailabilityType | Availability type defined by the given **bookingsAvailability**. The possible values are: `bookWhenStaffAreFree`, `notBookable`, `customWeeklyHours`, `unknownFutureValue`. Inherited from [bookingsAvailability](https://learn.microsoft.com/en-us/graph/api/resources/bookingsavailability?view=graph-rest-1.0). |
| businessHours | [bookingWorkHours](https://learn.microsoft.com/en-us/graph/api/resources/bookingworkhours?view=graph-rest-1.0) collection | The hours of operation in a week. The business hours value is set to `null` if the availability type isn't `customWeeklyHours`. Inherited from [bookingsAvailability](https://learn.microsoft.com/en-us/graph/api/resources/bookingsavailability?view=graph-rest-1.0). |
| endDate | Date | End date of the availability window. |
| startDate | Date | Start date of the availability window. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.bookingsAvailabilityWindow",
  "availabilityType": "String",
  "businessHours": [{"@odata.type": "microsoft.graph.bookingWorkHours"}],
  "endDate": "String (Date)",
  "startDate": "String (Date)"
}
```
