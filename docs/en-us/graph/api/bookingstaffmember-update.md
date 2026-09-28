<!-- Source: https://learn.microsoft.com/en-us/graph/api/bookingstaffmember-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-26 -->

# Update bookingstaffmember

Namespace: microsoft.graph

Update the properties of a [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) in the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0).

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
PATCH /solutions/bookingBusinesses/{id}/staffMembers/{id}
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
| availabilityIsAffectedByPersonalCalendar | Boolean | True means that if the staff member is a Microsoft 365 user, the Microsoft Bookings API uses the staff member's personal calendar in Microsoft 365 as well as the **workingHours** property to determine availability. |
| displayName | String | The name of the staff member, as displayed to customers. |
| emailAddress | String | The email address of the staff member. This can be in the same Microsoft 365 tenant as the business, or in a different email domain. This email address is used if the **sendConfirmationsToOwner** property is set to `true` in the scheduling policy of the business. |
| isEmailNotificationEnabled | Boolean | `True` indicates that a staff member will be notified via email when a booking assigned to them is created or changed. |
| role | bookingStaffRole | The role of the staff member in the business. The possible values are: `guest`, `administrator`, `viewer`, `externalGuest`, `unknownFutureValue`, `scheduler`, `teamMember`. |
| timeZone | String | The time zone of the staff member. For a list of possible values, see [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0). |
| useBusinessHours | Boolean | True means the staff member's availability is determined by the **businessHours** property of the business. False means the availability is determined by the staff member's **workingHouse** property setting. |
| workingHours | [bookingWorkHours](https://learn.microsoft.com/en-us/graph/api/resources/bookingworkhours?view=graph-rest-1.0) collection | The range of hours each day of the week that the staff member is available for booking. |

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

## Example

### Request

The following example changes the staff member's schedule to have Mondays off.

```http
PATCH https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/staffMembers/8ee1c803-a1fa-406d-8259-7ab53233f148
Content-type: application/json

{
    "@odata.type":"#microsoft.graph.bookingStaffMember",
    "workingHours":[
        {
            "@odata.type":"#microsoft.graph.bookingWorkHours",
            "day@odata.type":"#microsoft.graph.dayOfWeek",
            "day":"monday",
            "timeSlots@odata.type":"#Collection(microsoft.graph.bookingWorkTimeSlot)",
            "timeSlots":[

            ]
        },
        {
            "@odata.type":"#microsoft.graph.bookingWorkHours",
            "day@odata.type":"#microsoft.graph.dayOfWeek",
            "day":"tuesday",
            "timeSlots@odata.type":"#Collection(microsoft.graph.bookingWorkTimeSlot)",
            "timeSlots":[
                {
                    "@odata.type":"#microsoft.graph.bookingWorkTimeSlot",
                    "endTime":"17:00:00.0000000",
                    "startTime":"08:00:00.0000000"
                }
            ]
        },
        {
            "@odata.type":"#microsoft.graph.bookingWorkHours",
            "day@odata.type":"#microsoft.graph.dayOfWeek",
            "day":"wednesday",
            "timeSlots@odata.type":"#Collection(microsoft.graph.bookingWorkTimeSlot)",
            "timeSlots":[
                {
                    "@odata.type":"#microsoft.graph.bookingWorkTimeSlot",
                    "endTime":"17:00:00.0000000",
                    "startTime":"08:00:00.0000000"
                }
            ]
        },
        {
            "@odata.type":"#microsoft.graph.bookingWorkHours",
            "day@odata.type":"#microsoft.graph.dayOfWeek",
            "day":"thursday",
            "timeSlots@odata.type":"#Collection(microsoft.graph.bookingWorkTimeSlot)",
            "timeSlots":[
                {
                    "@odata.type":"#microsoft.graph.bookingWorkTimeSlot",
                    "endTime":"17:00:00.0000000",
                    "startTime":"08:00:00.0000000"
                }
            ]
        },
        {
            "@odata.type":"#microsoft.graph.bookingWorkHours",
            "day@odata.type":"#microsoft.graph.dayOfWeek",
            "day":"friday",
            "timeSlots@odata.type":"#Collection(microsoft.graph.bookingWorkTimeSlot)",
            "timeSlots":[
                {
                    "@odata.type":"#microsoft.graph.bookingWorkTimeSlot",
                    "endTime":"17:00:00.0000000",
                    "startTime":"08:00:00.0000000"
                }
            ]
        }
    ]
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
