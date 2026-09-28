<!-- Source: https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-customers?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create bookingCustomer

Namespace: microsoft.graph

Create a new [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) object.

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
| Application | BookingsAppointment.ReadWrite.All | Bookings.Manage.All, Bookings.ReadWrite.All |

## HTTP request

```http
POST /solutions/bookingBusinesses/{id}/customers
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {code}. Required. |

## Request body

In the request body, supply a JSON representation of a [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and a [bookingCustomer](https://learn.microsoft.com/en-us/graph/api/resources/bookingcustomer?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/customers
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.bookingCustomer",
    "displayName": "Joni Sherman",
    "emailAddress": "jonis@relecloud.com",
    "addresses": [
        {
            "postOfficeBox":"",
            "street":"4567 Main Street",
            "city":"Buffalo",
            "state":"NY",
            "countryOrRegion":"USA",
            "postalCode":"98052",
            "type":"home"
        },
        {
            "postOfficeBox":"",
            "street":"4570 Main Street",
            "city":"Buffalo",
            "state":"NY",
            "countryOrRegion":"USA",
            "postalCode":"98054",
            "type":"business"
        }
    ],
    "phones": [
        {
            "number": "206-555-0100",
            "type": "home"
        },
        {
            "number": "206-555-0200",
            "type": "business"
        }
     ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new BookingCustomer
{
	OdataType = "#microsoft.graph.bookingCustomer",
	DisplayName = "Joni Sherman",
	EmailAddress = "jonis@relecloud.com",
	Addresses = new List<PhysicalAddress>
	{
		new PhysicalAddress
		{
			Street = "4567 Main Street",
			City = "Buffalo",
			State = "NY",
			CountryOrRegion = "USA",
			PostalCode = "98052",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"postOfficeBox" , ""
				},
				{
					"type" , "home"
				},
			},
		},
		new PhysicalAddress
		{
			Street = "4570 Main Street",
			City = "Buffalo",
			State = "NY",
			CountryOrRegion = "USA",
			PostalCode = "98054",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"postOfficeBox" , ""
				},
				{
					"type" , "business"
				},
			},
		},
	},
	Phones = new List<Phone>
	{
		new Phone
		{
			Number = "206-555-0100",
			Type = PhoneType.Home,
		},
		new Phone
		{
			Number = "206-555-0200",
			Type = PhoneType.Business,
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BookingBusinesses["{bookingBusiness-id}"].Customers.PostAsync(requestBody);
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

requestBody := graphmodels.NewBookingCustomerBase()
displayName := "Joni Sherman"
requestBody.SetDisplayName(&displayName) 
emailAddress := "jonis@relecloud.com"
requestBody.SetEmailAddress(&emailAddress) 


physicalAddress := graphmodels.NewPhysicalAddress()
street := "4567 Main Street"
physicalAddress.SetStreet(&street) 
city := "Buffalo"
physicalAddress.SetCity(&city) 
state := "NY"
physicalAddress.SetState(&state) 
countryOrRegion := "USA"
physicalAddress.SetCountryOrRegion(&countryOrRegion) 
postalCode := "98052"
physicalAddress.SetPostalCode(&postalCode) 
additionalData := map[string]interface{}{
	"postOfficeBox" : "", 
	"type" : "home", 
}
physicalAddress.SetAdditionalData(additionalData)
physicalAddress1 := graphmodels.NewPhysicalAddress()
street := "4570 Main Street"
physicalAddress1.SetStreet(&street) 
city := "Buffalo"
physicalAddress1.SetCity(&city) 
state := "NY"
physicalAddress1.SetState(&state) 
countryOrRegion := "USA"
physicalAddress1.SetCountryOrRegion(&countryOrRegion) 
postalCode := "98054"
physicalAddress1.SetPostalCode(&postalCode) 
additionalData := map[string]interface{}{
	"postOfficeBox" : "", 
	"type" : "business", 
}
physicalAddress1.SetAdditionalData(additionalData)

addresses := []graphmodels.PhysicalAddressable {
	physicalAddress,
	physicalAddress1,
}
requestBody.SetAddresses(addresses)


phone := graphmodels.NewPhone()
number := "206-555-0100"
phone.SetNumber(&number) 
type := graphmodels.HOME_PHONETYPE 
phone.SetType(&type) 
phone1 := graphmodels.NewPhone()
number := "206-555-0200"
phone1.SetNumber(&number) 
type := graphmodels.BUSINESS_PHONETYPE 
phone1.SetType(&type) 

phones := []graphmodels.Phoneable {
	phone,
	phone1,
}
requestBody.SetPhones(phones)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
customers, err := graphClient.Solutions().BookingBusinesses().ByBookingBusinessId("bookingBusiness-id").Customers().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BookingCustomer bookingCustomerBase = new BookingCustomer();
bookingCustomerBase.setOdataType("#microsoft.graph.bookingCustomer");
bookingCustomerBase.setDisplayName("Joni Sherman");
bookingCustomerBase.setEmailAddress("jonis@relecloud.com");
LinkedList<PhysicalAddress> addresses = new LinkedList<PhysicalAddress>();
PhysicalAddress physicalAddress = new PhysicalAddress();
physicalAddress.setStreet("4567 Main Street");
physicalAddress.setCity("Buffalo");
physicalAddress.setState("NY");
physicalAddress.setCountryOrRegion("USA");
physicalAddress.setPostalCode("98052");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("postOfficeBox", "");
additionalData.put("type", "home");
physicalAddress.setAdditionalData(additionalData);
addresses.add(physicalAddress);
PhysicalAddress physicalAddress1 = new PhysicalAddress();
physicalAddress1.setStreet("4570 Main Street");
physicalAddress1.setCity("Buffalo");
physicalAddress1.setState("NY");
physicalAddress1.setCountryOrRegion("USA");
physicalAddress1.setPostalCode("98054");
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("postOfficeBox", "");
additionalData1.put("type", "business");
physicalAddress1.setAdditionalData(additionalData1);
addresses.add(physicalAddress1);
bookingCustomerBase.setAddresses(addresses);
LinkedList<Phone> phones = new LinkedList<Phone>();
Phone phone = new Phone();
phone.setNumber("206-555-0100");
phone.setType(PhoneType.Home);
phones.add(phone);
Phone phone1 = new Phone();
phone1.setNumber("206-555-0200");
phone1.setType(PhoneType.Business);
phones.add(phone1);
bookingCustomerBase.setPhones(phones);
BookingCustomerBase result = graphClient.solutions().bookingBusinesses().byBookingBusinessId("{bookingBusiness-id}").customers().post(bookingCustomerBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const bookingCustomerBase = {
    '@odata.type': '#microsoft.graph.bookingCustomer',
    displayName: 'Joni Sherman',
    emailAddress: 'jonis@relecloud.com',
    addresses: [
        {
            postOfficeBox: '',
            street: '4567 Main Street',
            city: 'Buffalo',
            state: 'NY',
            countryOrRegion: 'USA',
            postalCode: '98052',
            type: 'home'
        },
        {
            postOfficeBox: '',
            street: '4570 Main Street',
            city: 'Buffalo',
            state: 'NY',
            countryOrRegion: 'USA',
            postalCode: '98054',
            type: 'business'
        }
    ],
    phones: [
        {
            number: '206-555-0100',
            type: 'home'
        },
        {
            number: '206-555-0200',
            type: 'business'
        }
     ]
};

await client.api('/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/customers')
	.post(bookingCustomerBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\BookingCustomer;
use Microsoft\Graph\Generated\Models\PhysicalAddress;
use Microsoft\Graph\Generated\Models\Phone;
use Microsoft\Graph\Generated\Models\PhoneType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BookingCustomer();
$requestBody->setOdataType('#microsoft.graph.bookingCustomer');
$requestBody->setDisplayName('Joni Sherman');
$requestBody->setEmailAddress('jonis@relecloud.com');
$addressesPhysicalAddress1 = new PhysicalAddress();
$addressesPhysicalAddress1->setStreet('4567 Main Street');
$addressesPhysicalAddress1->setCity('Buffalo');
$addressesPhysicalAddress1->setState('NY');
$addressesPhysicalAddress1->setCountryOrRegion('USA');
$addressesPhysicalAddress1->setPostalCode('98052');
$additionalData = [
	'postOfficeBox' => '',
	'type' => 'home',
];
$addressesPhysicalAddress1->setAdditionalData($additionalData);
$addressesArray []= $addressesPhysicalAddress1;
$addressesPhysicalAddress2 = new PhysicalAddress();
$addressesPhysicalAddress2->setStreet('4570 Main Street');
$addressesPhysicalAddress2->setCity('Buffalo');
$addressesPhysicalAddress2->setState('NY');
$addressesPhysicalAddress2->setCountryOrRegion('USA');
$addressesPhysicalAddress2->setPostalCode('98054');
$additionalData = [
	'postOfficeBox' => '',
	'type' => 'business',
];
$addressesPhysicalAddress2->setAdditionalData($additionalData);
$addressesArray []= $addressesPhysicalAddress2;
$requestBody->setAddresses($addressesArray);

$phonesPhone1 = new Phone();
$phonesPhone1->setNumber('206-555-0100');
$phonesPhone1->setType(new PhoneType('home'));
$phonesArray []= $phonesPhone1;
$phonesPhone2 = new Phone();
$phonesPhone2->setNumber('206-555-0200');
$phonesPhone2->setType(new PhoneType('business'));
$phonesArray []= $phonesPhone2;
$requestBody->setPhones($phonesArray);


$result = $graphServiceClient->solutions()->bookingBusinesses()->byBookingBusinessId('bookingBusiness-id')->customers()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	"@odata.type" = "#microsoft.graph.bookingCustomer"
	displayName = "Joni Sherman"
	emailAddress = "jonis@relecloud.com"
	addresses = @(
		@{
			postOfficeBox = ""
			street = "4567 Main Street"
			city = "Buffalo"
			state = "NY"
			countryOrRegion = "USA"
			postalCode = "98052"
			type = "home"
		}
		@{
			postOfficeBox = ""
			street = "4570 Main Street"
			city = "Buffalo"
			state = "NY"
			countryOrRegion = "USA"
			postalCode = "98054"
			type = "business"
		}
	)
	phones = @(
		@{
			number = "206-555-0100"
			type = "home"
		}
		@{
			number = "206-555-0200"
			type = "business"
		}
	)
}

New-MgBookingBusinessCustomer -BookingBusinessId $bookingBusinessId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.booking_customer import BookingCustomer
from msgraph.generated.models.physical_address import PhysicalAddress
from msgraph.generated.models.phone import Phone
from msgraph.generated.models.phone_type import PhoneType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BookingCustomer(
	odata_type = "#microsoft.graph.bookingCustomer",
	display_name = "Joni Sherman",
	email_address = "jonis@relecloud.com",
	addresses = [
		PhysicalAddress(
			street = "4567 Main Street",
			city = "Buffalo",
			state = "NY",
			country_or_region = "USA",
			postal_code = "98052",
			additional_data = {
					"post_office_box" : "",
					"type" : "home",
			}
		),
		PhysicalAddress(
			street = "4570 Main Street",
			city = "Buffalo",
			state = "NY",
			country_or_region = "USA",
			postal_code = "98054",
			additional_data = {
					"post_office_box" : "",
					"type" : "business",
			}
		),
	],
	phones = [
		Phone(
			number = "206-555-0100",
			type = PhoneType.Home,
		),
		Phone(
			number = "206-555-0200",
			type = PhoneType.Business,
		),
	],
)

result = await graph_client.solutions.booking_businesses.by_booking_business_id('bookingBusiness-id').customers.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.bookingCustomer",
    "@odata.context": "https://graph.microsoft.com/v1.0/solutions/$metadata#bookingBusinesses('Contosolunchdelivery%40contoso.com')/customers/$entity",
    "id": "36038f36-634e-44e4-9415-d7d59c2347aa",
    "displayName": "Joni Sherman",
    "emailAddress": "jonis@relecloud.com",
    "addresses": [
        {
            "postOfficeBox":"",
            "street":"4567 Main Street",
            "city":"Buffalo",
            "state":"NY",
            "countryOrRegion":"USA",
            "postalCode":"98052",
            "type":"home"
        },
        {
            "postOfficeBox":"",
            "street":"4570 Main Street",
            "city":"Buffalo",
            "state":"NY",
            "countryOrRegion":"USA",
            "postalCode":"98054",
            "type":"business"
        }
    ],
    "phones": [
        {
            "number": "206-555-0100",
            "type": "home"
        },
        {
            "number": "206-555-0200",
            "type": "business"
        }
     ]
}
```
