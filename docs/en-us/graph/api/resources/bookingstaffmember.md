<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# bookingStaffMember resource type

Namespace: microsoft.graph

Represents a staff member who provides services in a [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0).

Staff members can be part of the Microsoft 365 tenant where the **booking business** is configured, or they can use email services from other email providers.

When booking appointments, the Bookings API considers the following settings to determine a staff member's availability:

1. By default, the hours of operation of the business \(the **businessHours** property of the [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0) entity\) represent the general availability of the staff member.
2. If **useBusinessHours** is false, then the staff member's specific work hours \(**workingHours** property of the **bookingStaffmember** entity\) represent that member's general availability.
3. If **availabilityIsAffectedByPersonalCalendar** is true, then the Bookings API would first look at the staff member's generally available hours \(as determined by either #1 or #2\), and verify availability during those hours in the staff member's personal calendar, before making a booking.

Inherits from [bookingStaffMemberBase](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmemberbase?view=graph-rest-1.0).

Microsoft Bookings supports a maximum of 100 staff members in a booking calendar.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-staffmembers?view=graph-rest-1.0) | [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) collection | Get a list of **bookingStaffMember** objects in the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-staffmembers?view=graph-rest-1.0) | [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) collection | Create a new **bookingStaffMember** in the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/bookingstaffmember-get?view=graph-rest-1.0) | [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) | Get the properties and relationships of a **bookingStaffMember** in the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0). |
| [Update](https://learn.microsoft.com/en-us/graph/api/bookingstaffmember-update?view=graph-rest-1.0) | None | Update the properties of a **bookingStaffMember** in the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/bookingstaffmember-delete?view=graph-rest-1.0) | None | Delete a staff member in the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| availabilityIsAffectedByPersonalCalendar | Boolean | True means that if the staff member is a Microsoft 365 user, the Bookings API would verify the staff member's availability in their personal calendar in Microsoft 365, before making a booking. |
| createdDateTime | DateTimeOffset | The date, time, and time zone when the staff member was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| displayName | String | The name of the staff member, as displayed to customers. Required. |
| emailAddress | String | The email address of the staff member. This email address can be in the same Microsoft 365 tenant as the business, or in a different email domain. This email address can be used if the **sendConfirmationsToOwner** property is set to true in the scheduling policy of the business. Required. |
| id | String | The ID of the staff member, in a GUID format. Read-only. |
| isEmailNotificationEnabled | Boolean | Indicates that a staff member is notified via email when a booking assigned to them is created or changed. The default value is `true`. |
| membershipStatus | bookingStaffMembershipStatus | The membership status of the staff member in the business. The possible values are: `active`, `pendingAcceptance`, `rejectedByStaff`, `unknownFutureValue`. |
| lastUpdatedDateTime | DateTimeOffset | The date, time, and time zone when the staff member was last updated. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| role | bookingStaffRole | The role of the staff member in the business. The possible values are: `guest`, `administrator`, `viewer`, `externalGuest`, `unknownFutureValue`, `scheduler`, `teamMember`. You must use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `scheduler`, `teamMember`. Required. |
| timeZone | String | The time zone of the staff member. For a list of possible values, see [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0). |
| useBusinessHours | Boolean | True means the staff member's availability is as specified in the **businessHours** property of the business. False means the availability is determined by the staff member's **workingHours** property setting. |
| workingHours | [bookingWorkHours](https://learn.microsoft.com/en-us/graph/api/resources/bookingworkhours?view=graph-rest-1.0) collection | The range of hours each day of the week that the staff member is available for booking. By default, they're initialized to be the same as the **businessHours** property of the business. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.bookingStaffMember",
  "availabilityIsAffectedByPersonalCalendar": "Boolean",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "emailAddress": "String",
  "id": "String (identifier)",
  "isEmailNotificationEnabled": "Boolean",
  "lastUpdatedDateTime": "String (timestamp)",
  "role": "String",
  "timeZone": "String",
  "useBusinessHours": "Boolean",
  "workingHours": [{"@odata.type": "microsoft.graph.bookingWorkHours"}]
}
```
