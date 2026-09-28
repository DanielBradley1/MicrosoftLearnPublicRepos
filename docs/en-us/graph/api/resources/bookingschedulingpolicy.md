<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingschedulingpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-13 -->

# bookingSchedulingPolicy resource type

Namespace: microsoft.graph

Represents the set of policies that determine how appointments should be created in a Microsoft Bookings calendar.

Note

If the Default Scheduling Policy is enabled at the service level, the values of this resource are limited to those defined in the policy in the [List services](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-services) API response. In this case, the client must fall back to the Default Scheduling Policy for the business.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowStaffSelection | Boolean | `True` to allow customers to choose a specific person for the booking. |
| customAvailabilities | [bookingsAvailabilityWindow](https://learn.microsoft.com/en-us/graph/api/resources/bookingsavailabilitywindow?view=graph-rest-1.0) collection | Custom availability of the service in a given time frame. |
| generalAvailability | [bookingsAvailability](https://learn.microsoft.com/en-us/graph/api/resources/bookingsavailability?view=graph-rest-1.0) | General availability of the service defined by the scheduling policy. |
| isMeetingInviteToCustomersEnabled | Boolean | Indicates whether the meeting invite is sent to the customers. The default value is `false`. |
| maximumAdvance | Duration | Maximum number of days in advance that a booking can be made. It follows the [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) format. |
| minimumLeadTime | Duration | The minimum amount of time before which bookings and cancellations must be made. It follows the [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) format. |
| sendConfirmationsToOwner | Boolean | `True` to notify the business via email when a booking is created or changed. Use the email address specified in the **email** property of the **bookingBusiness** entity for the business. |
| timeSlotInterval | Duration | Duration of each time slot, denoted in [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) format. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "allowStaffSelection": "Boolean",
  "customAvailabilities": [{"@odata.type": "microsoft.graph.bookingsAvailabilityWindow"}],
  "generalAvailability": {"@odata.type": "microsoft.graph.bookingsAvailability"},
  "isMeetingInviteToCustomersEnabled": "Boolean",
  "maximumAdvance": "String (timestamp)",
  "minimumLeadTime": "String (timestamp)",
  "sendConfirmationsToOwner": "Boolean",
  "timeSlotInterval": "String (timestamp)"
}
```
