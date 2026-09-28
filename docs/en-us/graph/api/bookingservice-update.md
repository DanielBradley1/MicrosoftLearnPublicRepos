<!-- Source: https://learn.microsoft.com/en-us/graph/api/bookingservice-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update bookingservice

Namespace: microsoft.graph

Update the properties of a [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) object in the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0).

The following are some examples you can customize for a service:

- Price
- Typical length of an appointment
- Reminders
- Any time buffer to set up before or finish up after the service
- [Scheduling policy](https://learn.microsoft.com/en-us/graph/api/resources/bookingschedulingpolicy?view=graph-rest-1.0) parameters, such as minimum notice to book or cancel, and whether customers can select specific staff members for an appointment.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Bookings.ReadWrite.All | Bookings.Manage.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Bookings.ReadWrite.All | Bookings.Manage.All |

## HTTP request

```http
PATCH /solutions/bookingBusinesses/{id}/services/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {code}. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| customQuestions | [bookingQuestionAssignment](https://learn.microsoft.com/en-us/graph/api/resources/bookingquestionassignment?view=graph-rest-1.0) collection | This contains a set of custom questions associated with a particular service. Optional. |
| defaultDuration | Duration | The default length of the service represented in numbers of days, hours, minutes, and seconds. For example, P11D23H59M59.999999999999S. |
| defaultLocation | [location](https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0) | The default physical location for the service. |
| defaultPrice | Double | The default monetary price for the service. |
| defaultPriceType | bookingPriceType | The default way the service is charged. The possible values are: `undefined`, `fixedPrice`, `startingAt`, `hourly`, `free`, `priceVaries`, `callUs`, `notSet`, `unknownFutureValue`. |
| defaultReminders | [bookingReminder](https://learn.microsoft.com/en-us/graph/api/resources/bookingreminder?view=graph-rest-1.0) collection | The default set of reminders for an appointment of this service. The value of this property is available only when reading this **bookingService** by its ID. |
| description | String | A text description for the service. |
| displayName | String | A service name. |
| id | String | The unique identifier for the **bookingService**. Read-only. |
| isAnonymousJoinEnabled | Boolean | `True` if the URL to join the appointment anonymously \(**anonymousJoinWebUrl**\) is generated for the appointment booked for this service. |
| isCustomerAllowedToManageBooking | Boolean | Indicates that the customer can manage bookings created by the staff. The default value is `false`. |
| isHiddenFromCustomers | Boolean | `True` indicates that the service isn't available to customers for booking. |
| isLocationOnline | Boolean | `True` indicates that the appointments for the service are held online. The default value is `false`. |
| languageTag | String | The language of the self-service booking page. |
| maximumAttendeesCount | Int32 | The maximum number of customers allowed in a service. |
| notes | String | Additional information about this service. |
| postBuffer | Duration | The time to buffer after an appointment for this service ends, and before the next customer appointment can be booked. |
| preBuffer | Duration | The time to buffer before an appointment for this service can start. |
| schedulingPolicy | [bookingSchedulingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/bookingschedulingpolicy?view=graph-rest-1.0) | The set of policies that determine how appointments for this type of service should be created and managed. |
| smsNotificationsEnabled | Boolean | `True` indicates that SMS notifications can be sent to the customers for the appointment of the service. The default value is `false`. |
| staffMemberIds | String collection | Represents those [staff members](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) who provide this service. |

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

## Example

### Request

The following example updates the duration of the specified service.

```http
PATCH https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/services/57da6774-a087-4d69-b0e6-6fb82c339976
Content-type: application/json

{
    "@odata.type":"#microsoft.graph.bookingService",
    "defaultDuration":"PT30M"
}
```

### Response

The The following example shows the response.

```http
HTTP/1.1 204 No Content
```
