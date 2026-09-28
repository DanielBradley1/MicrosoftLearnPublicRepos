<!-- Source: https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-bookingbusinesses?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-13 -->

# Create bookingBusiness

Namespace: microsoft.graph

Create a new [Microsoft Bookings business](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0) in a tenant.

This is the first step in setting up a Bookings business where you must specify the business display name. You can include other information such as business address, web site address, and scheduling policy, or set that information later by [updating](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-update?view=graph-rest-1.0) the **bookingBusiness**.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Bookings.Manage.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /solutions/bookingBusinesses
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of a [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and a [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses
Content-type: application/json

{
    "displayName":"Fourth Coffee",
    "address":{
        "postOfficeBox":"P.O. Box 123",
        "street":"4567 Main Street",
        "city":"Buffalo",
        "state":"NY",
        "countryOrRegion":"USA",
        "postalCode":"98052"
    },
    "phone":"206-555-0100",
    "email":"manager@fourthcoffee.com",
    "webSiteUrl":"https://www.fourthcoffee.com",
    "defaultCurrencyIso":"USD"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new BookingBusiness
{
	DisplayName = "Fourth Coffee",
	Address = new PhysicalAddress
	{
		Street = "4567 Main Street",
		City = "Buffalo",
		State = "NY",
		CountryOrRegion = "USA",
		PostalCode = "98052",
		AdditionalData = new Dictionary<string, object>
		{
			{
				"postOfficeBox" , "P.O. Box 123"
			},
		},
	},
	Phone = "206-555-0100",
	Email = "manager@fourthcoffee.com",
	WebSiteUrl = "https://www.fourthcoffee.com",
	DefaultCurrencyIso = "USD",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BookingBusinesses.PostAsync(requestBody);
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

requestBody := graphmodels.NewBookingBusiness()
displayName := "Fourth Coffee"
requestBody.SetDisplayName(&displayName) 
address := graphmodels.NewPhysicalAddress()
street := "4567 Main Street"
address.SetStreet(&street) 
city := "Buffalo"
address.SetCity(&city) 
state := "NY"
address.SetState(&state) 
countryOrRegion := "USA"
address.SetCountryOrRegion(&countryOrRegion) 
postalCode := "98052"
address.SetPostalCode(&postalCode) 
additionalData := map[string]interface{}{
	"postOfficeBox" : "P.O. Box 123", 
}
address.SetAdditionalData(additionalData)
requestBody.SetAddress(address)
phone := "206-555-0100"
requestBody.SetPhone(&phone) 
email := "manager@fourthcoffee.com"
requestBody.SetEmail(&email) 
webSiteUrl := "https://www.fourthcoffee.com"
requestBody.SetWebSiteUrl(&webSiteUrl) 
defaultCurrencyIso := "USD"
requestBody.SetDefaultCurrencyIso(&defaultCurrencyIso) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
bookingBusinesses, err := graphClient.Solutions().BookingBusinesses().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BookingBusiness bookingBusiness = new BookingBusiness();
bookingBusiness.setDisplayName("Fourth Coffee");
PhysicalAddress address = new PhysicalAddress();
address.setStreet("4567 Main Street");
address.setCity("Buffalo");
address.setState("NY");
address.setCountryOrRegion("USA");
address.setPostalCode("98052");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("postOfficeBox", "P.O. Box 123");
address.setAdditionalData(additionalData);
bookingBusiness.setAddress(address);
bookingBusiness.setPhone("206-555-0100");
bookingBusiness.setEmail("manager@fourthcoffee.com");
bookingBusiness.setWebSiteUrl("https://www.fourthcoffee.com");
bookingBusiness.setDefaultCurrencyIso("USD");
BookingBusiness result = graphClient.solutions().bookingBusinesses().post(bookingBusiness);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const bookingBusiness = {
    displayName: 'Fourth Coffee',
    address: {
        postOfficeBox: 'P.O. Box 123',
        street: '4567 Main Street',
        city: 'Buffalo',
        state: 'NY',
        countryOrRegion: 'USA',
        postalCode: '98052'
    },
    phone: '206-555-0100',
    email: 'manager@fourthcoffee.com',
    webSiteUrl: 'https://www.fourthcoffee.com',
    defaultCurrencyIso: 'USD'
};

await client.api('/solutions/bookingBusinesses')
	.post(bookingBusiness);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\BookingBusiness;
use Microsoft\Graph\Generated\Models\PhysicalAddress;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BookingBusiness();
$requestBody->setDisplayName('Fourth Coffee');
$address = new PhysicalAddress();
$address->setStreet('4567 Main Street');
$address->setCity('Buffalo');
$address->setState('NY');
$address->setCountryOrRegion('USA');
$address->setPostalCode('98052');
$additionalData = [
	'postOfficeBox' => 'P.O. Box 123',
];
$address->setAdditionalData($additionalData);
$requestBody->setAddress($address);
$requestBody->setPhone('206-555-0100');
$requestBody->setEmail('manager@fourthcoffee.com');
$requestBody->setWebSiteUrl('https://www.fourthcoffee.com');
$requestBody->setDefaultCurrencyIso('USD');

$result = $graphServiceClient->solutions()->bookingBusinesses()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	displayName = "Fourth Coffee"
	address = @{
		postOfficeBox = "P.O. Box 123"
		street = "4567 Main Street"
		city = "Buffalo"
		state = "NY"
		countryOrRegion = "USA"
		postalCode = "98052"
	}
	phone = "206-555-0100"
	email = "manager@fourthcoffee.com"
	webSiteUrl = "https://www.fourthcoffee.com"
	defaultCurrencyIso = "USD"
}

New-MgBookingBusiness -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.booking_business import BookingBusiness
from msgraph.generated.models.physical_address import PhysicalAddress
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BookingBusiness(
	display_name = "Fourth Coffee",
	address = PhysicalAddress(
		street = "4567 Main Street",
		city = "Buffalo",
		state = "NY",
		country_or_region = "USA",
		postal_code = "98052",
		additional_data = {
				"post_office_box" : "P.O. Box 123",
		}
	),
	phone = "206-555-0100",
	email = "manager@fourthcoffee.com",
	web_site_url = "https://www.fourthcoffee.com",
	default_currency_iso = "USD",
)

result = await graph_client.solutions.booking_businesses.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context":"https://graph.microsoft.com/v1.0/solutions/$metadata#bookingBusinesses/$entity",
    "id":"fourthcoffee@contoso.com",
    "displayName":"Fourth Coffee",
    "businessType":"",
    "phone":"206-555-0100",
    "email":"manager@fourthcoffee.com",
    "webSiteUrl":"https://www.fourthcoffee.com",
    "languageTag":"en-US",
    "defaultCurrencyIso":"USD",
    "isPublished":false,
    "publicUrl":null,
    "address":{
        "postOfficeBox":"P.O. Box 123",
        "street":"4567 Main Street",
        "city":"Buffalo",
        "state":"NY",
        "countryOrRegion":"USA",
        "postalCode":"98052"
    },
    "businessHours":[
        {
            "day":"monday",
            "timeSlots":[
                {
                    "startTime":"08:00:00.0000000",
                    "endTime":"17:00:00.0000000"
                }
            ]
        },
        {
            "day":"tuesday",
            "timeSlots":[
                {
                    "startTime":"08:00:00.0000000",
                    "endTime":"17:00:00.0000000"
                }
            ]
        },
        {
            "day":"wednesday",
            "timeSlots":[
                {
                    "startTime":"08:00:00.0000000",
                    "endTime":"17:00:00.0000000"
                }
            ]
        },
        {
            "day":"thursday",
            "timeSlots":[
                {
                    "startTime":"08:00:00.0000000",
                    "endTime":"17:00:00.0000000"
                }
            ]
        },
        {
            "day":"friday",
            "timeSlots":[
                {
                    "startTime":"08:00:00.0000000",
                    "endTime":"17:00:00.0000000"
                }
            ]
        },
        {
            "day":"saturday",
            "timeSlots":[

            ]
        },
        {
            "day":"sunday",
            "timeSlots":[

            ]
        }
    ],
    "schedulingPolicy":{
        "timeSlotInterval":"PT30M",
        "minimumLeadTime":"P1D",
        "maximumAdvance":"P365D",
        "sendConfirmationsToOwner":true,
        "allowStaffSelection":true
    }
}
```
