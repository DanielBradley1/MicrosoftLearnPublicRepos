<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/booking-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-23 -->

# Use the Microsoft Bookings API in Microsoft Graph for shared bookings

Microsoft Bookings lets enterprise organization and small business owners manage customer bookings and information in shared bookings with minimal setup. A business owner can create one or more businesses, with each business offering a set of services. The owner can set up staff members, and specify the services that each staff member performs. A customer can book an appointment for a specific service in that business in an online or mobile app. Microsoft Bookings ensures that the appointment time is kept up-to-date for the business, staff members, and customers involved.

Important

The Microsoft Bookings API in Microsoft Graph applies only to shared bookings. The API is not applicable for personal bookings.

Programmatically, a [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0) in the Bookings API involves the following objects:

- One or more [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) objects
- One or more [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) objects
- A set of [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) instances
- A set of [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) objects

## Using the Microsoft Bookings REST API

Walk through the following steps before booking customer appointments for a business the first time. Make sure you provide the appropriate [access tokens](https://learn.microsoft.com/en-us/graph/auth/auth-concepts#access-tokens) for the corresponding operations.

1. Make sure the business has an [Microsoft 365 Business Premium](https://products.office.com/en-us/business/office-365-business-premium) subscription.
2. Create a new **bookingBusiness** by sending a POST operation to the entity set. At minimum, you should specify a name for the new business that customers will see:

```http
POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses
Authorization: Bearer {access token}
Content-Type: application/json

{
    "displayName":"Contoso"
}
```

Use the **id** property of the new **bookingBusiness** returned in the POST response to continue to [customize](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-update?view=graph-rest-1.0) business settings, and add staff members and services for the business.

3. Add individual staff members for the business:

```http
POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/{id}/staffMembers
Authorization: Bearer {access token}
Content-Type: application/json

{
    "displayName":"Dana Swope",
    "emailAddress": "danas@contoso.com",
    "role": "externalGuest"
}
```

4. Define each service offered by the business:

```http
POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/{id}/services
Authorization: Bearer {access token}
Content-Type: application/json

{
    "displayName":"Bento"
}
```

5. Publish the scheduling page for the business, to let customers and business operators start booking appointments:

```http
POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/{id}/publish
Authorization: Bearer {access token}
```

In general, to list all the booking businesses in the Microsoft 365 tenant:

```http
GET https://graph.microsoft.com/v1.0/solutions/bookingBusinesses
Authorization: Bearer {access token}
```

## Common use cases

The following table lists the common operations for a business in the Bookings API.

| Use cases | REST resources | See also |
| :--- | :--- | :--- |
| Create, get, update, or delete a business | [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0) | [Methods of bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0#methods) |
| Update the scheduling policy | [bookingSchedulingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/bookingschedulingpolicy?view=graph-rest-1.0) | [Update a bookingBusiness](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-update?view=graph-rest-1.0) |
| Add, get, update, or delete staff members | [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) | [Methods of bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0#methods) |
| Add, get, update, or delete services | [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) | [Methods of bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0#methods) |
| Add, get, update, or delete custom questions | [bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0) | [Methods of bookingCustomQuestion](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomquestion?view=graph-rest-1.0#methods) |
| Add, get, update, or delete customers | [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) | [Methods of bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0#methods) |
| Publish or unpublish the scheduling page | [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0) | [publish](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-publish?view=graph-rest-1.0)  <br>[unpublish](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-unpublish?view=graph-rest-1.0) |
| Create, get, update, delete, or cancel an appointment | [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) | [Methods of bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0#methods) |
| Get appointments in a date range | [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0) | [List Bookings calendarView](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-calendarview?view=graph-rest-1.0) |
| Get currency | [bookingCurrency](https://learn.microsoft.com/en-us/graph/api/resources/bookingcurrency?view=graph-rest-1.0) | [Methods of bookingCurrency](https://learn.microsoft.com/en-us/graph/api/resources/bookingcurrency?view=graph-rest-1.0#methods) |

## Related content

- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
- Learn how to choose [permissions](https://learn.microsoft.com/en-us/graph/permissions-reference) in Microsoft Graph.
