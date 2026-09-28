<!-- Source: https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-appointments?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create bookingAppointment

Namespace: microsoft.graph

Create a new [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) for the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0).

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
POST /solutions/bookingBusinesses/{id}/appointments
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {code}. Required. |

## Request body

In the request body, supply a JSON representation of a [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) object.

If the maximum number of customers \(**maximumAttendeesCount**\) allowed in the [service](https://learn.microsoft.com/en-us/graph/api/resources/bookingservice?view=graph-rest-1.0) is greater than 1:

- Make sure that the customers exist in the Booking Calendar. If they don’t, create using the [Create bookingCustomer](https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-customers?view=graph-rest-1.0) operation.
- Pass valid customer IDs when you create or update the appointment. If the customer ID is invalid, that customer isn't included in the appointment object.

## Response

If successful, this method returns a `201 Created` response code and a [bookingAppointment](https://learn.microsoft.com/en-us/graph/api/resources/bookingappointment?view=graph-rest-1.0) object in the response body.

## Example

### Request

The following example shows a request. This appointment doesn't involve booking specific staff members.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/appointments
Content-type: application/json

{
    "@odata.type": "#microsoft.graph.bookingAppointment",
    "customerTimeZone": "America/Chicago",
    "customerName": "Jordan Miller",
    "customerEmailAddress": "jordanm@contoso.com",
    "customerPhone": "213-555-0199",
    "customerNotes": null,	
    "smsNotificationsEnabled": true,
    "end": {
        "@odata.type": "#microsoft.graph.dateTimeTimeZone",
        "dateTime": "2018-05-01T12:30:00.0000000+00:00",
        "timeZone": "UTC"
    },
    "isCustomerAllowedToManageBooking": true,
    "isLocationOnline": true,
    "optOutOfCustomerEmail": false,
    "anonymousJoinWebUrl": null,
    "postBuffer": "PT10M",
    "preBuffer": "PT5M",
    "price": 10.0,
    "priceType@odata.type": "#microsoft.graph.bookingPriceType",
    "priceType": "fixedPrice",
    "reminders@odata.type": "#Collection(microsoft.graph.bookingReminder)",
    "reminders": [
        {
            "@odata.type": "#microsoft.graph.bookingReminder",
            "message": "This service is tomorrow",
            "offset": "P1D",
            "recipients@odata.type": "#microsoft.graph.bookingReminderRecipients",
            "recipients": "allAttendees"
        },
        {
            "@odata.type": "#microsoft.graph.bookingReminder",
            "message": "Please be available to enjoy your lunch service.",
            "offset": "PT1H",
            "recipients@odata.type": "#microsoft.graph.bookingReminderRecipients",
            "recipients": "customer"
        },
        {
            "@odata.type": "#microsoft.graph.bookingReminder",
            "message": "Please check traffic for next cater.",
            "offset": "PT2H",
            "recipients@odata.type": "#microsoft.graph.bookingReminderRecipients",
            "recipients": "staff"
        }
    ],
    "serviceId": "57da6774-a087-4d69-b0e6-6fb82c339976",
    "serviceLocation": {
        "@odata.type": "#microsoft.graph.location",
        "address": {
            "@odata.type": "#microsoft.graph.physicalAddress",
            "city": "Buffalo",
            "countryOrRegion": "USA",
            "postalCode": "98052",
            "postOfficeBox": null,
            "state": "NY",
            "street": "123 First Avenue",
            "type@odata.type": "#microsoft.graph.physicalAddressType",
            "type": null
        },
        "coordinates": null,
        "displayName": "Customer location",
        "locationEmailAddress": null,
        "locationType@odata.type": "#microsoft.graph.locationType",
        "locationType": null,
        "locationUri": null,
        "uniqueId": null,
        "uniqueIdType@odata.type": "#microsoft.graph.locationUniqueIdType",
        "uniqueIdType": null
    },
    "serviceName": "Catered bento",
    "serviceNotes": "Customer requires punctual service.",
    "staffMemberIds": [
      "8ee1c803-a1fa-406d-8259-7ab53233f148"
    ],
    "start": {
        "@odata.type": "#microsoft.graph.dateTimeTimeZone",
        "dateTime": "2018-05-01T12:00:00.0000000+00:00",
        "timeZone": "UTC"
    },
    "maximumAttendeesCount": 5,
    "filledAttendeesCount": 1,
    "customers@odata.type": "#Collection(microsoft.graph.bookingCustomerInformation)",
    "customers": [
        {
            "@odata.type": "#microsoft.graph.bookingCustomerInformation",
            "customerId": "7ed53fa5-9ef2-4f2f-975b-27447440bc09",
            "name": "Jordan Miller",
            "emailAddress": "jordanm@contoso.com",
            "phone": "213-555-0199",
            "notes": null,
            "location": {
                "@odata.type": "#microsoft.graph.location",
                "displayName": "Customer",
                "locationEmailAddress": null,
                "locationUri": "",
                "locationType": null,
                "uniqueId": null,
                "uniqueIdType": null,
                "address": {
                    "@odata.type": "#microsoft.graph.physicalAddress",
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
            "timeZone":"America/Chicago",
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
	CustomerTimeZone = "America/Chicago",
	CustomerName = "Jordan Miller",
	CustomerEmailAddress = "jordanm@contoso.com",
	CustomerPhone = "213-555-0199",
	CustomerNotes = null,
	SmsNotificationsEnabled = true,
	IsCustomerAllowedToManageBooking = true,
	IsLocationOnline = true,
	OptOutOfCustomerEmail = false,
	AnonymousJoinWebUrl = null,
	PostBuffer = TimeSpan.Parse("PT10M"),
	PreBuffer = TimeSpan.Parse("PT5M"),
	Price = 10d,
	PriceType = BookingPriceType.FixedPrice,
	Reminders = new List<BookingReminder>
	{
		new BookingReminder
		{
			OdataType = "#microsoft.graph.bookingReminder",
			Message = "This service is tomorrow",
			Offset = TimeSpan.Parse("P1D"),
			Recipients = BookingReminderRecipients.AllAttendees,
			AdditionalData = new Dictionary<string, object>
			{
				{
					"recipients@odata.type" , "#microsoft.graph.bookingReminderRecipients"
				},
			},
		},
		new BookingReminder
		{
			OdataType = "#microsoft.graph.bookingReminder",
			Message = "Please be available to enjoy your lunch service.",
			Offset = TimeSpan.Parse("PT1H"),
			Recipients = BookingReminderRecipients.Customer,
			AdditionalData = new Dictionary<string, object>
			{
				{
					"recipients@odata.type" , "#microsoft.graph.bookingReminderRecipients"
				},
			},
		},
		new BookingReminder
		{
			OdataType = "#microsoft.graph.bookingReminder",
			Message = "Please check traffic for next cater.",
			Offset = TimeSpan.Parse("PT2H"),
			Recipients = BookingReminderRecipients.Staff,
			AdditionalData = new Dictionary<string, object>
			{
				{
					"recipients@odata.type" , "#microsoft.graph.bookingReminderRecipients"
				},
			},
		},
	},
	ServiceId = "57da6774-a087-4d69-b0e6-6fb82c339976",
	ServiceLocation = new Location
	{
		OdataType = "#microsoft.graph.location",
		Address = new PhysicalAddress
		{
			OdataType = "#microsoft.graph.physicalAddress",
			City = "Buffalo",
			CountryOrRegion = "USA",
			PostalCode = "98052",
			State = "NY",
			Street = "123 First Avenue",
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
		DisplayName = "Customer location",
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
	ServiceName = "Catered bento",
	ServiceNotes = "Customer requires punctual service.",
	StaffMemberIds = new List<string>
	{
		"8ee1c803-a1fa-406d-8259-7ab53233f148",
	},
	MaximumAttendeesCount = 5,
	FilledAttendeesCount = 1,
	Customers = new List<BookingCustomerInformationBase>
	{
		new BookingCustomerInformation
		{
			OdataType = "#microsoft.graph.bookingCustomerInformation",
			CustomerId = "7ed53fa5-9ef2-4f2f-975b-27447440bc09",
			Name = "Jordan Miller",
			EmailAddress = "jordanm@contoso.com",
			Phone = "213-555-0199",
			Notes = null,
			Location = new Location
			{
				OdataType = "#microsoft.graph.location",
				DisplayName = "Customer",
				LocationEmailAddress = null,
				LocationUri = "",
				LocationType = null,
				UniqueId = null,
				UniqueIdType = null,
				Address = new PhysicalAddress
				{
					OdataType = "#microsoft.graph.physicalAddress",
					Street = "",
					City = "",
					State = "",
					CountryOrRegion = "",
					PostalCode = "",
				},
				Coordinates = new OutlookGeoCoordinates
				{
					Altitude = null,
					Latitude = null,
					Longitude = null,
					Accuracy = null,
					AltitudeAccuracy = null,
				},
			},
			TimeZone = "America/Chicago",
			CustomQuestionAnswers = new List<BookingQuestionAnswer>
			{
				new BookingQuestionAnswer
				{
					QuestionId = "3bc6fde0-4ad3-445d-ab17-0fc15dba0774",
					Question = "What is your age?",
					AnswerInputType = AnswerInputType.Text,
					AnswerOptions = new List<string>
					{
					},
					IsRequired = true,
					Answer = "25",
					SelectedOptions = new List<string>
					{
					},
				},
			},
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"end" , new DateTimeTimeZone
			{
				OdataType = "#microsoft.graph.dateTimeTimeZone",
				DateTime = "2018-05-01T12:30:00.0000000+00:00",
				TimeZone = "UTC",
			}
		},
		{
			"priceType@odata.type" , "#microsoft.graph.bookingPriceType"
		},
		{
			"reminders@odata.type" , "#Collection(microsoft.graph.bookingReminder)"
		},
		{
			"start" , new DateTimeTimeZone
			{
				OdataType = "#microsoft.graph.dateTimeTimeZone",
				DateTime = "2018-05-01T12:00:00.0000000+00:00",
				TimeZone = "UTC",
			}
		},
		{
			"customers@odata.type" , "#Collection(microsoft.graph.bookingCustomerInformation)"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BookingBusinesses["{bookingBusiness-id}"].Appointments.PostAsync(requestBody);
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

requestBody := graphmodels.NewBookingAppointment()
customerTimeZone := "America/Chicago"
requestBody.SetCustomerTimeZone(&customerTimeZone) 
customerName := "Jordan Miller"
requestBody.SetCustomerName(&customerName) 
customerEmailAddress := "jordanm@contoso.com"
requestBody.SetCustomerEmailAddress(&customerEmailAddress) 
customerPhone := "213-555-0199"
requestBody.SetCustomerPhone(&customerPhone) 
customerNotes := null
requestBody.SetCustomerNotes(&customerNotes) 
smsNotificationsEnabled := true
requestBody.SetSmsNotificationsEnabled(&smsNotificationsEnabled) 
isCustomerAllowedToManageBooking := true
requestBody.SetIsCustomerAllowedToManageBooking(&isCustomerAllowedToManageBooking) 
isLocationOnline := true
requestBody.SetIsLocationOnline(&isLocationOnline) 
optOutOfCustomerEmail := false
requestBody.SetOptOutOfCustomerEmail(&optOutOfCustomerEmail) 
anonymousJoinWebUrl := null
requestBody.SetAnonymousJoinWebUrl(&anonymousJoinWebUrl) 
postBuffer , err := abstractions.ParseISODuration("PT10M")
requestBody.SetPostBuffer(&postBuffer) 
preBuffer , err := abstractions.ParseISODuration("PT5M")
requestBody.SetPreBuffer(&preBuffer) 
price := float64(10)
requestBody.SetPrice(&price) 
priceType := graphmodels.FIXEDPRICE_BOOKINGPRICETYPE 
requestBody.SetPriceType(&priceType) 


bookingReminder := graphmodels.NewBookingReminder()
message := "This service is tomorrow"
bookingReminder.SetMessage(&message) 
offset , err := abstractions.ParseISODuration("P1D")
bookingReminder.SetOffset(&offset) 
recipients := graphmodels.ALLATTENDEES_BOOKINGREMINDERRECIPIENTS 
bookingReminder.SetRecipients(&recipients) 
additionalData := map[string]interface{}{
	"recipients@odata.type" : "#microsoft.graph.bookingReminderRecipients", 
}
bookingReminder.SetAdditionalData(additionalData)
bookingReminder1 := graphmodels.NewBookingReminder()
message := "Please be available to enjoy your lunch service."
bookingReminder1.SetMessage(&message) 
offset , err := abstractions.ParseISODuration("PT1H")
bookingReminder1.SetOffset(&offset) 
recipients := graphmodels.CUSTOMER_BOOKINGREMINDERRECIPIENTS 
bookingReminder1.SetRecipients(&recipients) 
additionalData := map[string]interface{}{
	"recipients@odata.type" : "#microsoft.graph.bookingReminderRecipients", 
}
bookingReminder1.SetAdditionalData(additionalData)
bookingReminder2 := graphmodels.NewBookingReminder()
message := "Please check traffic for next cater."
bookingReminder2.SetMessage(&message) 
offset , err := abstractions.ParseISODuration("PT2H")
bookingReminder2.SetOffset(&offset) 
recipients := graphmodels.STAFF_BOOKINGREMINDERRECIPIENTS 
bookingReminder2.SetRecipients(&recipients) 
additionalData := map[string]interface{}{
	"recipients@odata.type" : "#microsoft.graph.bookingReminderRecipients", 
}
bookingReminder2.SetAdditionalData(additionalData)

reminders := []graphmodels.BookingReminderable {
	bookingReminder,
	bookingReminder1,
	bookingReminder2,
}
requestBody.SetReminders(reminders)
serviceId := "57da6774-a087-4d69-b0e6-6fb82c339976"
requestBody.SetServiceId(&serviceId) 
serviceLocation := graphmodels.NewLocation()
address := graphmodels.NewPhysicalAddress()
city := "Buffalo"
address.SetCity(&city) 
countryOrRegion := "USA"
address.SetCountryOrRegion(&countryOrRegion) 
postalCode := "98052"
address.SetPostalCode(&postalCode) 
state := "NY"
address.SetState(&state) 
street := "123 First Avenue"
address.SetStreet(&street) 
additionalData := map[string]interface{}{
	postOfficeBox := null
address.SetPostOfficeBox(&postOfficeBox) 
	"type@odata.type" : "#microsoft.graph.physicalAddressType", 
	type := null
address.SetType(&type) 
}
address.SetAdditionalData(additionalData)
serviceLocation.SetAddress(address)
coordinates := null
serviceLocation.SetCoordinates(&coordinates) 
displayName := "Customer location"
serviceLocation.SetDisplayName(&displayName) 
locationEmailAddress := null
serviceLocation.SetLocationEmailAddress(&locationEmailAddress) 
locationType := null
serviceLocation.SetLocationType(&locationType) 
locationUri := null
serviceLocation.SetLocationUri(&locationUri) 
uniqueId := null
serviceLocation.SetUniqueId(&uniqueId) 
uniqueIdType := null
serviceLocation.SetUniqueIdType(&uniqueIdType) 
additionalData := map[string]interface{}{
	"locationType@odata.type" : "#microsoft.graph.locationType", 
	"uniqueIdType@odata.type" : "#microsoft.graph.locationUniqueIdType", 
}
serviceLocation.SetAdditionalData(additionalData)
requestBody.SetServiceLocation(serviceLocation)
serviceName := "Catered bento"
requestBody.SetServiceName(&serviceName) 
serviceNotes := "Customer requires punctual service."
requestBody.SetServiceNotes(&serviceNotes) 
staffMemberIds := []string {
	"8ee1c803-a1fa-406d-8259-7ab53233f148",
}
requestBody.SetStaffMemberIds(staffMemberIds)
maximumAttendeesCount := int32(5)
requestBody.SetMaximumAttendeesCount(&maximumAttendeesCount) 
filledAttendeesCount := int32(1)
requestBody.SetFilledAttendeesCount(&filledAttendeesCount) 


bookingCustomerInformationBase := graphmodels.NewBookingCustomerInformation()
customerId := "7ed53fa5-9ef2-4f2f-975b-27447440bc09"
bookingCustomerInformationBase.SetCustomerId(&customerId) 
name := "Jordan Miller"
bookingCustomerInformationBase.SetName(&name) 
emailAddress := "jordanm@contoso.com"
bookingCustomerInformationBase.SetEmailAddress(&emailAddress) 
phone := "213-555-0199"
bookingCustomerInformationBase.SetPhone(&phone) 
notes := null
bookingCustomerInformationBase.SetNotes(&notes) 
location := graphmodels.NewLocation()
displayName := "Customer"
location.SetDisplayName(&displayName) 
locationEmailAddress := null
location.SetLocationEmailAddress(&locationEmailAddress) 
locationUri := ""
location.SetLocationUri(&locationUri) 
locationType := null
location.SetLocationType(&locationType) 
uniqueId := null
location.SetUniqueId(&uniqueId) 
uniqueIdType := null
location.SetUniqueIdType(&uniqueIdType) 
address := graphmodels.NewPhysicalAddress()
street := ""
address.SetStreet(&street) 
city := ""
address.SetCity(&city) 
state := ""
address.SetState(&state) 
countryOrRegion := ""
address.SetCountryOrRegion(&countryOrRegion) 
postalCode := ""
address.SetPostalCode(&postalCode) 
location.SetAddress(address)
coordinates := graphmodels.NewOutlookGeoCoordinates()
altitude := null
coordinates.SetAltitude(&altitude) 
latitude := null
coordinates.SetLatitude(&latitude) 
longitude := null
coordinates.SetLongitude(&longitude) 
accuracy := null
coordinates.SetAccuracy(&accuracy) 
altitudeAccuracy := null
coordinates.SetAltitudeAccuracy(&altitudeAccuracy) 
location.SetCoordinates(coordinates)
bookingCustomerInformationBase.SetLocation(location)
timeZone := "America/Chicago"
bookingCustomerInformationBase.SetTimeZone(&timeZone) 


bookingQuestionAnswer := graphmodels.NewBookingQuestionAnswer()
questionId := "3bc6fde0-4ad3-445d-ab17-0fc15dba0774"
bookingQuestionAnswer.SetQuestionId(&questionId) 
question := "What is your age?"
bookingQuestionAnswer.SetQuestion(&question) 
answerInputType := graphmodels.TEXT_ANSWERINPUTTYPE 
bookingQuestionAnswer.SetAnswerInputType(&answerInputType) 
answerOptions := []string {

}
bookingQuestionAnswer.SetAnswerOptions(answerOptions)
isRequired := true
bookingQuestionAnswer.SetIsRequired(&isRequired) 
answer := "25"
bookingQuestionAnswer.SetAnswer(&answer) 
selectedOptions := []string {

}
bookingQuestionAnswer.SetSelectedOptions(selectedOptions)

customQuestionAnswers := []graphmodels.BookingQuestionAnswerable {
	bookingQuestionAnswer,
}
bookingCustomerInformationBase.SetCustomQuestionAnswers(customQuestionAnswers)

customers := []graphmodels.BookingCustomerInformationBaseable {
	bookingCustomerInformationBase,
}
requestBody.SetCustomers(customers)
additionalData := map[string]interface{}{
end := graphmodels.NewDateTimeTimeZone()
dateTime := "2018-05-01T12:30:00.0000000+00:00"
end.SetDateTime(&dateTime) 
timeZone := "UTC"
end.SetTimeZone(&timeZone) 
	requestBody.SetEnd(end)
	"priceType@odata.type" : "#microsoft.graph.bookingPriceType", 
	"reminders@odata.type" : "#Collection(microsoft.graph.bookingReminder)", 
start := graphmodels.NewDateTimeTimeZone()
dateTime := "2018-05-01T12:00:00.0000000+00:00"
start.SetDateTime(&dateTime) 
timeZone := "UTC"
start.SetTimeZone(&timeZone) 
	requestBody.SetStart(start)
	"customers@odata.type" : "#Collection(microsoft.graph.bookingCustomerInformation)", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
appointments, err := graphClient.Solutions().BookingBusinesses().ByBookingBusinessId("bookingBusiness-id").Appointments().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BookingAppointment bookingAppointment = new BookingAppointment();
bookingAppointment.setOdataType("#microsoft.graph.bookingAppointment");
bookingAppointment.setCustomerTimeZone("America/Chicago");
bookingAppointment.setCustomerName("Jordan Miller");
bookingAppointment.setCustomerEmailAddress("jordanm@contoso.com");
bookingAppointment.setCustomerPhone("213-555-0199");
bookingAppointment.setCustomerNotes(null);
bookingAppointment.setSmsNotificationsEnabled(true);
bookingAppointment.setIsCustomerAllowedToManageBooking(true);
bookingAppointment.setIsLocationOnline(true);
bookingAppointment.setOptOutOfCustomerEmail(false);
bookingAppointment.setAnonymousJoinWebUrl(null);
PeriodAndDuration postBuffer = PeriodAndDuration.ofDuration(Duration.parse("PT10M"));
bookingAppointment.setPostBuffer(postBuffer);
PeriodAndDuration preBuffer = PeriodAndDuration.ofDuration(Duration.parse("PT5M"));
bookingAppointment.setPreBuffer(preBuffer);
bookingAppointment.setPrice(10d);
bookingAppointment.setPriceType(BookingPriceType.FixedPrice);
LinkedList<BookingReminder> reminders = new LinkedList<BookingReminder>();
BookingReminder bookingReminder = new BookingReminder();
bookingReminder.setOdataType("#microsoft.graph.bookingReminder");
bookingReminder.setMessage("This service is tomorrow");
PeriodAndDuration offset = PeriodAndDuration.ofDuration(Duration.parse("P1D"));
bookingReminder.setOffset(offset);
bookingReminder.setRecipients(BookingReminderRecipients.AllAttendees);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("recipients@odata.type", "#microsoft.graph.bookingReminderRecipients");
bookingReminder.setAdditionalData(additionalData);
reminders.add(bookingReminder);
BookingReminder bookingReminder1 = new BookingReminder();
bookingReminder1.setOdataType("#microsoft.graph.bookingReminder");
bookingReminder1.setMessage("Please be available to enjoy your lunch service.");
PeriodAndDuration offset1 = PeriodAndDuration.ofDuration(Duration.parse("PT1H"));
bookingReminder1.setOffset(offset1);
bookingReminder1.setRecipients(BookingReminderRecipients.Customer);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("recipients@odata.type", "#microsoft.graph.bookingReminderRecipients");
bookingReminder1.setAdditionalData(additionalData1);
reminders.add(bookingReminder1);
BookingReminder bookingReminder2 = new BookingReminder();
bookingReminder2.setOdataType("#microsoft.graph.bookingReminder");
bookingReminder2.setMessage("Please check traffic for next cater.");
PeriodAndDuration offset2 = PeriodAndDuration.ofDuration(Duration.parse("PT2H"));
bookingReminder2.setOffset(offset2);
bookingReminder2.setRecipients(BookingReminderRecipients.Staff);
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
additionalData2.put("recipients@odata.type", "#microsoft.graph.bookingReminderRecipients");
bookingReminder2.setAdditionalData(additionalData2);
reminders.add(bookingReminder2);
bookingAppointment.setReminders(reminders);
bookingAppointment.setServiceId("57da6774-a087-4d69-b0e6-6fb82c339976");
Location serviceLocation = new Location();
serviceLocation.setOdataType("#microsoft.graph.location");
PhysicalAddress address = new PhysicalAddress();
address.setOdataType("#microsoft.graph.physicalAddress");
address.setCity("Buffalo");
address.setCountryOrRegion("USA");
address.setPostalCode("98052");
address.setState("NY");
address.setStreet("123 First Avenue");
HashMap<String, Object> additionalData3 = new HashMap<String, Object>();
additionalData3.put("postOfficeBox", null);
additionalData3.put("type@odata.type", "#microsoft.graph.physicalAddressType");
additionalData3.put("type", null);
address.setAdditionalData(additionalData3);
serviceLocation.setAddress(address);
serviceLocation.setCoordinates(null);
serviceLocation.setDisplayName("Customer location");
serviceLocation.setLocationEmailAddress(null);
serviceLocation.setLocationType(null);
serviceLocation.setLocationUri(null);
serviceLocation.setUniqueId(null);
serviceLocation.setUniqueIdType(null);
HashMap<String, Object> additionalData4 = new HashMap<String, Object>();
additionalData4.put("locationType@odata.type", "#microsoft.graph.locationType");
additionalData4.put("uniqueIdType@odata.type", "#microsoft.graph.locationUniqueIdType");
serviceLocation.setAdditionalData(additionalData4);
bookingAppointment.setServiceLocation(serviceLocation);
bookingAppointment.setServiceName("Catered bento");
bookingAppointment.setServiceNotes("Customer requires punctual service.");
LinkedList<String> staffMemberIds = new LinkedList<String>();
staffMemberIds.add("8ee1c803-a1fa-406d-8259-7ab53233f148");
bookingAppointment.setStaffMemberIds(staffMemberIds);
bookingAppointment.setMaximumAttendeesCount(5);
bookingAppointment.setFilledAttendeesCount(1);
LinkedList<BookingCustomerInformationBase> customers = new LinkedList<BookingCustomerInformationBase>();
BookingCustomerInformation bookingCustomerInformationBase = new BookingCustomerInformation();
bookingCustomerInformationBase.setOdataType("#microsoft.graph.bookingCustomerInformation");
bookingCustomerInformationBase.setCustomerId("7ed53fa5-9ef2-4f2f-975b-27447440bc09");
bookingCustomerInformationBase.setName("Jordan Miller");
bookingCustomerInformationBase.setEmailAddress("jordanm@contoso.com");
bookingCustomerInformationBase.setPhone("213-555-0199");
bookingCustomerInformationBase.setNotes(null);
Location location = new Location();
location.setOdataType("#microsoft.graph.location");
location.setDisplayName("Customer");
location.setLocationEmailAddress(null);
location.setLocationUri("");
location.setLocationType(null);
location.setUniqueId(null);
location.setUniqueIdType(null);
PhysicalAddress address1 = new PhysicalAddress();
address1.setOdataType("#microsoft.graph.physicalAddress");
address1.setStreet("");
address1.setCity("");
address1.setState("");
address1.setCountryOrRegion("");
address1.setPostalCode("");
location.setAddress(address1);
OutlookGeoCoordinates coordinates1 = new OutlookGeoCoordinates();
coordinates1.setAltitude(null);
coordinates1.setLatitude(null);
coordinates1.setLongitude(null);
coordinates1.setAccuracy(null);
coordinates1.setAltitudeAccuracy(null);
location.setCoordinates(coordinates1);
bookingCustomerInformationBase.setLocation(location);
bookingCustomerInformationBase.setTimeZone("America/Chicago");
LinkedList<BookingQuestionAnswer> customQuestionAnswers = new LinkedList<BookingQuestionAnswer>();
BookingQuestionAnswer bookingQuestionAnswer = new BookingQuestionAnswer();
bookingQuestionAnswer.setQuestionId("3bc6fde0-4ad3-445d-ab17-0fc15dba0774");
bookingQuestionAnswer.setQuestion("What is your age?");
bookingQuestionAnswer.setAnswerInputType(AnswerInputType.Text);
LinkedList<String> answerOptions = new LinkedList<String>();
bookingQuestionAnswer.setAnswerOptions(answerOptions);
bookingQuestionAnswer.setIsRequired(true);
bookingQuestionAnswer.setAnswer("25");
LinkedList<String> selectedOptions = new LinkedList<String>();
bookingQuestionAnswer.setSelectedOptions(selectedOptions);
customQuestionAnswers.add(bookingQuestionAnswer);
bookingCustomerInformationBase.setCustomQuestionAnswers(customQuestionAnswers);
customers.add(bookingCustomerInformationBase);
bookingAppointment.setCustomers(customers);
HashMap<String, Object> additionalData5 = new HashMap<String, Object>();
DateTimeTimeZone end = new DateTimeTimeZone();
end.setOdataType("#microsoft.graph.dateTimeTimeZone");
end.setDateTime("2018-05-01T12:30:00.0000000+00:00");
end.setTimeZone("UTC");
additionalData5.put("end", end);
additionalData5.put("priceType@odata.type", "#microsoft.graph.bookingPriceType");
additionalData5.put("reminders@odata.type", "#Collection(microsoft.graph.bookingReminder)");
DateTimeTimeZone start = new DateTimeTimeZone();
start.setOdataType("#microsoft.graph.dateTimeTimeZone");
start.setDateTime("2018-05-01T12:00:00.0000000+00:00");
start.setTimeZone("UTC");
additionalData5.put("start", start);
additionalData5.put("customers@odata.type", "#Collection(microsoft.graph.bookingCustomerInformation)");
bookingAppointment.setAdditionalData(additionalData5);
BookingAppointment result = graphClient.solutions().bookingBusinesses().byBookingBusinessId("{bookingBusiness-id}").appointments().post(bookingAppointment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const bookingAppointment = {
    '@odata.type': '#microsoft.graph.bookingAppointment',
    customerTimeZone: 'America/Chicago',
    customerName: 'Jordan Miller',
    customerEmailAddress: 'jordanm@contoso.com',
    customerPhone: '213-555-0199',
    customerNotes: null,	
    smsNotificationsEnabled: true,
    end: {
        '@odata.type': '#microsoft.graph.dateTimeTimeZone',
        dateTime: '2018-05-01T12:30:00.0000000+00:00',
        timeZone: 'UTC'
    },
    isCustomerAllowedToManageBooking: true,
    isLocationOnline: true,
    optOutOfCustomerEmail: false,
    anonymousJoinWebUrl: null,
    postBuffer: 'PT10M',
    preBuffer: 'PT5M',
    price: 10.0,
    'priceType@odata.type': '#microsoft.graph.bookingPriceType',
    priceType: 'fixedPrice',
    'reminders@odata.type': '#Collection(microsoft.graph.bookingReminder)',
    reminders: [
        {
            '@odata.type': '#microsoft.graph.bookingReminder',
            message: 'This service is tomorrow',
            offset: 'P1D',
            'recipients@odata.type': '#microsoft.graph.bookingReminderRecipients',
            recipients: 'allAttendees'
        },
        {
            '@odata.type': '#microsoft.graph.bookingReminder',
            message: 'Please be available to enjoy your lunch service.',
            offset: 'PT1H',
            'recipients@odata.type': '#microsoft.graph.bookingReminderRecipients',
            recipients: 'customer'
        },
        {
            '@odata.type': '#microsoft.graph.bookingReminder',
            message: 'Please check traffic for next cater.',
            offset: 'PT2H',
            'recipients@odata.type': '#microsoft.graph.bookingReminderRecipients',
            recipients: 'staff'
        }
    ],
    serviceId: '57da6774-a087-4d69-b0e6-6fb82c339976',
    serviceLocation: {
        '@odata.type': '#microsoft.graph.location',
        address: {
            '@odata.type': '#microsoft.graph.physicalAddress',
            city: 'Buffalo',
            countryOrRegion: 'USA',
            postalCode: '98052',
            postOfficeBox: null,
            state: 'NY',
            street: '123 First Avenue',
            'type@odata.type': '#microsoft.graph.physicalAddressType',
            type: null
        },
        coordinates: null,
        displayName: 'Customer location',
        locationEmailAddress: null,
        'locationType@odata.type': '#microsoft.graph.locationType',
        locationType: null,
        locationUri: null,
        uniqueId: null,
        'uniqueIdType@odata.type': '#microsoft.graph.locationUniqueIdType',
        uniqueIdType: null
    },
    serviceName: 'Catered bento',
    serviceNotes: 'Customer requires punctual service.',
    staffMemberIds: [
      '8ee1c803-a1fa-406d-8259-7ab53233f148'
    ],
    start: {
        '@odata.type': '#microsoft.graph.dateTimeTimeZone',
        dateTime: '2018-05-01T12:00:00.0000000+00:00',
        timeZone: 'UTC'
    },
    maximumAttendeesCount: 5,
    filledAttendeesCount: 1,
    'customers@odata.type': '#Collection(microsoft.graph.bookingCustomerInformation)',
    customers: [
        {
            '@odata.type': '#microsoft.graph.bookingCustomerInformation',
            customerId: '7ed53fa5-9ef2-4f2f-975b-27447440bc09',
            name: 'Jordan Miller',
            emailAddress: 'jordanm@contoso.com',
            phone: '213-555-0199',
            notes: null,
            location: {
                '@odata.type': '#microsoft.graph.location',
                displayName: 'Customer',
                locationEmailAddress: null,
                locationUri: '',
                locationType: null,
                uniqueId: null,
                uniqueIdType: null,
                address: {
                    '@odata.type': '#microsoft.graph.physicalAddress',
                    street: '',
                    city: '',
                    state: '',
                    countryOrRegion: '',
                    postalCode: ''
                },
                coordinates: {
                    altitude: null,
                    latitude: null,
                    longitude: null,
                    accuracy: null,
                    altitudeAccuracy: null
                }
            },
            timeZone: 'America/Chicago',
            customQuestionAnswers: [
                {
                    questionId: '3bc6fde0-4ad3-445d-ab17-0fc15dba0774',
                    question: 'What is your age?',
                    answerInputType: 'text',
                    answerOptions: [],
                    isRequired: true,
                    answer: '25',
                    selectedOptions: []
                }
            ]
        }
    ]
};

await client.api('/solutions/bookingBusinesses/Contosolunchdelivery@contoso.com/appointments')
	.post(bookingAppointment);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\BookingAppointment;
use Microsoft\Graph\Generated\Models\BookingPriceType;
use Microsoft\Graph\Generated\Models\BookingReminder;
use Microsoft\Graph\Generated\Models\BookingReminderRecipients;
use Microsoft\Graph\Generated\Models\Location;
use Microsoft\Graph\Generated\Models\PhysicalAddress;
use Microsoft\Graph\Generated\Models\BookingCustomerInformationBase;
use Microsoft\Graph\Generated\Models\BookingCustomerInformation;
use Microsoft\Graph\Generated\Models\OutlookGeoCoordinates;
use Microsoft\Graph\Generated\Models\BookingQuestionAnswer;
use Microsoft\Graph\Generated\Models\AnswerInputType;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BookingAppointment();
$requestBody->setOdataType('#microsoft.graph.bookingAppointment');
$requestBody->setCustomerTimeZone('America/Chicago');
$requestBody->setCustomerName('Jordan Miller');
$requestBody->setCustomerEmailAddress('jordanm@contoso.com');
$requestBody->setCustomerPhone('213-555-0199');
$requestBody->setCustomerNotes(null);
$requestBody->setSmsNotificationsEnabled(true);
$requestBody->setIsCustomerAllowedToManageBooking(true);
$requestBody->setIsLocationOnline(true);
$requestBody->setOptOutOfCustomerEmail(false);
$requestBody->setAnonymousJoinWebUrl(null);
$requestBody->setPostBuffer(new \DateInterval('PT10M'));
$requestBody->setPreBuffer(new \DateInterval('PT5M'));
$requestBody->setPrice(10);
$requestBody->setPriceType(new BookingPriceType('fixedPrice'));
$remindersBookingReminder1 = new BookingReminder();
$remindersBookingReminder1->setOdataType('#microsoft.graph.bookingReminder');
$remindersBookingReminder1->setMessage('This service is tomorrow');
$remindersBookingReminder1->setOffset(new \DateInterval('P1D'));
$remindersBookingReminder1->setRecipients(new BookingReminderRecipients('allAttendees'));
$additionalData = [
	'recipients@odata.type' => '#microsoft.graph.bookingReminderRecipients',
];
$remindersBookingReminder1->setAdditionalData($additionalData);
$remindersArray []= $remindersBookingReminder1;
$remindersBookingReminder2 = new BookingReminder();
$remindersBookingReminder2->setOdataType('#microsoft.graph.bookingReminder');
$remindersBookingReminder2->setMessage('Please be available to enjoy your lunch service.');
$remindersBookingReminder2->setOffset(new \DateInterval('PT1H'));
$remindersBookingReminder2->setRecipients(new BookingReminderRecipients('customer'));
$additionalData = [
	'recipients@odata.type' => '#microsoft.graph.bookingReminderRecipients',
];
$remindersBookingReminder2->setAdditionalData($additionalData);
$remindersArray []= $remindersBookingReminder2;
$remindersBookingReminder3 = new BookingReminder();
$remindersBookingReminder3->setOdataType('#microsoft.graph.bookingReminder');
$remindersBookingReminder3->setMessage('Please check traffic for next cater.');
$remindersBookingReminder3->setOffset(new \DateInterval('PT2H'));
$remindersBookingReminder3->setRecipients(new BookingReminderRecipients('staff'));
$additionalData = [
	'recipients@odata.type' => '#microsoft.graph.bookingReminderRecipients',
];
$remindersBookingReminder3->setAdditionalData($additionalData);
$remindersArray []= $remindersBookingReminder3;
$requestBody->setReminders($remindersArray);

$requestBody->setServiceId('57da6774-a087-4d69-b0e6-6fb82c339976');
$serviceLocation = new Location();
$serviceLocation->setOdataType('#microsoft.graph.location');
$serviceLocationAddress = new PhysicalAddress();
$serviceLocationAddress->setOdataType('#microsoft.graph.physicalAddress');
$serviceLocationAddress->setCity('Buffalo');
$serviceLocationAddress->setCountryOrRegion('USA');
$serviceLocationAddress->setPostalCode('98052');
$serviceLocationAddress->setState('NY');
$serviceLocationAddress->setStreet('123 First Avenue');
$additionalData = [
'postOfficeBox' => null,
'type@odata.type' => '#microsoft.graph.physicalAddressType',
'type' => null,
];
$serviceLocationAddress->setAdditionalData($additionalData);
$serviceLocation->setAddress($serviceLocationAddress);
$serviceLocation->setCoordinates(null);
$serviceLocation->setDisplayName('Customer location');
$serviceLocation->setLocationEmailAddress(null);
$serviceLocation->setLocationType(null);
$serviceLocation->setLocationUri(null);
$serviceLocation->setUniqueId(null);
$serviceLocation->setUniqueIdType(null);
$additionalData = [
'locationType@odata.type' => '#microsoft.graph.locationType',
'uniqueIdType@odata.type' => '#microsoft.graph.locationUniqueIdType',
];
$serviceLocation->setAdditionalData($additionalData);
$requestBody->setServiceLocation($serviceLocation);
$requestBody->setServiceName('Catered bento');
$requestBody->setServiceNotes('Customer requires punctual service.');
$requestBody->setStaffMemberIds(['8ee1c803-a1fa-406d-8259-7ab53233f148', ]);
$requestBody->setMaximumAttendeesCount(5);
$requestBody->setFilledAttendeesCount(1);
$customersBookingCustomerInformationBase1 = new BookingCustomerInformation();
$customersBookingCustomerInformationBase1->setOdataType('#microsoft.graph.bookingCustomerInformation');
$customersBookingCustomerInformationBase1->setCustomerId('7ed53fa5-9ef2-4f2f-975b-27447440bc09');
$customersBookingCustomerInformationBase1->setName('Jordan Miller');
$customersBookingCustomerInformationBase1->setEmailAddress('jordanm@contoso.com');
$customersBookingCustomerInformationBase1->setPhone('213-555-0199');
$customersBookingCustomerInformationBase1->setNotes(null);
$customersBookingCustomerInformationBase1Location = new Location();
$customersBookingCustomerInformationBase1Location->setOdataType('#microsoft.graph.location');
$customersBookingCustomerInformationBase1Location->setDisplayName('Customer');
$customersBookingCustomerInformationBase1Location->setLocationEmailAddress(null);
$customersBookingCustomerInformationBase1Location->setLocationUri('');
$customersBookingCustomerInformationBase1Location->setLocationType(null);
$customersBookingCustomerInformationBase1Location->setUniqueId(null);
$customersBookingCustomerInformationBase1Location->setUniqueIdType(null);
$customersBookingCustomerInformationBase1LocationAddress = new PhysicalAddress();
$customersBookingCustomerInformationBase1LocationAddress->setOdataType('#microsoft.graph.physicalAddress');
$customersBookingCustomerInformationBase1LocationAddress->setStreet('');
$customersBookingCustomerInformationBase1LocationAddress->setCity('');
$customersBookingCustomerInformationBase1LocationAddress->setState('');
$customersBookingCustomerInformationBase1LocationAddress->setCountryOrRegion('');
$customersBookingCustomerInformationBase1LocationAddress->setPostalCode('');
$customersBookingCustomerInformationBase1Location->setAddress($customersBookingCustomerInformationBase1LocationAddress);
$customersBookingCustomerInformationBase1LocationCoordinates = new OutlookGeoCoordinates();
$customersBookingCustomerInformationBase1LocationCoordinates->setAltitude(null);
$customersBookingCustomerInformationBase1LocationCoordinates->setLatitude(null);
$customersBookingCustomerInformationBase1LocationCoordinates->setLongitude(null);
$customersBookingCustomerInformationBase1LocationCoordinates->setAccuracy(null);
$customersBookingCustomerInformationBase1LocationCoordinates->setAltitudeAccuracy(null);
$customersBookingCustomerInformationBase1Location->setCoordinates($customersBookingCustomerInformationBase1LocationCoordinates);
$customersBookingCustomerInformationBase1->setLocation($customersBookingCustomerInformationBase1Location);
$customersBookingCustomerInformationBase1->setTimeZone('America/Chicago');
$customQuestionAnswersBookingQuestionAnswer1 = new BookingQuestionAnswer();
$customQuestionAnswersBookingQuestionAnswer1->setQuestionId('3bc6fde0-4ad3-445d-ab17-0fc15dba0774');
$customQuestionAnswersBookingQuestionAnswer1->setQuestion('What is your age?');
$customQuestionAnswersBookingQuestionAnswer1->setAnswerInputType(new AnswerInputType('text'));
$customQuestionAnswersBookingQuestionAnswer1->setAnswerOptions([]);
$customQuestionAnswersBookingQuestionAnswer1->setIsRequired(true);
$customQuestionAnswersBookingQuestionAnswer1->setAnswer('25');
$customQuestionAnswersBookingQuestionAnswer1->setSelectedOptions([]);
$customQuestionAnswersArray []= $customQuestionAnswersBookingQuestionAnswer1;
$customersBookingCustomerInformationBase1->setCustomQuestionAnswers($customQuestionAnswersArray);

$customersArray []= $customersBookingCustomerInformationBase1;
$requestBody->setCustomers($customersArray);

$additionalData = [
'end' => [
'@odata.type' => '#microsoft.graph.dateTimeTimeZone',
'dateTime' => '2018-05-01T12:30:00.0000000+00:00',
'timeZone' => 'UTC',
],
'priceType@odata.type' => '#microsoft.graph.bookingPriceType',
'reminders@odata.type' => '#Collection(microsoft.graph.bookingReminder)',
'start' => [
'@odata.type' => '#microsoft.graph.dateTimeTimeZone',
'dateTime' => '2018-05-01T12:00:00.0000000+00:00',
'timeZone' => 'UTC',
],
'customers@odata.type' => '#Collection(microsoft.graph.bookingCustomerInformation)',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->solutions()->bookingBusinesses()->byBookingBusinessId('bookingBusiness-id')->appointments()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.booking_appointment import BookingAppointment
from msgraph.generated.models.booking_price_type import BookingPriceType
from msgraph.generated.models.booking_reminder import BookingReminder
from msgraph.generated.models.booking_reminder_recipients import BookingReminderRecipients
from msgraph.generated.models.location import Location
from msgraph.generated.models.physical_address import PhysicalAddress
from msgraph.generated.models.booking_customer_information_base import BookingCustomerInformationBase
from msgraph.generated.models.booking_customer_information import BookingCustomerInformation
from msgraph.generated.models.outlook_geo_coordinates import OutlookGeoCoordinates
from msgraph.generated.models.booking_question_answer import BookingQuestionAnswer
from msgraph.generated.models.answer_input_type import AnswerInputType
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BookingAppointment(
	odata_type = "#microsoft.graph.bookingAppointment",
	customer_time_zone = "America/Chicago",
	customer_name = "Jordan Miller",
	customer_email_address = "jordanm@contoso.com",
	customer_phone = "213-555-0199",
	customer_notes = None,
	sms_notifications_enabled = True,
	is_customer_allowed_to_manage_booking = True,
	is_location_online = True,
	opt_out_of_customer_email = False,
	anonymous_join_web_url = None,
	post_buffer = "PT10M",
	pre_buffer = "PT5M",
	price = 10,
	price_type = BookingPriceType.FixedPrice,
	reminders = [
		BookingReminder(
			odata_type = "#microsoft.graph.bookingReminder",
			message = "This service is tomorrow",
			offset = "P1D",
			recipients = BookingReminderRecipients.AllAttendees,
			additional_data = {
					"recipients@odata_type" : "#microsoft.graph.bookingReminderRecipients",
			}
		),
		BookingReminder(
			odata_type = "#microsoft.graph.bookingReminder",
			message = "Please be available to enjoy your lunch service.",
			offset = "PT1H",
			recipients = BookingReminderRecipients.Customer,
			additional_data = {
					"recipients@odata_type" : "#microsoft.graph.bookingReminderRecipients",
			}
		),
		BookingReminder(
			odata_type = "#microsoft.graph.bookingReminder",
			message = "Please check traffic for next cater.",
			offset = "PT2H",
			recipients = BookingReminderRecipients.Staff,
			additional_data = {
					"recipients@odata_type" : "#microsoft.graph.bookingReminderRecipients",
			}
		),
	],
	service_id = "57da6774-a087-4d69-b0e6-6fb82c339976",
	service_location = Location(
		odata_type = "#microsoft.graph.location",
		address = PhysicalAddress(
			odata_type = "#microsoft.graph.physicalAddress",
			city = "Buffalo",
			country_or_region = "USA",
			postal_code = "98052",
			state = "NY",
			street = "123 First Avenue",
			additional_data = {
					"post_office_box" : None,
					"type@odata_type" : "#microsoft.graph.physicalAddressType",
					"type" : None,
			}
		),
		coordinates = None,
		display_name = "Customer location",
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
	service_name = "Catered bento",
	service_notes = "Customer requires punctual service.",
	staff_member_ids = [
		"8ee1c803-a1fa-406d-8259-7ab53233f148",
	],
	maximum_attendees_count = 5,
	filled_attendees_count = 1,
	customers = [
		BookingCustomerInformation(
			odata_type = "#microsoft.graph.bookingCustomerInformation",
			customer_id = "7ed53fa5-9ef2-4f2f-975b-27447440bc09",
			name = "Jordan Miller",
			email_address = "jordanm@contoso.com",
			phone = "213-555-0199",
			notes = None,
			location = Location(
				odata_type = "#microsoft.graph.location",
				display_name = "Customer",
				location_email_address = None,
				location_uri = "",
				location_type = None,
				unique_id = None,
				unique_id_type = None,
				address = PhysicalAddress(
					odata_type = "#microsoft.graph.physicalAddress",
					street = "",
					city = "",
					state = "",
					country_or_region = "",
					postal_code = "",
				),
				coordinates = OutlookGeoCoordinates(
					altitude = None,
					latitude = None,
					longitude = None,
					accuracy = None,
					altitude_accuracy = None,
				),
			),
			time_zone = "America/Chicago",
			custom_question_answers = [
				BookingQuestionAnswer(
					question_id = "3bc6fde0-4ad3-445d-ab17-0fc15dba0774",
					question = "What is your age?",
					answer_input_type = AnswerInputType.Text,
					answer_options = [
					],
					is_required = True,
					answer = "25",
					selected_options = [
					],
				),
			],
		),
	],
	additional_data = {
			"end" : {
					"@odata_type" : "#microsoft.graph.dateTimeTimeZone",
					"date_time" : "2018-05-01T12:30:00.0000000+00:00",
					"time_zone" : "UTC",
			},
			"price_type@odata_type" : "#microsoft.graph.bookingPriceType",
			"reminders@odata_type" : "#Collection(microsoft.graph.bookingReminder)",
			"start" : {
					"@odata_type" : "#microsoft.graph.dateTimeTimeZone",
					"date_time" : "2018-05-01T12:00:00.0000000+00:00",
					"time_zone" : "UTC",
			},
			"customers@odata_type" : "#Collection(microsoft.graph.bookingCustomerInformation)",
	}
)

result = await graph_client.solutions.booking_businesses.by_booking_business_id('bookingBusiness-id').appointments.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/solutions/$metadata#bookingBusinesses('Contosolunchdelivery%40contoso.com')/appointments/$entity",
    "id": "AAMkADc7zF4J0AAA8v_KnAAA=",
    "selfServiceAppointmentId": "00000000-0000-0000-0000-000000000000",
    "isLocationOnline": true,
    "joinWebUrl": "https://teams.microsoft.com/l/meetup-join/19%3ameeting_MTlhZTE3MDUtODk0Yy00MGZkLTlhNzktN2FmYTk3MDUxNmE2%40thread.v2/0?context=%7b%22Tid%22%3a%22995fa18c-b557-4694-8d07-b89779d6dc77%22%2c%22Oid%22%3a%22d4d260ab-989d-490e-b121-e2066391807a%22%7d",
    "smsNotificationsEnabled": true,
    "customerName": "Jordan Miller",
    "customerEmailAddress": "jordanm@contoso.com",
    "customerPhone": "213-555-0199",
    "customerNotes": null,	
    "customerTimeZone": "America/Chicago",
    "serviceId": "57da6774-a087-4d69-b0e6-6fb82c339976",
    "serviceName": "Catered bento",
    "duration": "PT30M",
    "preBuffer": "PT5M",
    "postBuffer": "PT10M",
    "priceType": "fixedPrice",
    "price": 10.0,
    "serviceNotes": "Customer requires punctual service.",
    "optOutOfCustomerEmail": false,
    "anonymousJoinWebUrl": null,
    "isCustomerAllowedToManageBooking": true,
    "staffMemberIds": [
      "8ee1c803-a1fa-406d-8259-7ab53233f148"
    ],
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
    "reminders": [
        {
            "offset": "P1D",
            "recipients": "allAttendees",
            "message": "This service is tomorrow"
        },
        {
            "offset": "PT1H",
            "recipients": "customer",
            "message": "Please be available to enjoy your lunch service."
        },
        {
            "offset": "PT2H",
            "recipients": "staff",
            "message": "Please check traffic for next cater."
        }
    ],
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
                "@odata.type": "#microsoft.graph.location",
                "displayName": "Customer",
                "locationEmailAddress": null,
                "locationUri": "",
                "locationType": null,
                "uniqueId": null,
                "uniqueIdType": null,
                "address": {
                    "@odata.type": "#microsoft.graph.physicalAddress",
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
    ]
}
```
