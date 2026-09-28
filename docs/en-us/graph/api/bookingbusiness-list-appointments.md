<!-- Source: https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-appointments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# List appointments

Namespace: microsoft.graph

Get a list of [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) objects for the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Bookings.Read.All | BookingsAppointment.ReadWrite.All, Bookings.Manage.All, Bookings.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | BookingsAppointment.ReadWrite.All | Bookings.Manage.All, Bookings.Read.All, Bookings.ReadWrite.All |

## HTTP request

```http
GET /solutions/bookingBusinesses/{id}/appointments
```

## Optional query parameters

This method supports the $count and $expand [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

To get the set of appointments of a Microsoft Bookings business within a date range, instead of `$filter`, [get the calendarView](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-list-calendarview?view=graph-rest-1.0) for that date range.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {code}. Required. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) objects in the response body.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/appointments
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BookingBusinesses["{bookingBusiness-id}"].Appointments.GetAsync();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
appointments, err := graphClient.Solutions().BookingBusinesses().ByBookingBusinessId("bookingBusiness-id").Appointments().Get(context.Background(), nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BookingAppointmentCollectionResponse result = graphClient.solutions().bookingBusinesses().byBookingBusinessId("{bookingBusiness-id}").appointments().get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let appointments = await client.api('/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/appointments')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->solutions()->bookingBusinesses()->byBookingBusinessId('bookingBusiness-id')->appointments()->get()->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

Get-MgBookingBusinessAppointment -BookingBusinessId $bookingBusinessId
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.solutions.booking_businesses.by_booking_business_id('bookingBusiness-id').appointments.get()
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/solutions/$metadata#bookingBusinesses('Contosolunchdelivery%40contoso.com')/appointments",
    "value": [
        {
            "id": "AAMkADKoAAA=",
            "selfServiceAppointmentId": "00000000-0000-0000-0000-000000000000",
            "isLocationOnline": true,
	    "customerName": "Jordan Miller",
	    "customerEmailAddress": "jordanm@contoso.com",
	    "customerPhone": "213-555-0199",
	    "customerNotes": null,	
            "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTlhZTE3MDUtODk0Yy00MGZkLTlhNzktN2FmYTk3MDUxNmE2%40thread.v2/0?context=%7b%22Tid%22%3a%22995fa18c-b557-4694-8d07-b89779d6dc77%22%2c%22Oid%22%3a%22d4d260ab-989d-490e-b121-e2066391807a%22%7d",
            "customers": [
                {
                    "@odata.type": "#microsoft.graph.bookingCustomerInformation",
                    "customerId": "829e3cb5-3d4d-4319-a8de-1953aedaa166",
                    "name": "Bob Kelly",
                    "emailAddress": "bobk@tailspintoys.com",
                    "phone": "213-555-0108",
                    "notes": null,
                    "location": {
                        "displayName": "Customer",
                        "locationEmailAddress": null,
                        "locationUri": "",
                        "locationType": null,
                        "uniqueId": null,
                        "uniqueIdType": null,
                        "address": {
                            "street": "",
                            "city": "",
                            "state": "",
                            "countryOrRegion": "",
                            "postalCode": ""
                        },
                        "coordinates": {
                            "altitude": null,
                            "latitude": null,
                            "longitude": null,
                            "accuracy": null,
                            "altitudeAccuracy": null
                        }
                    },
                    "timeZone": "America/Chicago"
                }
            ],
            "customerTimeZone": "America/Chicago",
            "customerName": "Bob Kelly",
            "customerEmailAddress": "bobk@tailspintoys.com",
            "customerPhone": "213-555-0103",
            "customerNotes": "This is a test note",
            "smsNotificationsEnabled": true,
            "serviceId": "57da6774-a087-4d69-b0e6-6fb82c339976",
            "serviceName": "Catered bento",
            "duration": "PT30M",
            "preBuffer": "PT5M",
            "postBuffer": "PT10M",
            "priceType": "fixedPrice",
            "price": 10.0,
            "serviceNotes": null,
            "optOutOfCustomerEmail": false,
            "anonymousJoinWebUrl": null,
            "staffMemberIds": [],
            "start": {
                "dateTime": "2018-04-30T13:00:00.0000000Z",
                "timeZone": "UTC"
            },
            "end": {
                "dateTime": "2018-04-30T13:30:00.0000000Z",
                "timeZone": "UTC"
            },
            "serviceLocation": {
                "displayName": "Customer location (987 Third Avenue, Buffalo, NY 98052, USA)",
                "locationEmailAddress": null,
                "locationUri": "",
                "locationType": null,
                "uniqueId": null,
                "uniqueIdType": null,
                "address": {
                    "street": "",
                    "city": "",
                    "state": "",
                    "countryOrRegion": "",
                    "postalCode": ""
                },
                "coordinates": {
                    "altitude": null,
                    "latitude": null,
                    "longitude": null,
                    "accuracy": null,
                    "altitudeAccuracy": null
                }
            },
            "reminders": []
        },
        {
            "id": "AAMkADKnAAA=",
            "selfServiceAppointmentId": "00000000-0000-0000-0000-000000000000",
            "isLocationOnline": true,
            "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MDUtODk0Yy00MGZkLTlhNzktN2xNmE2%40thread.v2/0?context=%7b%22Tid%22%3a%22995fa18c-b557-4694-8d07-b89779d6dc77%22%2c%22Oid%22%3a%22d4d260ab-989d-490e-b121-e2066391807a%22%7d",
            "maximumAttendeesCount": 5,
            "filledAttendeesCount": 1,
            "customers": [
                {
                    "@odata.type": "#microsoft.graph.bookingCustomerInformation",
                    "customerId": "7ed53fa5-9ef2-4f2f-975b-27447440bc09",
                    "name": "Jordan Miller",
                    "emailAddress": "jordanm@contoso.com",
                    "phone": "213-555-0199",
                    "notes": null,
                    "location": {
                        "displayName": "Customer",
                        "locationEmailAddress": null,
                        "locationUri": "",
                        "locationType": null,
                        "uniqueId": null,
                        "uniqueIdType": null,
                        "address": {
                            "street": "",
                            "city": "",
                            "state": "",
                            "countryOrRegion": "",
                            "postalCode": ""
                        },
                        "coordinates": {
                            "altitude": null,
                            "latitude": null,
                            "longitude": null,
                            "accuracy": null,
                            "altitudeAccuracy": null
                        }
                    },
                    "timeZone": "America/Chicago",
                    "customQuestionAnswers": [
                        {
                            "questionId": "3bc6fde0-4ad3-445d-ab17-0fc15dba0774",
                            "question": "What is your age?",
                            "answerInputType": "text",
                            "answerOptions": [],
                            "isRequired": true,
                            "answer": "25",
                            "selectedOptions": []
                        }
                    ]
                }
            ],
            "customerTimeZone": "America/Chicago",
            "smsNotificationsEnabled": true,
            "serviceId": "57da6774-a087-4d69-b0e6-6fb82c339976",
            "serviceName": "Catered bento",
            "duration": "PT30M",
            "preBuffer": "PT5M",
            "postBuffer": "PT10M",
            "priceType": "fixedPrice",
            "price": 10.0,
            "serviceNotes": null,
            "optOutOfCustomerEmail": false,
            "anonymousJoinWebUrl": null,
            "staffMemberIds": [],
            "isCustomerAllowedToManageBooking": true,
            "start": {
                "dateTime": "2018-05-01T12:00:00.0000000Z",
                "timeZone": "UTC"
            },
            "end": {
                "dateTime": "2018-05-01T12:30:00.0000000Z",
                "timeZone": "UTC"
            },
            "serviceLocation": {
                "displayName": "Customer location (123 First Avenue, Buffalo, NY 98052, USA)",
                "locationEmailAddress": null,
                "locationUri": "",
                "locationType": null,
                "uniqueId": null,
                "uniqueIdType": null,
                "address": {
                    "street": "",
                    "city": "",
                    "state": "",
                    "countryOrRegion": "",
                    "postalCode": ""
                },
                "coordinates": {
                    "altitude": null,
                    "latitude": null,
                    "longitude": null,
                    "accuracy": null,
                    "altitudeAccuracy": null
                }
            },
            "reminders": []
        }
    ]
}
```
