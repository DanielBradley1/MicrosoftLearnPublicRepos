<!-- Source: https://learn.microsoft.com/en-us/graph/api/bookingappointment-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-15 -->

# Update bookingAppointment

Namespace: microsoft.graph

Update the properties of a [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) object in the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | BookingsAppointment.ReadWrite.All | Bookings.Manage.All, Bookings.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BookingsAppointment.ReadWrite.All | Bookings.Manage.All, Bookings.Read.All, Bookings.ReadWrite.All |

Note

If you create a custom app using application permissions, you must follow the [Business rules validation](https://learn.microsoft.com/en-us/graph/bookingsbusiness-business-rules).

## HTTP request

```http
PATCH /solutions/bookingBusinesses/{id}/appointments/{id}
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
| customerEmailAddress | String | The SMTP address of the [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) who books the appointment. |
| customerName | String | The customer's name. |
| customerNotes | String | Notes from the customer associated with this appointment. You can get the value only when you read this **bookingAppointment** by its ID. You can set this property only when you initially create an appointment with a new customer. |
| customerPhone | String | The customer's phone number. |
| customers | [bookingCustomerInformation](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomerinformation?view=graph-rest-1.0) collection | It lists down the customer properties for an appointment. An appointment contains a list of customer information and each unit indicates the properties of a customer who is part of that appointment. Optional. |
| customerTimeZone | String | The time zone of the customer. For a list of possible values, see [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0). |
| duration | Duration | The length of the appointment, denoted in [ISO8601](https://www.iso.org/iso-8601-date-and-time-format.html) format. |
| end | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date, time, and time zone that the appointment ends. |
| invoiceStatus | string | The status of the invoice. The possible values are: `draft`, `reviewing`, `open`, `canceled`, `paid`, and `corrective`. |
| isCustomerAllowedToManageBooking | Boolean | Indicates that the customer can manage bookings created by the staff. The default value is `false`. |
| filledAttendeesCount | Int32 | The current number of customers in the appointment. Required. |
| isLocationOnline | Boolean | `True` indicates that the appointment is held online. The default value is `false`. |
| maximumAttendeesCount | Int32 | The maximum number of customers allowed in the appointment. Required. |
| optOutOfCustomerEmail | Boolean | `True` indicates that the [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) for this appointment doesn't wish to receive a confirmation for this appointment. |
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
| smsNotificationsEnabled | Boolean | `True` indicates that SMS notifications are sent to the customers for the appointment. The default value is `false`. |
| staffMemberIds | String collection | The ID of each [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) who is scheduled in this appointment. |
| start | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | The date, time, and time zone when the appointment begins. |

Note

If the maximum number of customers \(**maximumAttedeesCount**\) allowed in the [service](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) is greater than 1:

- Make sure that the customers exist in the Booking Calendar. If they don’t, create using the [Create bookingCustomer](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-customers?view=graph-rest-1.0) operation.
- Pass valid customer IDs when you create or update the appointment. If the customer ID is invalid, that customer won't be included in the appointment object.

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

## Examples

### Example 1: Change the date of service

#### Request

The following example changes the date of service by a day.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/appointments/AAMkADKnAAA=
Content-type: application/json

{
    "@odata.type":"#microsoft.graph.bookingAppointment",
    "end":{
        "@odata.type":"#microsoft.graph.dateTimeTimeZone",
        "dateTime":"2018-05-06T12:30:00.0000000+00:00",
        "timeZone":"UTC"
    },
    "start":{
        "@odata.type":"#microsoft.graph.dateTimeTimeZone",
        "dateTime":"2018-05-06T12:00:00.0000000+00:00",
        "timeZone":"UTC"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new BookingAppointment
{
	OdataType = "#microsoft.graph.bookingAppointment",
	AdditionalData = new Dictionary<string, object>
	{
		{
			"end" , new DateTimeTimeZone
			{
				OdataType = "#microsoft.graph.dateTimeTimeZone",
				DateTime = "2018-05-06T12:30:00.0000000+00:00",
				TimeZone = "UTC",
			}
		},
		{
			"start" , new DateTimeTimeZone
			{
				OdataType = "#microsoft.graph.dateTimeTimeZone",
				DateTime = "2018-05-06T12:00:00.0000000+00:00",
				TimeZone = "UTC",
			}
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BookingBusinesses["{bookingBusiness-id}"].Appointments["{bookingAppointment-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewBookingAppointment()
additionalData := map[string]interface{}{
end := graphmodels.NewDateTimeTimeZone()
dateTime := "2018-05-06T12:30:00.0000000+00:00"
end.SetDateTime(&dateTime) 
timeZone := "UTC"
end.SetTimeZone(&timeZone) 
	requestBody.SetEnd(end)
start := graphmodels.NewDateTimeTimeZone()
dateTime := "2018-05-06T12:00:00.0000000+00:00"
start.SetDateTime(&dateTime) 
timeZone := "UTC"
start.SetTimeZone(&timeZone) 
	requestBody.SetStart(start)
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
appointments, err := graphClient.Solutions().BookingBusinesses().ByBookingBusinessId("bookingBusiness-id").Appointments().ByBookingAppointmentId("bookingAppointment-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BookingAppointment bookingAppointment = new BookingAppointment();
bookingAppointment.setOdataType("#microsoft.graph.bookingAppointment");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
DateTimeTimeZone end = new DateTimeTimeZone();
end.setOdataType("#microsoft.graph.dateTimeTimeZone");
end.setDateTime("2018-05-06T12:30:00.0000000+00:00");
end.setTimeZone("UTC");
additionalData.put("end", end);
DateTimeTimeZone start = new DateTimeTimeZone();
start.setOdataType("#microsoft.graph.dateTimeTimeZone");
start.setDateTime("2018-05-06T12:00:00.0000000+00:00");
start.setTimeZone("UTC");
additionalData.put("start", start);
bookingAppointment.setAdditionalData(additionalData);
BookingAppointment result = graphClient.solutions().bookingBusinesses().byBookingBusinessId("{bookingBusiness-id}").appointments().byBookingAppointmentId("{bookingAppointment-id}").patch(bookingAppointment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const bookingAppointment = {
    '@odata.type':'#microsoft.graph.bookingAppointment',
    end: {
        '@odata.type':'#microsoft.graph.dateTimeTimeZone',
        dateTime: '2018-05-06T12:30:00.0000000+00:00',
        timeZone: 'UTC'
    },
    start: {
        '@odata.type':'#microsoft.graph.dateTimeTimeZone',
        dateTime: '2018-05-06T12:00:00.0000000+00:00',
        timeZone: 'UTC'
    }
};

await client.api('/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/appointments/AAMkADKnAAA=')
	.update(bookingAppointment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\BookingAppointment;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BookingAppointment();
$requestBody->setOdataType('#microsoft.graph.bookingAppointment');
$additionalData = [
	'end' => [
		'@odata.type' => '#microsoft.graph.dateTimeTimeZone',
		'dateTime' => '2018-05-06T12:30:00.0000000+00:00',
		'timeZone' => 'UTC',
	],
	'start' => [
		'@odata.type' => '#microsoft.graph.dateTimeTimeZone',
		'dateTime' => '2018-05-06T12:00:00.0000000+00:00',
		'timeZone' => 'UTC',
	],
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->solutions()->bookingBusinesses()->byBookingBusinessId('bookingBusiness-id')->appointments()->byBookingAppointmentId('bookingAppointment-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	"@odata.type" = "#microsoft.graph.bookingAppointment"
	end = @{
		"@odata.type" = "#microsoft.graph.dateTimeTimeZone"
		dateTime = "2018-05-06T12:30:00.0000000+00:00"
		timeZone = "UTC"
	}
	start = @{
		"@odata.type" = "#microsoft.graph.dateTimeTimeZone"
		dateTime = "2018-05-06T12:00:00.0000000+00:00"
		timeZone = "UTC"
	}
}

Update-MgBookingBusinessAppointment -BookingBusinessId $bookingBusinessId -BookingAppointmentId $bookingAppointmentId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.booking_appointment import BookingAppointment
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BookingAppointment(
	odata_type = "#microsoft.graph.bookingAppointment",
	additional_data = {
			"end" : {
					"@odata_type" : "#microsoft.graph.dateTimeTimeZone",
					"date_time" : "2018-05-06T12:30:00.0000000+00:00",
					"time_zone" : "UTC",
			},
			"start" : {
					"@odata_type" : "#microsoft.graph.dateTimeTimeZone",
					"date_time" : "2018-05-06T12:00:00.0000000+00:00",
					"time_zone" : "UTC",
			},
	}
)

result = await graph_client.solutions.booking_businesses.by_booking_business_id('bookingBusiness-id').appointments.by_booking_appointment_id('bookingAppointment-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Update the customers for an appointment

The following example updates the customers array for a multi-customer appointment. The **customers** property is a full replacement array — include all customers that should be part of the appointment, not just the new ones.

Note

- Each object in the **customers** array must include `@odata.type` set to `#microsoft.graph.bookingCustomerInformation`. Omitting this property causes the request to fail.
- Include customer details such as **name**, **emailAddress**, and **phone** for each entry. The API doesn't automatically populate these fields from the **customerId** — if omitted, they will be blank on the appointment.
- The **customerId** must reference a valid [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) that exists in the Booking Calendar. If it doesn't exist, create one using the [Create bookingCustomer](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-customers?view=graph-rest-1.0) operation.
- The associated [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) must have **maximumAttendeesCount** greater than 1 to support multiple customers.

#### Request

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/appointments/AAMkADKoAAA=
Content-type: application/json

{
    "@odata.type":"#microsoft.graph.bookingAppointment",
    "customers": [
        {
            "@odata.type": "#microsoft.graph.bookingCustomerInformation",
            "customerId": "cd56bb19-c348-42c6-af5c-09818c87fb8c",
            "name": "John Doe",
            "emailAddress": "john.doe@example.com",
            "phone": "313-555-5555"
        },
        {
            "@odata.type": "#microsoft.graph.bookingCustomerInformation",
            "customerId": "72f148fa-9a86-4c59-b277-f5089d9ea0e7",
            "name": "Jane Smith",
            "emailAddress": "jane.smith@example.com",
            "phone": "248-555-5678"
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new BookingAppointment
{
	OdataType = "#microsoft.graph.bookingAppointment",
	Customers = new List<BookingCustomerInformationBase>
	{
		new BookingCustomerInformation
		{
			OdataType = "#microsoft.graph.bookingCustomerInformation",
			CustomerId = "cd56bb19-c348-42c6-af5c-09818c87fb8c",
			Name = "John Doe",
			EmailAddress = "john.doe@example.com",
			Phone = "313-555-5555",
		},
		new BookingCustomerInformation
		{
			OdataType = "#microsoft.graph.bookingCustomerInformation",
			CustomerId = "72f148fa-9a86-4c59-b277-f5089d9ea0e7",
			Name = "Jane Smith",
			EmailAddress = "jane.smith@example.com",
			Phone = "248-555-5678",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BookingBusinesses["{bookingBusiness-id}"].Appointments["{bookingAppointment-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewBookingAppointment()


bookingCustomerInformationBase := graphmodels.NewBookingCustomerInformation()
customerId := "cd56bb19-c348-42c6-af5c-09818c87fb8c"
bookingCustomerInformationBase.SetCustomerId(&customerId) 
name := "John Doe"
bookingCustomerInformationBase.SetName(&name) 
emailAddress := "john.doe@example.com"
bookingCustomerInformationBase.SetEmailAddress(&emailAddress) 
phone := "313-555-5555"
bookingCustomerInformationBase.SetPhone(&phone) 
bookingCustomerInformationBase1 := graphmodels.NewBookingCustomerInformation()
customerId := "72f148fa-9a86-4c59-b277-f5089d9ea0e7"
bookingCustomerInformationBase1.SetCustomerId(&customerId) 
name := "Jane Smith"
bookingCustomerInformationBase1.SetName(&name) 
emailAddress := "jane.smith@example.com"
bookingCustomerInformationBase1.SetEmailAddress(&emailAddress) 
phone := "248-555-5678"
bookingCustomerInformationBase1.SetPhone(&phone) 

customers := []graphmodels.BookingCustomerInformationBaseable {
	bookingCustomerInformationBase,
	bookingCustomerInformationBase1,
}
requestBody.SetCustomers(customers)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
appointments, err := graphClient.Solutions().BookingBusinesses().ByBookingBusinessId("bookingBusiness-id").Appointments().ByBookingAppointmentId("bookingAppointment-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BookingAppointment bookingAppointment = new BookingAppointment();
bookingAppointment.setOdataType("#microsoft.graph.bookingAppointment");
LinkedList<BookingCustomerInformationBase> customers = new LinkedList<BookingCustomerInformationBase>();
BookingCustomerInformation bookingCustomerInformationBase = new BookingCustomerInformation();
bookingCustomerInformationBase.setOdataType("#microsoft.graph.bookingCustomerInformation");
bookingCustomerInformationBase.setCustomerId("cd56bb19-c348-42c6-af5c-09818c87fb8c");
bookingCustomerInformationBase.setName("John Doe");
bookingCustomerInformationBase.setEmailAddress("john.doe@example.com");
bookingCustomerInformationBase.setPhone("313-555-5555");
customers.add(bookingCustomerInformationBase);
BookingCustomerInformation bookingCustomerInformationBase1 = new BookingCustomerInformation();
bookingCustomerInformationBase1.setOdataType("#microsoft.graph.bookingCustomerInformation");
bookingCustomerInformationBase1.setCustomerId("72f148fa-9a86-4c59-b277-f5089d9ea0e7");
bookingCustomerInformationBase1.setName("Jane Smith");
bookingCustomerInformationBase1.setEmailAddress("jane.smith@example.com");
bookingCustomerInformationBase1.setPhone("248-555-5678");
customers.add(bookingCustomerInformationBase1);
bookingAppointment.setCustomers(customers);
BookingAppointment result = graphClient.solutions().bookingBusinesses().byBookingBusinessId("{bookingBusiness-id}").appointments().byBookingAppointmentId("{bookingAppointment-id}").patch(bookingAppointment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const bookingAppointment = {
    '@odata.type':'#microsoft.graph.bookingAppointment',
    customers: [
        {
            '@odata.type': '#microsoft.graph.bookingCustomerInformation',
            customerId: 'cd56bb19-c348-42c6-af5c-09818c87fb8c',
            name: 'John Doe',
            emailAddress: 'john.doe@example.com',
            phone: '313-555-5555'
        },
        {
            '@odata.type': '#microsoft.graph.bookingCustomerInformation',
            customerId: '72f148fa-9a86-4c59-b277-f5089d9ea0e7',
            name: 'Jane Smith',
            emailAddress: 'jane.smith@example.com',
            phone: '248-555-5678'
        }
    ]
};

await client.api('/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/appointments/AAMkADKoAAA=')
	.update(bookingAppointment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\BookingAppointment;
use Microsoft\Graph\Generated\Models\BookingCustomerInformationBase;
use Microsoft\Graph\Generated\Models\BookingCustomerInformation;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BookingAppointment();
$requestBody->setOdataType('#microsoft.graph.bookingAppointment');
$customersBookingCustomerInformationBase1 = new BookingCustomerInformation();
$customersBookingCustomerInformationBase1->setOdataType('#microsoft.graph.bookingCustomerInformation');
$customersBookingCustomerInformationBase1->setCustomerId('cd56bb19-c348-42c6-af5c-09818c87fb8c');
$customersBookingCustomerInformationBase1->setName('John Doe');
$customersBookingCustomerInformationBase1->setEmailAddress('john.doe@example.com');
$customersBookingCustomerInformationBase1->setPhone('313-555-5555');
$customersArray []= $customersBookingCustomerInformationBase1;
$customersBookingCustomerInformationBase2 = new BookingCustomerInformation();
$customersBookingCustomerInformationBase2->setOdataType('#microsoft.graph.bookingCustomerInformation');
$customersBookingCustomerInformationBase2->setCustomerId('72f148fa-9a86-4c59-b277-f5089d9ea0e7');
$customersBookingCustomerInformationBase2->setName('Jane Smith');
$customersBookingCustomerInformationBase2->setEmailAddress('jane.smith@example.com');
$customersBookingCustomerInformationBase2->setPhone('248-555-5678');
$customersArray []= $customersBookingCustomerInformationBase2;
$requestBody->setCustomers($customersArray);


$result = $graphServiceClient->solutions()->bookingBusinesses()->byBookingBusinessId('bookingBusiness-id')->appointments()->byBookingAppointmentId('bookingAppointment-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	"@odata.type" = "#microsoft.graph.bookingAppointment"
	customers = @(
		@{
			"@odata.type" = "#microsoft.graph.bookingCustomerInformation"
			customerId = "cd56bb19-c348-42c6-af5c-09818c87fb8c"
			name = "John Doe"
			emailAddress = "john.doe@example.com"
			phone = "313-555-5555"
		}
		@{
			"@odata.type" = "#microsoft.graph.bookingCustomerInformation"
			customerId = "72f148fa-9a86-4c59-b277-f5089d9ea0e7"
			name = "Jane Smith"
			emailAddress = "jane.smith@example.com"
			phone = "248-555-5678"
		}
	)
}

Update-MgBookingBusinessAppointment -BookingBusinessId $bookingBusinessId -BookingAppointmentId $bookingAppointmentId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.booking_appointment import BookingAppointment
from msgraph.generated.models.booking_customer_information_base import BookingCustomerInformationBase
from msgraph.generated.models.booking_customer_information import BookingCustomerInformation
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BookingAppointment(
	odata_type = "#microsoft.graph.bookingAppointment",
	customers = [
		BookingCustomerInformation(
			odata_type = "#microsoft.graph.bookingCustomerInformation",
			customer_id = "cd56bb19-c348-42c6-af5c-09818c87fb8c",
			name = "John Doe",
			email_address = "john.doe@example.com",
			phone = "313-555-5555",
		),
		BookingCustomerInformation(
			odata_type = "#microsoft.graph.bookingCustomerInformation",
			customer_id = "72f148fa-9a86-4c59-b277-f5089d9ea0e7",
			name = "Jane Smith",
			email_address = "jane.smith@example.com",
			phone = "248-555-5678",
		),
	],
)

result = await graph_client.solutions.booking_businesses.by_booking_business_id('bookingBusiness-id').appointments.by_booking_appointment_id('bookingAppointment-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
