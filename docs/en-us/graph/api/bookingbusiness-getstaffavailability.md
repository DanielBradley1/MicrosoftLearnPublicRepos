<!-- Source: https://learn.microsoft.com/en-us/graph/api/bookingbusiness-getstaffavailability?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# bookingsBusiness: getStaffAvailability

Namespace: microsoft.graph

Get the availability information of [staff members](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) of a [Microsoft Bookings calendar](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Bookings.Read.All | Bookings.Manage.All, Bookings.ReadWrite.All, Calendars.Read, Calendars.ReadWrite |

## HTTP request

```http
POST /solutions/bookingBusinesses/{id}/getStaffAvailability
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {code}. Required. |
| Content-Type | application/json. Required. |

## Request body

In the request body, pass the list of staff IDs along with two other parameters of [dateTimeTimeZone resource type](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone) called **startDateTime** and **endDateTime**. These correspond to the two timestamps between which the staff availability will be returned.

## Response

If successful, this method returns a `200 OK` response code and a [staffAvailabilityItem](https://learn.microsoft.com/en-us/graph/api/resources/staffavailabilityitem?view=graph-rest-1.0) collection in the response.

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

```http
POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/getStaffAvailability
Content-Type: application/json

{
    "staffIds": [
        "311a5454-08b2-4560-ba1c-f715e938cb79"
    ],
    "startDateTime": {
        "dateTime": "2022-01-25T00:00:00",
        "timeZone": "India Standard Time"
    },
    "endDateTime": {
        "dateTime": "2022-01-26T17:00:00",
        "timeZone": "Pacific Standard Time"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Solutions.BookingBusinesses.Item.GetStaffAvailability;
using Microsoft.Graph.Models;

var requestBody = new GetStaffAvailabilityPostRequestBody
{
	StaffIds = new List<string>
	{
		"311a5454-08b2-4560-ba1c-f715e938cb79",
	},
	StartDateTime = new DateTimeTimeZone
	{
		DateTime = "2022-01-25T00:00:00",
		TimeZone = "India Standard Time",
	},
	EndDateTime = new DateTimeTimeZone
	{
		DateTime = "2022-01-26T17:00:00",
		TimeZone = "Pacific Standard Time",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BookingBusinesses["{bookingBusiness-id}"].GetStaffAvailability.PostAsGetStaffAvailabilityPostResponseAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphsolutions "github.com/microsoftgraph/msgraph-sdk-go/solutions"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphsolutions.NewGetStaffAvailabilityPostRequestBody()
staffIds := []string {
	"311a5454-08b2-4560-ba1c-f715e938cb79",
}
requestBody.SetStaffIds(staffIds)
startDateTime := graphmodels.NewDateTimeTimeZone()
dateTime := "2022-01-25T00:00:00"
startDateTime.SetDateTime(&dateTime) 
timeZone := "India Standard Time"
startDateTime.SetTimeZone(&timeZone) 
requestBody.SetStartDateTime(startDateTime)
endDateTime := graphmodels.NewDateTimeTimeZone()
dateTime := "2022-01-26T17:00:00"
endDateTime.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
endDateTime.SetTimeZone(&timeZone) 
requestBody.SetEndDateTime(endDateTime)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
getStaffAvailability, err := graphClient.Solutions().BookingBusinesses().ByBookingBusinessId("bookingBusiness-id").GetStaffAvailability().PostAsGetStaffAvailabilityPostResponse(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.solutions.bookingbusinesses.item.getstaffavailability.GetStaffAvailabilityPostRequestBody getStaffAvailabilityPostRequestBody = new com.microsoft.graph.solutions.bookingbusinesses.item.getstaffavailability.GetStaffAvailabilityPostRequestBody();
LinkedList<String> staffIds = new LinkedList<String>();
staffIds.add("311a5454-08b2-4560-ba1c-f715e938cb79");
getStaffAvailabilityPostRequestBody.setStaffIds(staffIds);
DateTimeTimeZone startDateTime = new DateTimeTimeZone();
startDateTime.setDateTime("2022-01-25T00:00:00");
startDateTime.setTimeZone("India Standard Time");
getStaffAvailabilityPostRequestBody.setStartDateTime(startDateTime);
DateTimeTimeZone endDateTime = new DateTimeTimeZone();
endDateTime.setDateTime("2022-01-26T17:00:00");
endDateTime.setTimeZone("Pacific Standard Time");
getStaffAvailabilityPostRequestBody.setEndDateTime(endDateTime);
var result = graphClient.solutions().bookingBusinesses().byBookingBusinessId("{bookingBusiness-id}").getStaffAvailability().post(getStaffAvailabilityPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const staffAvailabilityItem = {
    staffIds: [
        '311a5454-08b2-4560-ba1c-f715e938cb79'
    ],
    startDateTime: {
        dateTime: '2022-01-25T00:00:00',
        timeZone: 'India Standard Time'
    },
    endDateTime: {
        dateTime: '2022-01-26T17:00:00',
        timeZone: 'Pacific Standard Time'
    }
};

await client.api('/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/getStaffAvailability')
	.post(staffAvailabilityItem);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Solutions\BookingBusinesses\Item\GetStaffAvailability\GetStaffAvailabilityPostRequestBody;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new GetStaffAvailabilityPostRequestBody();
$requestBody->setStaffIds(['311a5454-08b2-4560-ba1c-f715e938cb79', 	]);
$startDateTime = new DateTimeTimeZone();
$startDateTime->setDateTime('2022-01-25T00:00:00');
$startDateTime->setTimeZone('India Standard Time');
$requestBody->setStartDateTime($startDateTime);
$endDateTime = new DateTimeTimeZone();
$endDateTime->setDateTime('2022-01-26T17:00:00');
$endDateTime->setTimeZone('Pacific Standard Time');
$requestBody->setEndDateTime($endDateTime);

$result = $graphServiceClient->solutions()->bookingBusinesses()->byBookingBusinessId('bookingBusiness-id')->getStaffAvailability()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	staffIds = @(
	"311a5454-08b2-4560-ba1c-f715e938cb79"
)
startDateTime = @{
	dateTime = "2022-01-25T00:00:00"
	timeZone = "India Standard Time"
}
endDateTime = @{
	dateTime = "2022-01-26T17:00:00"
	timeZone = "Pacific Standard Time"
}
}

Get-MgBookingBusinessStaffAvailability -BookingBusinessId $bookingBusinessId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.solutions.bookingbusinesses.item.get_staff_availability.get_staff_availability_post_request_body import GetStaffAvailabilityPostRequestBody
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = GetStaffAvailabilityPostRequestBody(
	staff_ids = [
		"311a5454-08b2-4560-ba1c-f715e938cb79",
	],
	start_date_time = DateTimeTimeZone(
		date_time = "2022-01-25T00:00:00",
		time_zone = "India Standard Time",
	),
	end_date_time = DateTimeTimeZone(
		date_time = "2022-01-26T17:00:00",
		time_zone = "Pacific Standard Time",
	),
)

result = await graph_client.solutions.booking_businesses.by_booking_business_id('bookingBusiness-id').get_staff_availability.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "staffAvailabilityItem": [
        {
            "staffId": "311a5454-08b2-4560-ba1c-f715e938cb79",
            "availabilityItems": [
                {
                    "status": "Available",
                    "startDateTime": {
                        "dateTime": "2022-01-24T08:00:00",
                        "timeZone": "(UTC-08:00) Pacific Time (US & Canada)"
                    },
                    "endDateTime": {
                        "dateTime": "2022-01-24T15:00:00",
                        "timeZone": "(UTC-08:00) Pacific Time (US & Canada)"
                    },
                    "serviceId": ""
                },
                {
                    "status": "Busy",
                    "startDateTime": {
                        "dateTime": "2022-01-24T15:00:00",
                        "timeZone": "(UTC-08:00) Pacific Time (US & Canada)"
                    },
                    "endDateTime": {
                        "dateTime": "2022-01-24T16:00:00",
                        "timeZone": "(UTC-08:00) Pacific Time (US & Canada)"
                    },
                    "serviceId": "57da6774-a087-4d69-b0e6-6fb82c339976"
                },
                {
                    "status": "Available",
                    "startDateTime": {
                        "dateTime": "2022-01-24T16:00:00",
                        "timeZone": "(UTC-08:00) Pacific Time (US & Canada)"
                    },
                    "endDateTime": {
                        "dateTime": "2022-01-24T17:00:00",
                        "timeZone": "(UTC-08:00) Pacific Time (US & Canada)"
                    },
                    "serviceId": ""
                },
                {
                    "status": "Available",
                    "startDateTime": {
                        "dateTime": "2022-01-25T08:00:00",
                        "timeZone": "(UTC-08:00) Pacific Time (US & Canada)"
                    },
                    "endDateTime": {
                        "dateTime": "2022-01-25T17:00:00",
                        "timeZone": "(UTC-08:00) Pacific Time (US & Canada)"
                    },
                    "serviceId": ""
                },
                {
                    "status": "Available",
                    "startDateTime": {
                        "dateTime": "2022-01-26T08:00:00",
                        "timeZone": "(UTC-08:00) Pacific Time (US & Canada)"
                    },
                    "endDateTime": {
                        "dateTime": "2022-01-26T17:00:00",
                        "timeZone": "(UTC-08:00) Pacific Time (US & Canada)"
                    },
                    "serviceId": ""
                }
            ]
        }
    ]
}
```
