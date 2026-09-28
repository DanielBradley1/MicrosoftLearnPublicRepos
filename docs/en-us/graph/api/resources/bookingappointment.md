<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# bookingAppointment resource type

Namespace: microsoft.graph

Represents a customer appointment for a [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0), performed by a set of staff members, provided by a Microsoft Bookings business.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-appointments?view=graph-rest-1.0) | [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) collection | Get a list of **bookingAppointment** objects in the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-appointments?view=graph-rest-1.0) | [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) | Create a new **bookingAppointment** for the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/bookingappointment-get?view=graph-rest-1.0) | [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) | Read the properties and relationships of **bookingAppointment** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/bookingappointment-update?view=graph-rest-1.0) | [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) | Update a **bookingAppointment** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/bookingappointment-delete?view=graph-rest-1.0) | None | Delete a **bookingAppointment** object. |
| [Cancel appointment](https://learn.microsoft.com/en-us/graph/api/bookingappointment-cancel?view=graph-rest-1.0) | None | Cancel a **bookingAppointment** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalInformation | String | Additional information that is sent to the customer when an appointment is confirmed. |
| anonymousJoinWebUrl | String | The URL of the meeting to join anonymously. |
| appointmentLabel | String | The custom label that can be stamped on this appointment by users. |
| createdDateTime | DateTimeOffset | The date, time, and time zone when the appointment was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| customerEmailAddress | String | The SMTP address of the [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) who books the appointment. |
| customerName | String | The customer's name. |
| customerNotes | String | Notes from the customer associated with this appointment. You can get the value only when you read this **bookingAppointment** by its ID. You can set this property only when you initially create an appointment with a new customer. |
| customerPhone | String | The customer's phone number. |
| customers | [bookingCustomerInformation](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomerinformation?view=graph-rest-1.0) collection | A collection of customer properties for an appointment. An appointment contains a list of customer information and each unit will indicate the properties of a customer who is part of that appointment. Optional. |
| customerTimeZone | String | The time zone of the customer. For a list of possible values, see [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0). |
| duration | Duration | The length of the appointment, denoted in [ISO8601](https://www.iso.org/iso-8601-date-and-time-format.html) format. |
| end | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date, time, and time zone when the appointment ends. |
| filledAttendeesCount | Int32 | The current number of customers in the appointment. |
| id | String | The ID of the **bookingAppointment**. Read-only. |
| isCustomerAllowedToManageBooking | Boolean | Indicates that the customer can manage bookings created by the staff. The default value is `false`. |
| isLocationOnline | Boolean | Indicates that the appointment is held online. The default value is `false`. |
| joinWebUrl | String | The URL of the online meeting for the appointment. |
| lastUpdatedDateTime | DateTimeOffset | The date, time, and time zone when the booking business was last updated. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| maximumAttendeesCount | Int32 | The maximum number of customers allowed in an appointment. If **maximumAttendeesCount** of the service is greater than 1, pass valid customer IDs while creating or updating an appointment. To create a customer, use the [Create bookingCustomer](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-customers?view=graph-rest-1.0) operation. |
| optOutOfCustomerEmail | Boolean | If `true` indicates that the [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) for this appointment doesn't wish to receive a confirmation for this appointment. |
| postBuffer | Duration | The amount of time to reserve after the appointment ends, for cleaning up, as an example. The value is expressed in [ISO8601](https://www.iso.org/iso-8601-date-and-time-format.html) format. |
| preBuffer | Duration | The amount of time to reserve before the appointment begins, for preparation, as an example. The value is expressed in [ISO8601](https://www.iso.org/iso-8601-date-and-time-format.html) format. |
| price | Double | The regular price for an appointment for the specified [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0). |
| priceType | bookingPriceType | A setting to provide flexibility for the pricing structure of services. The possible values are: `undefined`, `fixedPrice`, `startingAt`, `hourly`, `free`, `priceVaries`, `callUs`, `notSet`, `unknownFutureValue`. |
| reminders | [bookingReminder](https://learn.microsoft.com/en-us/graph/api/resources/bookingreminder?view=graph-rest-1.0) collection | The collection of customer reminders sent for this appointment. The value of this property is available only when reading this **bookingAppointment** by its ID. |
| selfServiceAppointmentId | String | Another tracking ID for the appointment, if the appointment was created directly by the customer on the scheduling page, as opposed to by a staff member on behalf of the customer. |
| serviceId | String | The ID of the [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) associated with this appointment. |
| serviceLocation | [location](https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0) | The location where the service is delivered. |
| serviceName | String | The name of the **bookingService** associated with this appointment.  <br>This property is optional when creating a new appointment. If not specified, it's computed from the service associated with the appointment by the **serviceId** property. |
| serviceNotes | String | Notes from a [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0). The value of this property is available only when reading this **bookingAppointment** by its ID. |
| smsNotificationsEnabled | Boolean | If `true`, indicates SMS notifications will be sent to the customers for the appointment. Default value is `false`. |
| staffMemberIds | String collection | The ID of each [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) who is scheduled in this appointment. |
| start | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date, time, and time zone when the appointment begins. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.bookingAppointment",
  "additionalInformation": "String",
  "anonymousJoinWebUrl": "String",
  "appointmentLabel": "String",
  "createdDateTime": "String (timestamp)",
  "customerEmailAddress": "String",
  "customerName": "String",
  "customerNotes": "String",
  "customerPhone": "String",
  "customers": [{"@odata.type": "microsoft.graph.bookingCustomerInformation"}],
  "customerTimeZone": "String",
  "duration": "String (duration)",
  "end": {"@odata.type": "microsoft.graph.dateTimeTimeZone"},
  "filledAttendeesCount": "Int32",
  "id": "String (identifier)",
  "isCustomerAllowedToManageBooking": "Boolean",
  "isLocationOnline": "Boolean",
  "joinWebUrl": "String",
  "lastUpdatedDateTime": "String (timestamp)",
  "maximumAttendeesCount": "Int32",
  "optOutOfCustomerEmail": "Boolean",
  "postBuffer": "String (duration)",
  "preBuffer": "String (duration)",
  "price": "Double",
  "priceType": "String",
  "reminders": [{"@odata.type": "microsoft.graph.bookingReminder"}],
  "selfServiceAppointmentId": "String",
  "serviceId": "String",
  "serviceLocation": {"@odata.type": "microsoft.graph.location"},
  "serviceName": "String",
  "serviceNotes": "String",
  "smsNotificationsEnabled": "Boolean",
  "staffMemberIds": ["String"],
  "start": {"@odata.type": "microsoft.graph.dateTimeTimeZone"}
}
```
