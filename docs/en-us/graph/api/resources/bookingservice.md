<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-31 -->

# bookingService resource type

Namespace: microsoft.graph

Represents information about a particular service provided by a [booking business](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0), such as the service name, price, and the staff that usually provides such service.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-services?view=graph-rest-1.0) | [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) collection | Get a list of **bookingService** objects in the specified [booking business](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0). |
| [Create](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-services?view=graph-rest-1.0) | [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) | Create a **bookingService** for the specified [booking business](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0). |
| [Get](https://learn.microsoft.com/en-us/graph/api/bookingservice-get?view=graph-rest-1.0) | [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) | Get the properties and relationships of a **bookingService** object in the specified [booking business](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0). |
| [Update](https://learn.microsoft.com/en-us/graph/api/bookingservice-update?view=graph-rest-1.0) | None | Update a **bookingService** object in the specified [booking business](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0). |
| [Delete](https://learn.microsoft.com/en-us/graph/api/bookingservice-delete?view=graph-rest-1.0) | None | Delete a **bookingService** object in the specified [booking business](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalInformation | String | Additional information that is sent to the customer when an appointment is confirmed. |
| createdDateTime | DateTimeOffset | The date, time, and time zone when the service was created. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| customQuestions | [bookingQuestionAssignment](https://learn.microsoft.com/en-us/graph/api/resources/bookingquestionassignment?view=graph-rest-1.0) collection | Contains the set of custom questions associated with a particular service. |
| defaultDuration | Duration | The default length of the service, represented in numbers of days, hours, minutes, and seconds. For example, P11D23H59M59.999999999999S. |
| defaultLocation | [location](https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0) | The default physical location for the service. |
| defaultPrice | Double | The default monetary price for the service. |
| defaultPriceType | bookingPriceType | The default way the service is charged. The possible values are: `undefined`, `fixedPrice`, `startingAt`, `hourly`, `free`, `priceVaries`, `callUs`, `notSet`, `unknownFutureValue`. |
| defaultReminders | [bookingReminder](https://learn.microsoft.com/en-us/graph/api/resources/bookingreminder?view=graph-rest-1.0) collection | The default set of reminders for an appointment of this service. The value of this property is available only when reading this **bookingService** by its ID. |
| description | String | A text description for the service. |
| displayName | String | A service name. |
| id | String | The ID of that service, in a GUID format. Read-only. |
| isAnonymousJoinEnabled | Boolean | Indicates if an anonymousJoinWebUrl\(webrtcUrl\) is generated for the appointment booked for this service. The default value is `false`. |
| isCustomerAllowedToManageBooking | Boolean | Indicates that the customer can manage bookings created by the staff. The default value is `false`. |
| isHiddenFromCustomers | Boolean | `True` indicates that this service isn't available to customers for booking. |
| isLocationOnline | Boolean | Indicates that the appointments for the service are held online. The default value is `false`. |
| languageTag | String | The language of the self-service booking page. |
| lastUpdatedDateTime | DateTimeOffset | The date, time, and time zone when the service was last updated. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| maximumAttendeesCount | Int32 | The maximum number of customers allowed in a service. If **maximumAttendeesCount** of the service is greater than 1, pass valid customer IDs while creating or updating an appointment. To create a customer, use the [Create bookingCustomer](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-customers?view=graph-rest-1.0) operation. |
| notes | String | Additional information about this service. |
| postBuffer | Duration | The time to buffer after an appointment for this service ends, and before the next customer appointment can be booked. |
| preBuffer | Duration | The time to buffer before an appointment for this service can start. |
| schedulingPolicy | [bookingSchedulingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/bookingschedulingpolicy?view=graph-rest-1.0) | The set of policies that determine how appointments for this type of service should be created and managed. |
| smsNotificationsEnabled | Boolean | True indicates SMS notifications can be sent to the customers for the appointment of the service. Default value is false. |
| staffMemberIds | String collection | Represents those [staff members](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) who provide this service. |
| webUrl | String | The URL a customer uses to access the service. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.bookingService",
  "additionalInformation": "String",
  "createdDateTime": "String (timestamp)",
  "customQuestions": [{"@odata.type": "microsoft.graph.bookingQuestionAssignment"}],
  "defaultDuration": "String (duration)",
  "defaultLocation": {"@odata.type": "microsoft.graph.location"},
  "defaultPrice": "Double",
  "defaultPriceType": "String",
  "defaultReminders": [{"@odata.type": "microsoft.graph.bookingReminder"}],
  "description": "String",
  "displayName": "String",
  "id": "String (identifier)",
  "isAnonymousJoinEnabled": "Boolean",
  "isCustomerAllowedToManageBooking": "Boolean",
  "isHiddenFromCustomers": "Boolean",
  "isLocationOnline": "Boolean",
  "languageTag": "String",
  "lastUpdatedDateTime": "String (timestamp)",
  "maximumAttendeesCount": "Int32",
  "notes": "String",
  "postBuffer": "String (duration)",
  "preBuffer": "String (duration)",
  "schedulingPolicy": {"@odata.type": "microsoft.graph.bookingSchedulingPolicy"},
  "smsNotificationsEnabled": "Boolean",
  "staffMemberIds": ["String"],
  "webUrl": "String"
}
```
