<!-- Source: https://learn.microsoft.com/en-us/graph/api/bookingbusiness-post-staffmembers?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create bookingStaffMember

Namespace: microsoft.graph

Create a new [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) in the specified [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0).

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
POST /solutions/bookingBusinesses/{id}/staffMembers
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {code}. Required. |

## Request body

In the request body, supply a JSON representation of a [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) object. You must include the following properties:

- **displayName**
- **emailAddress**
- **role**

## Response

If successful, this method returns a `201 Created` response code and a [bookingStaffMember](https://learn.microsoft.com/en-us/graph/api/resources/bookingstaffmember?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/{id}/staffMembers
Content-type: application/json

{
    "@odata.type":"#microsoft.graph.bookingStaffMember",
    "displayName":"Dana Swope",
    "emailAddress":"danas@contoso.com",
    "role@odata.type":"#microsoft.graph.bookingStaffRole",
    "role":"externalGuest",
    "timeZone":"America/Chicago",
    "useBusinessHours":true,
    "workingHours@odata.type":"#Collection(microsoft.graph.bookingWorkHours)",
    "workingHours":[
        {
            "@odata.type":"#microsoft.graph.bookingWorkHours",
            "day@odata.type":"#microsoft.graph.dayOfWeek",
            "day":"monday",
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
    ],
    "isEmailNotificationEnabled": false
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new BookingStaffMember
{
	OdataType = "#microsoft.graph.bookingStaffMember",
	DisplayName = "Dana Swope",
	EmailAddress = "danas@contoso.com",
	Role = BookingStaffRole.ExternalGuest,
	TimeZone = "America/Chicago",
	UseBusinessHours = true,
	WorkingHours = new List<BookingWorkHours>
	{
		new BookingWorkHours
		{
			OdataType = "#microsoft.graph.bookingWorkHours",
			Day = DayOfWeekObject.Monday,
			TimeSlots = new List<BookingWorkTimeSlot>
			{
				new BookingWorkTimeSlot
				{
					OdataType = "#microsoft.graph.bookingWorkTimeSlot",
					EndTime = new Time(DateTime.Parse("17:00:00.0000000")),
					StartTime = new Time(DateTime.Parse("08:00:00.0000000")),
				},
			},
			AdditionalData = new Dictionary<string, object>
			{
				{
					"day@odata.type" , "#microsoft.graph.dayOfWeek"
				},
				{
					"timeSlots@odata.type" , "#Collection(microsoft.graph.bookingWorkTimeSlot)"
				},
			},
		},
		new BookingWorkHours
		{
			OdataType = "#microsoft.graph.bookingWorkHours",
			Day = DayOfWeekObject.Tuesday,
			TimeSlots = new List<BookingWorkTimeSlot>
			{
				new BookingWorkTimeSlot
				{
					OdataType = "#microsoft.graph.bookingWorkTimeSlot",
					EndTime = new Time(DateTime.Parse("17:00:00.0000000")),
					StartTime = new Time(DateTime.Parse("08:00:00.0000000")),
				},
			},
			AdditionalData = new Dictionary<string, object>
			{
				{
					"day@odata.type" , "#microsoft.graph.dayOfWeek"
				},
				{
					"timeSlots@odata.type" , "#Collection(microsoft.graph.bookingWorkTimeSlot)"
				},
			},
		},
		new BookingWorkHours
		{
			OdataType = "#microsoft.graph.bookingWorkHours",
			Day = DayOfWeekObject.Wednesday,
			TimeSlots = new List<BookingWorkTimeSlot>
			{
				new BookingWorkTimeSlot
				{
					OdataType = "#microsoft.graph.bookingWorkTimeSlot",
					EndTime = new Time(DateTime.Parse("17:00:00.0000000")),
					StartTime = new Time(DateTime.Parse("08:00:00.0000000")),
				},
			},
			AdditionalData = new Dictionary<string, object>
			{
				{
					"day@odata.type" , "#microsoft.graph.dayOfWeek"
				},
				{
					"timeSlots@odata.type" , "#Collection(microsoft.graph.bookingWorkTimeSlot)"
				},
			},
		},
		new BookingWorkHours
		{
			OdataType = "#microsoft.graph.bookingWorkHours",
			Day = DayOfWeekObject.Thursday,
			TimeSlots = new List<BookingWorkTimeSlot>
			{
				new BookingWorkTimeSlot
				{
					OdataType = "#microsoft.graph.bookingWorkTimeSlot",
					EndTime = new Time(DateTime.Parse("17:00:00.0000000")),
					StartTime = new Time(DateTime.Parse("08:00:00.0000000")),
				},
			},
			AdditionalData = new Dictionary<string, object>
			{
				{
					"day@odata.type" , "#microsoft.graph.dayOfWeek"
				},
				{
					"timeSlots@odata.type" , "#Collection(microsoft.graph.bookingWorkTimeSlot)"
				},
			},
		},
		new BookingWorkHours
		{
			OdataType = "#microsoft.graph.bookingWorkHours",
			Day = DayOfWeekObject.Friday,
			TimeSlots = new List<BookingWorkTimeSlot>
			{
				new BookingWorkTimeSlot
				{
					OdataType = "#microsoft.graph.bookingWorkTimeSlot",
					EndTime = new Time(DateTime.Parse("17:00:00.0000000")),
					StartTime = new Time(DateTime.Parse("08:00:00.0000000")),
				},
			},
			AdditionalData = new Dictionary<string, object>
			{
				{
					"day@odata.type" , "#microsoft.graph.dayOfWeek"
				},
				{
					"timeSlots@odata.type" , "#Collection(microsoft.graph.bookingWorkTimeSlot)"
				},
			},
		},
	},
	IsEmailNotificationEnabled = false,
	AdditionalData = new Dictionary<string, object>
	{
		{
			"role@odata.type" , "#microsoft.graph.bookingStaffRole"
		},
		{
			"workingHours@odata.type" , "#Collection(microsoft.graph.bookingWorkHours)"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BookingBusinesses["{bookingBusiness-id}"].StaffMembers.PostAsync(requestBody);
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

requestBody := graphmodels.NewBookingStaffMemberBase()
displayName := "Dana Swope"
requestBody.SetDisplayName(&displayName) 
emailAddress := "danas@contoso.com"
requestBody.SetEmailAddress(&emailAddress) 
role := graphmodels.EXTERNALGUEST_BOOKINGSTAFFROLE 
requestBody.SetRole(&role) 
timeZone := "America/Chicago"
requestBody.SetTimeZone(&timeZone) 
useBusinessHours := true
requestBody.SetUseBusinessHours(&useBusinessHours) 


bookingWorkHours := graphmodels.NewBookingWorkHours()
day := graphmodels.MONDAY_DAYOFWEEK 
bookingWorkHours.SetDay(&day) 


bookingWorkTimeSlot := graphmodels.NewBookingWorkTimeSlot()
endTime := 17:00:00.0000000
bookingWorkTimeSlot.SetEndTime(&endTime) 
startTime := 08:00:00.0000000
bookingWorkTimeSlot.SetStartTime(&startTime) 

timeSlots := []graphmodels.BookingWorkTimeSlotable {
	bookingWorkTimeSlot,
}
bookingWorkHours.SetTimeSlots(timeSlots)
additionalData := map[string]interface{}{
	"day@odata.type" : "#microsoft.graph.dayOfWeek", 
	"timeSlots@odata.type" : "#Collection(microsoft.graph.bookingWorkTimeSlot)", 
}
bookingWorkHours.SetAdditionalData(additionalData)
bookingWorkHours1 := graphmodels.NewBookingWorkHours()
day := graphmodels.TUESDAY_DAYOFWEEK 
bookingWorkHours1.SetDay(&day) 


bookingWorkTimeSlot := graphmodels.NewBookingWorkTimeSlot()
endTime := 17:00:00.0000000
bookingWorkTimeSlot.SetEndTime(&endTime) 
startTime := 08:00:00.0000000
bookingWorkTimeSlot.SetStartTime(&startTime) 

timeSlots := []graphmodels.BookingWorkTimeSlotable {
	bookingWorkTimeSlot,
}
bookingWorkHours1.SetTimeSlots(timeSlots)
additionalData := map[string]interface{}{
	"day@odata.type" : "#microsoft.graph.dayOfWeek", 
	"timeSlots@odata.type" : "#Collection(microsoft.graph.bookingWorkTimeSlot)", 
}
bookingWorkHours1.SetAdditionalData(additionalData)
bookingWorkHours2 := graphmodels.NewBookingWorkHours()
day := graphmodels.WEDNESDAY_DAYOFWEEK 
bookingWorkHours2.SetDay(&day) 


bookingWorkTimeSlot := graphmodels.NewBookingWorkTimeSlot()
endTime := 17:00:00.0000000
bookingWorkTimeSlot.SetEndTime(&endTime) 
startTime := 08:00:00.0000000
bookingWorkTimeSlot.SetStartTime(&startTime) 

timeSlots := []graphmodels.BookingWorkTimeSlotable {
	bookingWorkTimeSlot,
}
bookingWorkHours2.SetTimeSlots(timeSlots)
additionalData := map[string]interface{}{
	"day@odata.type" : "#microsoft.graph.dayOfWeek", 
	"timeSlots@odata.type" : "#Collection(microsoft.graph.bookingWorkTimeSlot)", 
}
bookingWorkHours2.SetAdditionalData(additionalData)
bookingWorkHours3 := graphmodels.NewBookingWorkHours()
day := graphmodels.THURSDAY_DAYOFWEEK 
bookingWorkHours3.SetDay(&day) 


bookingWorkTimeSlot := graphmodels.NewBookingWorkTimeSlot()
endTime := 17:00:00.0000000
bookingWorkTimeSlot.SetEndTime(&endTime) 
startTime := 08:00:00.0000000
bookingWorkTimeSlot.SetStartTime(&startTime) 

timeSlots := []graphmodels.BookingWorkTimeSlotable {
	bookingWorkTimeSlot,
}
bookingWorkHours3.SetTimeSlots(timeSlots)
additionalData := map[string]interface{}{
	"day@odata.type" : "#microsoft.graph.dayOfWeek", 
	"timeSlots@odata.type" : "#Collection(microsoft.graph.bookingWorkTimeSlot)", 
}
bookingWorkHours3.SetAdditionalData(additionalData)
bookingWorkHours4 := graphmodels.NewBookingWorkHours()
day := graphmodels.FRIDAY_DAYOFWEEK 
bookingWorkHours4.SetDay(&day) 


bookingWorkTimeSlot := graphmodels.NewBookingWorkTimeSlot()
endTime := 17:00:00.0000000
bookingWorkTimeSlot.SetEndTime(&endTime) 
startTime := 08:00:00.0000000
bookingWorkTimeSlot.SetStartTime(&startTime) 

timeSlots := []graphmodels.BookingWorkTimeSlotable {
	bookingWorkTimeSlot,
}
bookingWorkHours4.SetTimeSlots(timeSlots)
additionalData := map[string]interface{}{
	"day@odata.type" : "#microsoft.graph.dayOfWeek", 
	"timeSlots@odata.type" : "#Collection(microsoft.graph.bookingWorkTimeSlot)", 
}
bookingWorkHours4.SetAdditionalData(additionalData)

workingHours := []graphmodels.BookingWorkHoursable {
	bookingWorkHours,
	bookingWorkHours1,
	bookingWorkHours2,
	bookingWorkHours3,
	bookingWorkHours4,
}
requestBody.SetWorkingHours(workingHours)
isEmailNotificationEnabled := false
requestBody.SetIsEmailNotificationEnabled(&isEmailNotificationEnabled) 
additionalData := map[string]interface{}{
	"role@odata.type" : "#microsoft.graph.bookingStaffRole", 
	"workingHours@odata.type" : "#Collection(microsoft.graph.bookingWorkHours)", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
staffMembers, err := graphClient.Solutions().BookingBusinesses().ByBookingBusinessId("bookingBusiness-id").StaffMembers().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BookingStaffMember bookingStaffMemberBase = new BookingStaffMember();
bookingStaffMemberBase.setOdataType("#microsoft.graph.bookingStaffMember");
bookingStaffMemberBase.setDisplayName("Dana Swope");
bookingStaffMemberBase.setEmailAddress("danas@contoso.com");
bookingStaffMemberBase.setRole(BookingStaffRole.ExternalGuest);
bookingStaffMemberBase.setTimeZone("America/Chicago");
bookingStaffMemberBase.setUseBusinessHours(true);
LinkedList<BookingWorkHours> workingHours = new LinkedList<BookingWorkHours>();
BookingWorkHours bookingWorkHours = new BookingWorkHours();
bookingWorkHours.setOdataType("#microsoft.graph.bookingWorkHours");
bookingWorkHours.setDay(DayOfWeek.Monday);
LinkedList<BookingWorkTimeSlot> timeSlots = new LinkedList<BookingWorkTimeSlot>();
BookingWorkTimeSlot bookingWorkTimeSlot = new BookingWorkTimeSlot();
bookingWorkTimeSlot.setOdataType("#microsoft.graph.bookingWorkTimeSlot");
LocalTime endTime = LocalTime.parse("17:00:00.0000000");
bookingWorkTimeSlot.setEndTime(endTime);
LocalTime startTime = LocalTime.parse("08:00:00.0000000");
bookingWorkTimeSlot.setStartTime(startTime);
timeSlots.add(bookingWorkTimeSlot);
bookingWorkHours.setTimeSlots(timeSlots);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("day@odata.type", "#microsoft.graph.dayOfWeek");
additionalData.put("timeSlots@odata.type", "#Collection(microsoft.graph.bookingWorkTimeSlot)");
bookingWorkHours.setAdditionalData(additionalData);
workingHours.add(bookingWorkHours);
BookingWorkHours bookingWorkHours1 = new BookingWorkHours();
bookingWorkHours1.setOdataType("#microsoft.graph.bookingWorkHours");
bookingWorkHours1.setDay(DayOfWeek.Tuesday);
LinkedList<BookingWorkTimeSlot> timeSlots1 = new LinkedList<BookingWorkTimeSlot>();
BookingWorkTimeSlot bookingWorkTimeSlot1 = new BookingWorkTimeSlot();
bookingWorkTimeSlot1.setOdataType("#microsoft.graph.bookingWorkTimeSlot");
LocalTime endTime1 = LocalTime.parse("17:00:00.0000000");
bookingWorkTimeSlot1.setEndTime(endTime1);
LocalTime startTime1 = LocalTime.parse("08:00:00.0000000");
bookingWorkTimeSlot1.setStartTime(startTime1);
timeSlots1.add(bookingWorkTimeSlot1);
bookingWorkHours1.setTimeSlots(timeSlots1);
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("day@odata.type", "#microsoft.graph.dayOfWeek");
additionalData1.put("timeSlots@odata.type", "#Collection(microsoft.graph.bookingWorkTimeSlot)");
bookingWorkHours1.setAdditionalData(additionalData1);
workingHours.add(bookingWorkHours1);
BookingWorkHours bookingWorkHours2 = new BookingWorkHours();
bookingWorkHours2.setOdataType("#microsoft.graph.bookingWorkHours");
bookingWorkHours2.setDay(DayOfWeek.Wednesday);
LinkedList<BookingWorkTimeSlot> timeSlots2 = new LinkedList<BookingWorkTimeSlot>();
BookingWorkTimeSlot bookingWorkTimeSlot2 = new BookingWorkTimeSlot();
bookingWorkTimeSlot2.setOdataType("#microsoft.graph.bookingWorkTimeSlot");
LocalTime endTime2 = LocalTime.parse("17:00:00.0000000");
bookingWorkTimeSlot2.setEndTime(endTime2);
LocalTime startTime2 = LocalTime.parse("08:00:00.0000000");
bookingWorkTimeSlot2.setStartTime(startTime2);
timeSlots2.add(bookingWorkTimeSlot2);
bookingWorkHours2.setTimeSlots(timeSlots2);
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
additionalData2.put("day@odata.type", "#microsoft.graph.dayOfWeek");
additionalData2.put("timeSlots@odata.type", "#Collection(microsoft.graph.bookingWorkTimeSlot)");
bookingWorkHours2.setAdditionalData(additionalData2);
workingHours.add(bookingWorkHours2);
BookingWorkHours bookingWorkHours3 = new BookingWorkHours();
bookingWorkHours3.setOdataType("#microsoft.graph.bookingWorkHours");
bookingWorkHours3.setDay(DayOfWeek.Thursday);
LinkedList<BookingWorkTimeSlot> timeSlots3 = new LinkedList<BookingWorkTimeSlot>();
BookingWorkTimeSlot bookingWorkTimeSlot3 = new BookingWorkTimeSlot();
bookingWorkTimeSlot3.setOdataType("#microsoft.graph.bookingWorkTimeSlot");
LocalTime endTime3 = LocalTime.parse("17:00:00.0000000");
bookingWorkTimeSlot3.setEndTime(endTime3);
LocalTime startTime3 = LocalTime.parse("08:00:00.0000000");
bookingWorkTimeSlot3.setStartTime(startTime3);
timeSlots3.add(bookingWorkTimeSlot3);
bookingWorkHours3.setTimeSlots(timeSlots3);
HashMap<String, Object> additionalData3 = new HashMap<String, Object>();
additionalData3.put("day@odata.type", "#microsoft.graph.dayOfWeek");
additionalData3.put("timeSlots@odata.type", "#Collection(microsoft.graph.bookingWorkTimeSlot)");
bookingWorkHours3.setAdditionalData(additionalData3);
workingHours.add(bookingWorkHours3);
BookingWorkHours bookingWorkHours4 = new BookingWorkHours();
bookingWorkHours4.setOdataType("#microsoft.graph.bookingWorkHours");
bookingWorkHours4.setDay(DayOfWeek.Friday);
LinkedList<BookingWorkTimeSlot> timeSlots4 = new LinkedList<BookingWorkTimeSlot>();
BookingWorkTimeSlot bookingWorkTimeSlot4 = new BookingWorkTimeSlot();
bookingWorkTimeSlot4.setOdataType("#microsoft.graph.bookingWorkTimeSlot");
LocalTime endTime4 = LocalTime.parse("17:00:00.0000000");
bookingWorkTimeSlot4.setEndTime(endTime4);
LocalTime startTime4 = LocalTime.parse("08:00:00.0000000");
bookingWorkTimeSlot4.setStartTime(startTime4);
timeSlots4.add(bookingWorkTimeSlot4);
bookingWorkHours4.setTimeSlots(timeSlots4);
HashMap<String, Object> additionalData4 = new HashMap<String, Object>();
additionalData4.put("day@odata.type", "#microsoft.graph.dayOfWeek");
additionalData4.put("timeSlots@odata.type", "#Collection(microsoft.graph.bookingWorkTimeSlot)");
bookingWorkHours4.setAdditionalData(additionalData4);
workingHours.add(bookingWorkHours4);
bookingStaffMemberBase.setWorkingHours(workingHours);
bookingStaffMemberBase.setIsEmailNotificationEnabled(false);
HashMap<String, Object> additionalData5 = new HashMap<String, Object>();
additionalData5.put("role@odata.type", "#microsoft.graph.bookingStaffRole");
additionalData5.put("workingHours@odata.type", "#Collection(microsoft.graph.bookingWorkHours)");
bookingStaffMemberBase.setAdditionalData(additionalData5);
BookingStaffMemberBase result = graphClient.solutions().bookingBusinesses().byBookingBusinessId("{bookingBusiness-id}").staffMembers().post(bookingStaffMemberBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const bookingStaffMemberBase = {
    '@odata.type':'#microsoft.graph.bookingStaffMember',
    displayName: 'Dana Swope',
    emailAddress: 'danas@contoso.com',
    'role@odata.type':'#microsoft.graph.bookingStaffRole',
    role: 'externalGuest',
    timeZone: 'America/Chicago',
    useBusinessHours: true,
    'workingHours@odata.type':'#Collection(microsoft.graph.bookingWorkHours)',
    workingHours: [
        {
            '@odata.type':'#microsoft.graph.bookingWorkHours',
            'day@odata.type':'#microsoft.graph.dayOfWeek',
            day: 'monday',
            'timeSlots@odata.type':'#Collection(microsoft.graph.bookingWorkTimeSlot)',
            timeSlots: [
                {
                    '@odata.type':'#microsoft.graph.bookingWorkTimeSlot',
                    endTime: '17:00:00.0000000',
                    startTime: '08:00:00.0000000'
                }
            ]
        },
        {
            '@odata.type':'#microsoft.graph.bookingWorkHours',
            'day@odata.type':'#microsoft.graph.dayOfWeek',
            day: 'tuesday',
            'timeSlots@odata.type':'#Collection(microsoft.graph.bookingWorkTimeSlot)',
            timeSlots: [
                {
                    '@odata.type':'#microsoft.graph.bookingWorkTimeSlot',
                    endTime: '17:00:00.0000000',
                    startTime: '08:00:00.0000000'
                }
            ]
        },
        {
            '@odata.type':'#microsoft.graph.bookingWorkHours',
            'day@odata.type':'#microsoft.graph.dayOfWeek',
            day: 'wednesday',
            'timeSlots@odata.type':'#Collection(microsoft.graph.bookingWorkTimeSlot)',
            timeSlots: [
                {
                    '@odata.type':'#microsoft.graph.bookingWorkTimeSlot',
                    endTime: '17:00:00.0000000',
                    startTime: '08:00:00.0000000'
                }
            ]
        },
        {
            '@odata.type':'#microsoft.graph.bookingWorkHours',
            'day@odata.type':'#microsoft.graph.dayOfWeek',
            day: 'thursday',
            'timeSlots@odata.type':'#Collection(microsoft.graph.bookingWorkTimeSlot)',
            timeSlots: [
                {
                    '@odata.type':'#microsoft.graph.bookingWorkTimeSlot',
                    endTime: '17:00:00.0000000',
                    startTime: '08:00:00.0000000'
                }
            ]
        },
        {
            '@odata.type':'#microsoft.graph.bookingWorkHours',
            'day@odata.type':'#microsoft.graph.dayOfWeek',
            day: 'friday',
            'timeSlots@odata.type':'#Collection(microsoft.graph.bookingWorkTimeSlot)',
            timeSlots: [
                {
                    '@odata.type':'#microsoft.graph.bookingWorkTimeSlot',
                    endTime: '17:00:00.0000000',
                    startTime: '08:00:00.0000000'
                }
            ]
        }
    ],
    isEmailNotificationEnabled: false
};

await client.api('/solutions/bookingBusinesses/{id}/staffMembers')
	.post(bookingStaffMemberBase);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\BookingStaffMember;
use Microsoft\Graph\Generated\Models\BookingStaffRole;
use Microsoft\Graph\Generated\Models\BookingWorkHours;
use Microsoft\Graph\Generated\Models\DayOfWeek;
use Microsoft\Graph\Generated\Models\BookingWorkTimeSlot;
use Microsoft\Kiota\Abstractions\Types\Time;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BookingStaffMember();
$requestBody->setOdataType('#microsoft.graph.bookingStaffMember');
$requestBody->setDisplayName('Dana Swope');
$requestBody->setEmailAddress('danas@contoso.com');
$requestBody->setRole(new BookingStaffRole('externalGuest'));
$requestBody->setTimeZone('America/Chicago');
$requestBody->setUseBusinessHours(true);
$workingHoursBookingWorkHours1 = new BookingWorkHours();
$workingHoursBookingWorkHours1->setOdataType('#microsoft.graph.bookingWorkHours');
$workingHoursBookingWorkHours1->setDay(new DayOfWeek('monday'));
$timeSlotsBookingWorkTimeSlot1 = new BookingWorkTimeSlot();
$timeSlotsBookingWorkTimeSlot1->setOdataType('#microsoft.graph.bookingWorkTimeSlot');
$timeSlotsBookingWorkTimeSlot1->setEndTime(new Time('17:00:00.0000000'));
$timeSlotsBookingWorkTimeSlot1->setStartTime(new Time('08:00:00.0000000'));
$timeSlotsArray []= $timeSlotsBookingWorkTimeSlot1;
$workingHoursBookingWorkHours1->setTimeSlots($timeSlotsArray);

$additionalData = [
'day@odata.type' => '#microsoft.graph.dayOfWeek',
'timeSlots@odata.type' => '#Collection(microsoft.graph.bookingWorkTimeSlot)',
];
$workingHoursBookingWorkHours1->setAdditionalData($additionalData);
$workingHoursArray []= $workingHoursBookingWorkHours1;
$workingHoursBookingWorkHours2 = new BookingWorkHours();
$workingHoursBookingWorkHours2->setOdataType('#microsoft.graph.bookingWorkHours');
$workingHoursBookingWorkHours2->setDay(new DayOfWeek('tuesday'));
$timeSlotsBookingWorkTimeSlot1 = new BookingWorkTimeSlot();
$timeSlotsBookingWorkTimeSlot1->setOdataType('#microsoft.graph.bookingWorkTimeSlot');
$timeSlotsBookingWorkTimeSlot1->setEndTime(new Time('17:00:00.0000000'));
$timeSlotsBookingWorkTimeSlot1->setStartTime(new Time('08:00:00.0000000'));
$timeSlotsArray []= $timeSlotsBookingWorkTimeSlot1;
$workingHoursBookingWorkHours2->setTimeSlots($timeSlotsArray);

$additionalData = [
'day@odata.type' => '#microsoft.graph.dayOfWeek',
'timeSlots@odata.type' => '#Collection(microsoft.graph.bookingWorkTimeSlot)',
];
$workingHoursBookingWorkHours2->setAdditionalData($additionalData);
$workingHoursArray []= $workingHoursBookingWorkHours2;
$workingHoursBookingWorkHours3 = new BookingWorkHours();
$workingHoursBookingWorkHours3->setOdataType('#microsoft.graph.bookingWorkHours');
$workingHoursBookingWorkHours3->setDay(new DayOfWeek('wednesday'));
$timeSlotsBookingWorkTimeSlot1 = new BookingWorkTimeSlot();
$timeSlotsBookingWorkTimeSlot1->setOdataType('#microsoft.graph.bookingWorkTimeSlot');
$timeSlotsBookingWorkTimeSlot1->setEndTime(new Time('17:00:00.0000000'));
$timeSlotsBookingWorkTimeSlot1->setStartTime(new Time('08:00:00.0000000'));
$timeSlotsArray []= $timeSlotsBookingWorkTimeSlot1;
$workingHoursBookingWorkHours3->setTimeSlots($timeSlotsArray);

$additionalData = [
'day@odata.type' => '#microsoft.graph.dayOfWeek',
'timeSlots@odata.type' => '#Collection(microsoft.graph.bookingWorkTimeSlot)',
];
$workingHoursBookingWorkHours3->setAdditionalData($additionalData);
$workingHoursArray []= $workingHoursBookingWorkHours3;
$workingHoursBookingWorkHours4 = new BookingWorkHours();
$workingHoursBookingWorkHours4->setOdataType('#microsoft.graph.bookingWorkHours');
$workingHoursBookingWorkHours4->setDay(new DayOfWeek('thursday'));
$timeSlotsBookingWorkTimeSlot1 = new BookingWorkTimeSlot();
$timeSlotsBookingWorkTimeSlot1->setOdataType('#microsoft.graph.bookingWorkTimeSlot');
$timeSlotsBookingWorkTimeSlot1->setEndTime(new Time('17:00:00.0000000'));
$timeSlotsBookingWorkTimeSlot1->setStartTime(new Time('08:00:00.0000000'));
$timeSlotsArray []= $timeSlotsBookingWorkTimeSlot1;
$workingHoursBookingWorkHours4->setTimeSlots($timeSlotsArray);

$additionalData = [
'day@odata.type' => '#microsoft.graph.dayOfWeek',
'timeSlots@odata.type' => '#Collection(microsoft.graph.bookingWorkTimeSlot)',
];
$workingHoursBookingWorkHours4->setAdditionalData($additionalData);
$workingHoursArray []= $workingHoursBookingWorkHours4;
$workingHoursBookingWorkHours5 = new BookingWorkHours();
$workingHoursBookingWorkHours5->setOdataType('#microsoft.graph.bookingWorkHours');
$workingHoursBookingWorkHours5->setDay(new DayOfWeek('friday'));
$timeSlotsBookingWorkTimeSlot1 = new BookingWorkTimeSlot();
$timeSlotsBookingWorkTimeSlot1->setOdataType('#microsoft.graph.bookingWorkTimeSlot');
$timeSlotsBookingWorkTimeSlot1->setEndTime(new Time('17:00:00.0000000'));
$timeSlotsBookingWorkTimeSlot1->setStartTime(new Time('08:00:00.0000000'));
$timeSlotsArray []= $timeSlotsBookingWorkTimeSlot1;
$workingHoursBookingWorkHours5->setTimeSlots($timeSlotsArray);

$additionalData = [
'day@odata.type' => '#microsoft.graph.dayOfWeek',
'timeSlots@odata.type' => '#Collection(microsoft.graph.bookingWorkTimeSlot)',
];
$workingHoursBookingWorkHours5->setAdditionalData($additionalData);
$workingHoursArray []= $workingHoursBookingWorkHours5;
$requestBody->setWorkingHours($workingHoursArray);

$requestBody->setIsEmailNotificationEnabled(false);
$additionalData = [
'role@odata.type' => '#microsoft.graph.bookingStaffRole',
'workingHours@odata.type' => '#Collection(microsoft.graph.bookingWorkHours)',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->solutions()->bookingBusinesses()->byBookingBusinessId('bookingBusiness-id')->staffMembers()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	"@odata.type" = "#microsoft.graph.bookingStaffMember"
	displayName = "Dana Swope"
	emailAddress = "danas@contoso.com"
	"role@odata.type" = "#microsoft.graph.bookingStaffRole"
	role = "externalGuest"
	timeZone = "America/Chicago"
	useBusinessHours = $true
	"workingHours@odata.type" = "#Collection(microsoft.graph.bookingWorkHours)"
	workingHours = @(
		@{
			"@odata.type" = "#microsoft.graph.bookingWorkHours"
			"day@odata.type" = "#microsoft.graph.dayOfWeek"
			day = "monday"
			"timeSlots@odata.type" = "#Collection(microsoft.graph.bookingWorkTimeSlot)"
			timeSlots = @(
				@{
					"@odata.type" = "#microsoft.graph.bookingWorkTimeSlot"
					endTime = "17:00:00.0000000"
					startTime = "08:00:00.0000000"
				}
			)
		}
		@{
			"@odata.type" = "#microsoft.graph.bookingWorkHours"
			"day@odata.type" = "#microsoft.graph.dayOfWeek"
			day = "tuesday"
			"timeSlots@odata.type" = "#Collection(microsoft.graph.bookingWorkTimeSlot)"
			timeSlots = @(
				@{
					"@odata.type" = "#microsoft.graph.bookingWorkTimeSlot"
					endTime = "17:00:00.0000000"
					startTime = "08:00:00.0000000"
				}
			)
		}
		@{
			"@odata.type" = "#microsoft.graph.bookingWorkHours"
			"day@odata.type" = "#microsoft.graph.dayOfWeek"
			day = "wednesday"
			"timeSlots@odata.type" = "#Collection(microsoft.graph.bookingWorkTimeSlot)"
			timeSlots = @(
				@{
					"@odata.type" = "#microsoft.graph.bookingWorkTimeSlot"
					endTime = "17:00:00.0000000"
					startTime = "08:00:00.0000000"
				}
			)
		}
		@{
			"@odata.type" = "#microsoft.graph.bookingWorkHours"
			"day@odata.type" = "#microsoft.graph.dayOfWeek"
			day = "thursday"
			"timeSlots@odata.type" = "#Collection(microsoft.graph.bookingWorkTimeSlot)"
			timeSlots = @(
				@{
					"@odata.type" = "#microsoft.graph.bookingWorkTimeSlot"
					endTime = "17:00:00.0000000"
					startTime = "08:00:00.0000000"
				}
			)
		}
		@{
			"@odata.type" = "#microsoft.graph.bookingWorkHours"
			"day@odata.type" = "#microsoft.graph.dayOfWeek"
			day = "friday"
			"timeSlots@odata.type" = "#Collection(microsoft.graph.bookingWorkTimeSlot)"
			timeSlots = @(
				@{
					"@odata.type" = "#microsoft.graph.bookingWorkTimeSlot"
					endTime = "17:00:00.0000000"
					startTime = "08:00:00.0000000"
				}
			)
		}
	)
	isEmailNotificationEnabled = $false
}

New-MgBookingBusinessStaffMember -BookingBusinessId $bookingBusinessId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.booking_staff_member import BookingStaffMember
from msgraph.generated.models.booking_staff_role import BookingStaffRole
from msgraph.generated.models.booking_work_hours import BookingWorkHours
from msgraph.generated.models.day_of_week import DayOfWeek
from msgraph.generated.models.booking_work_time_slot import BookingWorkTimeSlot
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BookingStaffMember(
	odata_type = "#microsoft.graph.bookingStaffMember",
	display_name = "Dana Swope",
	email_address = "danas@contoso.com",
	role = BookingStaffRole.ExternalGuest,
	time_zone = "America/Chicago",
	use_business_hours = True,
	working_hours = [
		BookingWorkHours(
			odata_type = "#microsoft.graph.bookingWorkHours",
			day = DayOfWeek.Monday,
			time_slots = [
				BookingWorkTimeSlot(
					odata_type = "#microsoft.graph.bookingWorkTimeSlot",
					end_time = "17:00:00.0000000",
					start_time = "08:00:00.0000000",
				),
			],
			additional_data = {
					"day@odata_type" : "#microsoft.graph.dayOfWeek",
					"time_slots@odata_type" : "#Collection(microsoft.graph.bookingWorkTimeSlot)",
			}
		),
		BookingWorkHours(
			odata_type = "#microsoft.graph.bookingWorkHours",
			day = DayOfWeek.Tuesday,
			time_slots = [
				BookingWorkTimeSlot(
					odata_type = "#microsoft.graph.bookingWorkTimeSlot",
					end_time = "17:00:00.0000000",
					start_time = "08:00:00.0000000",
				),
			],
			additional_data = {
					"day@odata_type" : "#microsoft.graph.dayOfWeek",
					"time_slots@odata_type" : "#Collection(microsoft.graph.bookingWorkTimeSlot)",
			}
		),
		BookingWorkHours(
			odata_type = "#microsoft.graph.bookingWorkHours",
			day = DayOfWeek.Wednesday,
			time_slots = [
				BookingWorkTimeSlot(
					odata_type = "#microsoft.graph.bookingWorkTimeSlot",
					end_time = "17:00:00.0000000",
					start_time = "08:00:00.0000000",
				),
			],
			additional_data = {
					"day@odata_type" : "#microsoft.graph.dayOfWeek",
					"time_slots@odata_type" : "#Collection(microsoft.graph.bookingWorkTimeSlot)",
			}
		),
		BookingWorkHours(
			odata_type = "#microsoft.graph.bookingWorkHours",
			day = DayOfWeek.Thursday,
			time_slots = [
				BookingWorkTimeSlot(
					odata_type = "#microsoft.graph.bookingWorkTimeSlot",
					end_time = "17:00:00.0000000",
					start_time = "08:00:00.0000000",
				),
			],
			additional_data = {
					"day@odata_type" : "#microsoft.graph.dayOfWeek",
					"time_slots@odata_type" : "#Collection(microsoft.graph.bookingWorkTimeSlot)",
			}
		),
		BookingWorkHours(
			odata_type = "#microsoft.graph.bookingWorkHours",
			day = DayOfWeek.Friday,
			time_slots = [
				BookingWorkTimeSlot(
					odata_type = "#microsoft.graph.bookingWorkTimeSlot",
					end_time = "17:00:00.0000000",
					start_time = "08:00:00.0000000",
				),
			],
			additional_data = {
					"day@odata_type" : "#microsoft.graph.dayOfWeek",
					"time_slots@odata_type" : "#Collection(microsoft.graph.bookingWorkTimeSlot)",
			}
		),
	],
	is_email_notification_enabled = False,
	additional_data = {
			"role@odata_type" : "#microsoft.graph.bookingStaffRole",
			"working_hours@odata_type" : "#Collection(microsoft.graph.bookingWorkHours)",
	}
)

result = await graph_client.solutions.booking_businesses.by_booking_business_id('bookingBusiness-id').staff_members.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.type":"#microsoft.graph.bookingStaffMember",
    "@odata.context":"https://graph.microsoft.com/v1.0/solutions/$metadata#bookingBusinesses('Contosolunchdelivery%40contoso.com')/staffMembers/$entity",
    "id":"8ee1c803-a1fa-406d-8259-7ab53233f148",
    "displayName":"Dana Swope",
    "emailAddress":"danas@contoso.com",
    "availabilityIsAffectedByPersonalCalendar":false,
    "role":"externalGuest",
    "timeZone":"America/Chicago",
    "useBusinessHours":true,
    "workingHours":[
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
        }
    ],
    "isEmailNotificationEnabled": false
}
```
