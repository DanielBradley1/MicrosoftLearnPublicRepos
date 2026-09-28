<!-- Source: https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-services?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create bookingService

Namespace: microsoft.graph

Create a new [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) for the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0).

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
POST /solutions/bookingBusinesses/{id}/services
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {code}. Required. |

## Request body

In the request body, supply a JSON representation of a [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and a [bookingService](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) object in the response body.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/services
Content-type: application/json

{
    "@odata.type":"#microsoft.graph.bookingService",
    "defaultDuration":"PT1H30M",
    "defaultLocation":{
        "@odata.type":"#microsoft.graph.location",
        "address":{
            "@odata.type":"#microsoft.graph.physicalAddress",
            "city":"Buffalo",
            "countryOrRegion":"USA",
            "postalCode":"98052",
            "postOfficeBox":null,
            "state":"NY",
            "street":"4567 First Street",
            "type@odata.type":"#microsoft.graph.physicalAddressType",
            "type":null
        },
        "coordinates":null,
        "displayName":"Contoso Lunch Delivery",
        "locationEmailAddress":null,
        "locationType@odata.type":"#microsoft.graph.locationType",
        "locationType":null,
        "locationUri":null,
        "uniqueId":null,
        "uniqueIdType@odata.type":"#microsoft.graph.locationUniqueIdType",
        "uniqueIdType":null
    },
    "defaultPrice":10.0,
    "defaultPriceType@odata.type":"#microsoft.graph.bookingPriceType",
    "defaultPriceType":"fixedPrice",
    "defaultReminders@odata.type":"#Collection(microsoft.graph.bookingReminder)",
    "defaultReminders":[
        {
            "@odata.type":"#microsoft.graph.bookingReminder",
            "message":"Please be reminded that this service is tomorrow.",
            "offset":"P1D",
            "recipients@odata.type":"#microsoft.graph.bookingReminderRecipients",
            "recipients":"allAttendees"
        }
    ],
    "description":"Individual bento box lunch delivery",
    "displayName":"Bento",
    "isLocationOnline": true,
    "smsNotificationsEnabled": true,
    "isCustomerAllowedToManageBooking": true,
    "languageTag": "en-US",
    "isHiddenFromCustomers":false,
    "notes":"Home-cooked special",
    "postBuffer":"PT10M",
    "preBuffer":"PT5M",
    "schedulingPolicy":{
        "@odata.type":"#microsoft.graph.bookingSchedulingPolicy",
        "allowStaffSelection":true,
        "maximumAdvance":"P10D",
        "minimumLeadTime":"PT10H",
        "sendConfirmationsToOwner":true,
        "timeSlotInterval":"PT1H"
    },
    "staffMemberIds@odata.type":"#Collection(String)",
    "staffMemberIds":[
        "d90d1e8c-5cfe-48cf-a2d5-966267375b6a",
        "2f5f8794-0b29-45b5-b56a-2eb5ff7aa880"
    ],
    "isAnonymousJoinEnabled": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new BookingService
{
	OdataType = "#microsoft.graph.bookingService",
	DefaultDuration = TimeSpan.Parse("PT1H30M"),
	DefaultLocation = new Location
	{
		OdataType = "#microsoft.graph.location",
		Address = new PhysicalAddress
		{
			OdataType = "#microsoft.graph.physicalAddress",
			City = "Buffalo",
			CountryOrRegion = "USA",
			PostalCode = "98052",
			State = "NY",
			Street = "4567 First Street",
			AdditionalData = new Dictionary<string, object>
			{
				{
					"postOfficeBox" , null
				},
				{
					"type@odata.type" , "#microsoft.graph.physicalAddressType"
				},
				{
					"type" , null
				},
			},
		},
		Coordinates = null,
		DisplayName = "Contoso Lunch Delivery",
		LocationEmailAddress = null,
		LocationType = null,
		LocationUri = null,
		UniqueId = null,
		UniqueIdType = null,
		AdditionalData = new Dictionary<string, object>
		{
			{
				"locationType@odata.type" , "#microsoft.graph.locationType"
			},
			{
				"uniqueIdType@odata.type" , "#microsoft.graph.locationUniqueIdType"
			},
		},
	},
	DefaultPrice = 10d,
	DefaultPriceType = BookingPriceType.FixedPrice,
	DefaultReminders = new List<BookingReminder>
	{
		new BookingReminder
		{
			OdataType = "#microsoft.graph.bookingReminder",
			Message = "Please be reminded that this service is tomorrow.",
			Offset = TimeSpan.Parse("P1D"),
			Recipients = BookingReminderRecipients.AllAttendees,
			AdditionalData = new Dictionary<string, object>
			{
				{
					"recipients@odata.type" , "#microsoft.graph.bookingReminderRecipients"
				},
			},
		},
	},
	Description = "Individual bento box lunch delivery",
	DisplayName = "Bento",
	IsLocationOnline = true,
	SmsNotificationsEnabled = true,
	IsCustomerAllowedToManageBooking = true,
	LanguageTag = "en-US",
	IsHiddenFromCustomers = false,
	Notes = "Home-cooked special",
	PostBuffer = TimeSpan.Parse("PT10M"),
	PreBuffer = TimeSpan.Parse("PT5M"),
	SchedulingPolicy = new BookingSchedulingPolicy
	{
		OdataType = "#microsoft.graph.bookingSchedulingPolicy",
		AllowStaffSelection = true,
		MaximumAdvance = TimeSpan.Parse("P10D"),
		MinimumLeadTime = TimeSpan.Parse("PT10H"),
		SendConfirmationsToOwner = true,
		TimeSlotInterval = TimeSpan.Parse("PT1H"),
	},
	StaffMemberIds = new List<string>
	{
		"d90d1e8c-5cfe-48cf-a2d5-966267375b6a",
		"2f5f8794-0b29-45b5-b56a-2eb5ff7aa880",
	},
	IsAnonymousJoinEnabled = false,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"defaultPriceType@odata.type" , "#microsoft.graph.bookingPriceType"
		},
		{
			"defaultReminders@odata.type" , "#Collection(microsoft.graph.bookingReminder)"
		},
		{
			"staffMemberIds@odata.type" , "#Collection(String)"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BookingBusinesses["{bookingBusiness-id}"].Services.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewBookingService()
defaultDuration , err := abstractions.ParseISODuration("PT1H30M")
requestBody.SetDefaultDuration(&defaultDuration) 
defaultLocation := graphmodels.NewLocation()
address := graphmodels.NewPhysicalAddress()
city := "Buffalo"
address.SetCity(&city) 
countryOrRegion := "USA"
address.SetCountryOrRegion(&countryOrRegion) 
postalCode := "98052"
address.SetPostalCode(&postalCode) 
state := "NY"
address.SetState(&state) 
street := "4567 First Street"
address.SetStreet(&street) 
additionalData := map[string]interface{}{
	postOfficeBox := null
address.SetPostOfficeBox(&postOfficeBox) 
	"type@odata.type" : "#microsoft.graph.physicalAddressType", 
	type := null
address.SetType(&type) 
}
address.SetAdditionalData(additionalData)
defaultLocation.SetAddress(address)
coordinates := null
defaultLocation.SetCoordinates(&coordinates) 
displayName := "Contoso Lunch Delivery"
defaultLocation.SetDisplayName(&displayName) 
locationEmailAddress := null
defaultLocation.SetLocationEmailAddress(&locationEmailAddress) 
locationType := null
defaultLocation.SetLocationType(&locationType) 
locationUri := null
defaultLocation.SetLocationUri(&locationUri) 
uniqueId := null
defaultLocation.SetUniqueId(&uniqueId) 
uniqueIdType := null
defaultLocation.SetUniqueIdType(&uniqueIdType) 
additionalData := map[string]interface{}{
	"locationType@odata.type" : "#microsoft.graph.locationType", 
	"uniqueIdType@odata.type" : "#microsoft.graph.locationUniqueIdType", 
}
defaultLocation.SetAdditionalData(additionalData)
requestBody.SetDefaultLocation(defaultLocation)
defaultPrice := float64(10)
requestBody.SetDefaultPrice(&defaultPrice) 
defaultPriceType := graphmodels.FIXEDPRICE_BOOKINGPRICETYPE 
requestBody.SetDefaultPriceType(&defaultPriceType) 


bookingReminder := graphmodels.NewBookingReminder()
message := "Please be reminded that this service is tomorrow."
bookingReminder.SetMessage(&message) 
offset , err := abstractions.ParseISODuration("P1D")
bookingReminder.SetOffset(&offset) 
recipients := graphmodels.ALLATTENDEES_BOOKINGREMINDERRECIPIENTS 
bookingReminder.SetRecipients(&recipients) 
additionalData := map[string]interface{}{
	"recipients@odata.type" : "#microsoft.graph.bookingReminderRecipients", 
}
bookingReminder.SetAdditionalData(additionalData)

defaultReminders := []graphmodels.BookingReminderable {
	bookingReminder,
}
requestBody.SetDefaultReminders(defaultReminders)
description := "Individual bento box lunch delivery"
requestBody.SetDescription(&description) 
displayName := "Bento"
requestBody.SetDisplayName(&displayName) 
isLocationOnline := true
requestBody.SetIsLocationOnline(&isLocationOnline) 
smsNotificationsEnabled := true
requestBody.SetSmsNotificationsEnabled(&smsNotificationsEnabled) 
isCustomerAllowedToManageBooking := true
requestBody.SetIsCustomerAllowedToManageBooking(&isCustomerAllowedToManageBooking) 
languageTag := "en-US"
requestBody.SetLanguageTag(&languageTag) 
isHiddenFromCustomers := false
requestBody.SetIsHiddenFromCustomers(&isHiddenFromCustomers) 
notes := "Home-cooked special"
requestBody.SetNotes(&notes) 
postBuffer , err := abstractions.ParseISODuration("PT10M")
requestBody.SetPostBuffer(&postBuffer) 
preBuffer , err := abstractions.ParseISODuration("PT5M")
requestBody.SetPreBuffer(&preBuffer) 
schedulingPolicy := graphmodels.NewBookingSchedulingPolicy()
allowStaffSelection := true
schedulingPolicy.SetAllowStaffSelection(&allowStaffSelection) 
maximumAdvance , err := abstractions.ParseISODuration("P10D")
schedulingPolicy.SetMaximumAdvance(&maximumAdvance) 
minimumLeadTime , err := abstractions.ParseISODuration("PT10H")
schedulingPolicy.SetMinimumLeadTime(&minimumLeadTime) 
sendConfirmationsToOwner := true
schedulingPolicy.SetSendConfirmationsToOwner(&sendConfirmationsToOwner) 
timeSlotInterval , err := abstractions.ParseISODuration("PT1H")
schedulingPolicy.SetTimeSlotInterval(&timeSlotInterval) 
requestBody.SetSchedulingPolicy(schedulingPolicy)
staffMemberIds := []string {
	"d90d1e8c-5cfe-48cf-a2d5-966267375b6a",
	"2f5f8794-0b29-45b5-b56a-2eb5ff7aa880",
}
requestBody.SetStaffMemberIds(staffMemberIds)
isAnonymousJoinEnabled := false
requestBody.SetIsAnonymousJoinEnabled(&isAnonymousJoinEnabled) 
additionalData := map[string]interface{}{
	"defaultPriceType@odata.type" : "#microsoft.graph.bookingPriceType", 
	"defaultReminders@odata.type" : "#Collection(microsoft.graph.bookingReminder)", 
	"staffMemberIds@odata.type" : "#Collection(String)", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
services, err := graphClient.Solutions().BookingBusinesses().ByBookingBusinessId("bookingBusiness-id").Services().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BookingService bookingService = new BookingService();
bookingService.setOdataType("#microsoft.graph.bookingService");
PeriodAndDuration defaultDuration = PeriodAndDuration.ofDuration(Duration.parse("PT1H30M"));
bookingService.setDefaultDuration(defaultDuration);
Location defaultLocation = new Location();
defaultLocation.setOdataType("#microsoft.graph.location");
PhysicalAddress address = new PhysicalAddress();
address.setOdataType("#microsoft.graph.physicalAddress");
address.setCity("Buffalo");
address.setCountryOrRegion("USA");
address.setPostalCode("98052");
address.setState("NY");
address.setStreet("4567 First Street");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("postOfficeBox", null);
additionalData.put("type@odata.type", "#microsoft.graph.physicalAddressType");
additionalData.put("type", null);
address.setAdditionalData(additionalData);
defaultLocation.setAddress(address);
defaultLocation.setCoordinates(null);
defaultLocation.setDisplayName("Contoso Lunch Delivery");
defaultLocation.setLocationEmailAddress(null);
defaultLocation.setLocationType(null);
defaultLocation.setLocationUri(null);
defaultLocation.setUniqueId(null);
defaultLocation.setUniqueIdType(null);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("locationType@odata.type", "#microsoft.graph.locationType");
additionalData1.put("uniqueIdType@odata.type", "#microsoft.graph.locationUniqueIdType");
defaultLocation.setAdditionalData(additionalData1);
bookingService.setDefaultLocation(defaultLocation);
bookingService.setDefaultPrice(10d);
bookingService.setDefaultPriceType(BookingPriceType.FixedPrice);
LinkedList<BookingReminder> defaultReminders = new LinkedList<BookingReminder>();
BookingReminder bookingReminder = new BookingReminder();
bookingReminder.setOdataType("#microsoft.graph.bookingReminder");
bookingReminder.setMessage("Please be reminded that this service is tomorrow.");
PeriodAndDuration offset = PeriodAndDuration.ofDuration(Duration.parse("P1D"));
bookingReminder.setOffset(offset);
bookingReminder.setRecipients(BookingReminderRecipients.AllAttendees);
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
additionalData2.put("recipients@odata.type", "#microsoft.graph.bookingReminderRecipients");
bookingReminder.setAdditionalData(additionalData2);
defaultReminders.add(bookingReminder);
bookingService.setDefaultReminders(defaultReminders);
bookingService.setDescription("Individual bento box lunch delivery");
bookingService.setDisplayName("Bento");
bookingService.setIsLocationOnline(true);
bookingService.setSmsNotificationsEnabled(true);
bookingService.setIsCustomerAllowedToManageBooking(true);
bookingService.setLanguageTag("en-US");
bookingService.setIsHiddenFromCustomers(false);
bookingService.setNotes("Home-cooked special");
PeriodAndDuration postBuffer = PeriodAndDuration.ofDuration(Duration.parse("PT10M"));
bookingService.setPostBuffer(postBuffer);
PeriodAndDuration preBuffer = PeriodAndDuration.ofDuration(Duration.parse("PT5M"));
bookingService.setPreBuffer(preBuffer);
BookingSchedulingPolicy schedulingPolicy = new BookingSchedulingPolicy();
schedulingPolicy.setOdataType("#microsoft.graph.bookingSchedulingPolicy");
schedulingPolicy.setAllowStaffSelection(true);
PeriodAndDuration maximumAdvance = PeriodAndDuration.ofDuration(Duration.parse("P10D"));
schedulingPolicy.setMaximumAdvance(maximumAdvance);
PeriodAndDuration minimumLeadTime = PeriodAndDuration.ofDuration(Duration.parse("PT10H"));
schedulingPolicy.setMinimumLeadTime(minimumLeadTime);
schedulingPolicy.setSendConfirmationsToOwner(true);
PeriodAndDuration timeSlotInterval = PeriodAndDuration.ofDuration(Duration.parse("PT1H"));
schedulingPolicy.setTimeSlotInterval(timeSlotInterval);
bookingService.setSchedulingPolicy(schedulingPolicy);
LinkedList<String> staffMemberIds = new LinkedList<String>();
staffMemberIds.add("d90d1e8c-5cfe-48cf-a2d5-966267375b6a");
staffMemberIds.add("2f5f8794-0b29-45b5-b56a-2eb5ff7aa880");
bookingService.setStaffMemberIds(staffMemberIds);
bookingService.setIsAnonymousJoinEnabled(false);
HashMap<String, Object> additionalData3 = new HashMap<String, Object>();
additionalData3.put("defaultPriceType@odata.type", "#microsoft.graph.bookingPriceType");
additionalData3.put("defaultReminders@odata.type", "#Collection(microsoft.graph.bookingReminder)");
additionalData3.put("staffMemberIds@odata.type", "#Collection(String)");
bookingService.setAdditionalData(additionalData3);
BookingService result = graphClient.solutions().bookingBusinesses().byBookingBusinessId("{bookingBusiness-id}").services().post(bookingService);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const bookingService = {
    '@odata.type':'#microsoft.graph.bookingService',
    defaultDuration: 'PT1H30M',
    defaultLocation: {
        '@odata.type':'#microsoft.graph.location',
        address: {
            '@odata.type':'#microsoft.graph.physicalAddress',
            city: 'Buffalo',
            countryOrRegion: 'USA',
            postalCode: '98052',
            postOfficeBox: null,
            state: 'NY',
            street: '4567 First Street',
            'type@odata.type':'#microsoft.graph.physicalAddressType',
            type: null
        },
        coordinates: null,
        displayName: 'Contoso Lunch Delivery',
        locationEmailAddress: null,
        'locationType@odata.type':'#microsoft.graph.locationType',
        locationType: null,
        locationUri: null,
        uniqueId: null,
        'uniqueIdType@odata.type':'#microsoft.graph.locationUniqueIdType',
        uniqueIdType: null
    },
    defaultPrice: 10.0,
    'defaultPriceType@odata.type':'#microsoft.graph.bookingPriceType',
    defaultPriceType: 'fixedPrice',
    'defaultReminders@odata.type':'#Collection(microsoft.graph.bookingReminder)',
    defaultReminders: [
        {
            '@odata.type':'#microsoft.graph.bookingReminder',
            message: 'Please be reminded that this service is tomorrow.',
            offset: 'P1D',
            'recipients@odata.type':'#microsoft.graph.bookingReminderRecipients',
            recipients: 'allAttendees'
        }
    ],
    description: 'Individual bento box lunch delivery',
    displayName: 'Bento',
    isLocationOnline: true,
    smsNotificationsEnabled: true,
    isCustomerAllowedToManageBooking: true,
    languageTag: 'en-US',
    isHiddenFromCustomers: false,
    notes: 'Home-cooked special',
    postBuffer: 'PT10M',
    preBuffer: 'PT5M',
    schedulingPolicy: {
        '@odata.type':'#microsoft.graph.bookingSchedulingPolicy',
        allowStaffSelection: true,
        maximumAdvance: 'P10D',
        minimumLeadTime: 'PT10H',
        sendConfirmationsToOwner: true,
        timeSlotInterval: 'PT1H'
    },
    'staffMemberIds@odata.type':'#Collection(String)',
    staffMemberIds: [
        'd90d1e8c-5cfe-48cf-a2d5-966267375b6a',
        '2f5f8794-0b29-45b5-b56a-2eb5ff7aa880'
    ],
    isAnonymousJoinEnabled: false
};

await client.api('/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/services')
	.post(bookingService);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\BookingService;
use Microsoft\Graph\Generated\Models\Location;
use Microsoft\Graph\Generated\Models\PhysicalAddress;
use Microsoft\Graph\Generated\Models\BookingPriceType;
use Microsoft\Graph\Generated\Models\BookingReminder;
use Microsoft\Graph\Generated\Models\BookingReminderRecipients;
use Microsoft\Graph\Generated\Models\BookingSchedulingPolicy;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BookingService();
$requestBody->setOdataType('#microsoft.graph.bookingService');
$requestBody->setDefaultDuration(new \DateInterval('PT1H30M'));
$defaultLocation = new Location();
$defaultLocation->setOdataType('#microsoft.graph.location');
$defaultLocationAddress = new PhysicalAddress();
$defaultLocationAddress->setOdataType('#microsoft.graph.physicalAddress');
$defaultLocationAddress->setCity('Buffalo');
$defaultLocationAddress->setCountryOrRegion('USA');
$defaultLocationAddress->setPostalCode('98052');
$defaultLocationAddress->setState('NY');
$defaultLocationAddress->setStreet('4567 First Street');
$additionalData = [
	'postOfficeBox' => null,
	'type@odata.type' => '#microsoft.graph.physicalAddressType',
	'type' => null,
];
$defaultLocationAddress->setAdditionalData($additionalData);
$defaultLocation->setAddress($defaultLocationAddress);
$defaultLocation->setCoordinates(null);
$defaultLocation->setDisplayName('Contoso Lunch Delivery');
$defaultLocation->setLocationEmailAddress(null);
$defaultLocation->setLocationType(null);
$defaultLocation->setLocationUri(null);
$defaultLocation->setUniqueId(null);
$defaultLocation->setUniqueIdType(null);
$additionalData = [
	'locationType@odata.type' => '#microsoft.graph.locationType',
	'uniqueIdType@odata.type' => '#microsoft.graph.locationUniqueIdType',
];
$defaultLocation->setAdditionalData($additionalData);
$requestBody->setDefaultLocation($defaultLocation);
$requestBody->setDefaultPrice(10);
$requestBody->setDefaultPriceType(new BookingPriceType('fixedPrice'));
$defaultRemindersBookingReminder1 = new BookingReminder();
$defaultRemindersBookingReminder1->setOdataType('#microsoft.graph.bookingReminder');
$defaultRemindersBookingReminder1->setMessage('Please be reminded that this service is tomorrow.');
$defaultRemindersBookingReminder1->setOffset(new \DateInterval('P1D'));
$defaultRemindersBookingReminder1->setRecipients(new BookingReminderRecipients('allAttendees'));
$additionalData = [
	'recipients@odata.type' => '#microsoft.graph.bookingReminderRecipients',
];
$defaultRemindersBookingReminder1->setAdditionalData($additionalData);
$defaultRemindersArray []= $defaultRemindersBookingReminder1;
$requestBody->setDefaultReminders($defaultRemindersArray);

$requestBody->setDescription('Individual bento box lunch delivery');
$requestBody->setDisplayName('Bento');
$requestBody->setIsLocationOnline(true);
$requestBody->setSmsNotificationsEnabled(true);
$requestBody->setIsCustomerAllowedToManageBooking(true);
$requestBody->setLanguageTag('en-US');
$requestBody->setIsHiddenFromCustomers(false);
$requestBody->setNotes('Home-cooked special');
$requestBody->setPostBuffer(new \DateInterval('PT10M'));
$requestBody->setPreBuffer(new \DateInterval('PT5M'));
$schedulingPolicy = new BookingSchedulingPolicy();
$schedulingPolicy->setOdataType('#microsoft.graph.bookingSchedulingPolicy');
$schedulingPolicy->setAllowStaffSelection(true);
$schedulingPolicy->setMaximumAdvance(new \DateInterval('P10D'));
$schedulingPolicy->setMinimumLeadTime(new \DateInterval('PT10H'));
$schedulingPolicy->setSendConfirmationsToOwner(true);
$schedulingPolicy->setTimeSlotInterval(new \DateInterval('PT1H'));
$requestBody->setSchedulingPolicy($schedulingPolicy);
$requestBody->setStaffMemberIds(['d90d1e8c-5cfe-48cf-a2d5-966267375b6a', '2f5f8794-0b29-45b5-b56a-2eb5ff7aa880', ]);
$requestBody->setIsAnonymousJoinEnabled(false);
$additionalData = [
'defaultPriceType@odata.type' => '#microsoft.graph.bookingPriceType',
'defaultReminders@odata.type' => '#Collection(microsoft.graph.bookingReminder)',
'staffMemberIds@odata.type' => '#Collection(String)',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->solutions()->bookingBusinesses()->byBookingBusinessId('bookingBusiness-id')->services()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.booking_service import BookingService
from msgraph.generated.models.location import Location
from msgraph.generated.models.physical_address import PhysicalAddress
from msgraph.generated.models.booking_price_type import BookingPriceType
from msgraph.generated.models.booking_reminder import BookingReminder
from msgraph.generated.models.booking_reminder_recipients import BookingReminderRecipients
from msgraph.generated.models.booking_scheduling_policy import BookingSchedulingPolicy
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BookingService(
	odata_type = "#microsoft.graph.bookingService",
	default_duration = "PT1H30M",
	default_location = Location(
		odata_type = "#microsoft.graph.location",
		address = PhysicalAddress(
			odata_type = "#microsoft.graph.physicalAddress",
			city = "Buffalo",
			country_or_region = "USA",
			postal_code = "98052",
			state = "NY",
			street = "4567 First Street",
			additional_data = {
					"post_office_box" : None,
					"type@odata_type" : "#microsoft.graph.physicalAddressType",
					"type" : None,
			}
		),
		coordinates = None,
		display_name = "Contoso Lunch Delivery",
		location_email_address = None,
		location_type = None,
		location_uri = None,
		unique_id = None,
		unique_id_type = None,
		additional_data = {
				"location_type@odata_type" : "#microsoft.graph.locationType",
				"unique_id_type@odata_type" : "#microsoft.graph.locationUniqueIdType",
		}
	),
	default_price = 10,
	default_price_type = BookingPriceType.FixedPrice,
	default_reminders = [
		BookingReminder(
			odata_type = "#microsoft.graph.bookingReminder",
			message = "Please be reminded that this service is tomorrow.",
			offset = "P1D",
			recipients = BookingReminderRecipients.AllAttendees,
			additional_data = {
					"recipients@odata_type" : "#microsoft.graph.bookingReminderRecipients",
			}
		),
	],
	description = "Individual bento box lunch delivery",
	display_name = "Bento",
	is_location_online = True,
	sms_notifications_enabled = True,
	is_customer_allowed_to_manage_booking = True,
	language_tag = "en-US",
	is_hidden_from_customers = False,
	notes = "Home-cooked special",
	post_buffer = "PT10M",
	pre_buffer = "PT5M",
	scheduling_policy = BookingSchedulingPolicy(
		odata_type = "#microsoft.graph.bookingSchedulingPolicy",
		allow_staff_selection = True,
		maximum_advance = "P10D",
		minimum_lead_time = "PT10H",
		send_confirmations_to_owner = True,
		time_slot_interval = "PT1H",
	),
	staff_member_ids = [
		"d90d1e8c-5cfe-48cf-a2d5-966267375b6a",
		"2f5f8794-0b29-45b5-b56a-2eb5ff7aa880",
	],
	is_anonymous_join_enabled = False,
	additional_data = {
			"default_price_type@odata_type" : "#microsoft.graph.bookingPriceType",
			"default_reminders@odata_type" : "#Collection(microsoft.graph.bookingReminder)",
			"staff_member_ids@odata_type" : "#Collection(String)",
	}
)

result = await graph_client.solutions.booking_businesses.by_booking_business_id('bookingBusiness-id').services.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/solutions/$metadata#bookingBusinesses('Contosolunchdelivery%40contoso.com')/services/$entity",
    "id": "57da6774-a087-4d69-b0e6-6fb82c339976",
    "displayName": "Bento",
    "defaultDuration": "PT1H30M",
    "defaultPrice": 10.0,
    "defaultPriceType": "fixedPrice",
    "description": "Individual bento box lunch delivery",
    "languageTag": "",
    "isHiddenFromCustomers": false,
    "notes": "Home-cooked special",
    "preBuffer": "PT5M",
    "postBuffer": "PT10M",
    "staffMemberIds": [],
    "isLocationOnline": true,
    "isAnonymousJoinEnabled": false,
    "smsNotificationsEnabled": true,
    "isCustomerAllowedToManageBooking": true,
    "webUrl": "https://outlook.office365.com/owa/calendar/Contosolunchdelivery@contoso.onmicrosoft.com/bookings/s/gkcGIq92Z0u5h4FWB9Qgcg2",
    "defaultLocation": {
        "displayName": "Contoso Lunch Delivery",
        "locationEmailAddress": null,
        "locationUri": "",
        "locationType": null,
        "uniqueId": null,
        "uniqueIdType": null,
        "address": {
            "street": "4567 First Street",
            "city": "Buffalo",
            "state": "NY",
            "countryOrRegion": "USA",
            "postalCode": "98052"
        },
        "coordinates": {
            "altitude": null,
            "latitude": null,
            "longitude": null,
            "accuracy": null,
            "altitudeAccuracy": null
        }
    },
    "defaultReminders": [
        {
            "offset": "P1D",
            "recipients": "allAttendees",
            "message": "Please be reminded that this service is tomorrow."
        }
    ],
    "schedulingPolicy": {
        "timeSlotInterval": "PT1H",
        "minimumLeadTime": "PT10H",
        "maximumAdvance": "P10D",
        "sendConfirmationsToOwner": true,
        "allowStaffSelection": true
    }
}
```
