<!-- Source: https://learn.microsoft.com/en-us/graph/api/shiftpreferences-put?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update shiftPreferences

Namespace: microsoft.graph

Update the properties and relationships of a [shiftPreferences](https://learn.microsoft.com/en-us/graph/api/resources/shiftpreferences?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User.ReadWrite.All | AgentIdUser.ReadWrite.All, AgentIdUser.ReadWrite.IdentityParentedBy |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | UserShiftPreferences.ReadWrite.All | Not available. |

> **Note**: This API supports admin permissions. Users with admin roles can access groups that they are not a member of.

## HTTP request

```http
PATCH /users/{userId}/settings/shiftPreferences
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

In the request body, supply a JSON representation of a [shiftPreferences](https://learn.microsoft.com/en-us/graph/api/resources/shiftpreferences?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `204 NO CONTENT` response code.

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
PATCH https://graph.microsoft.com/v1.0/users/871dbd5c-3a6a-4392-bfe1-042452793a50/settings/shiftPreferences
Content-type: application/json

{
    "id": "SHPR_eeab4fb1-20e5-48ca-ad9b-98119d94bee7",
    "@odata.etag": "1a371e53-f0a6-4327-a1ee-e3c56e4b38aa",
    "availability": [
        {
            "recurrence": {
                "pattern": {
                    "type": "Weekly",
                    "daysOfWeek": ["Monday", "Wednesday", "Friday"],
                    "interval": 1
                },
                "range": {
                    "type": "noEnd"
                }
            },
            "timeZone": "Pacific Standard Time",
            "timeSlots": null
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ShiftPreferences
{
	Id = "SHPR_eeab4fb1-20e5-48ca-ad9b-98119d94bee7",
	Availability = new List<ShiftAvailability>
	{
		new ShiftAvailability
		{
			Recurrence = new PatternedRecurrence
			{
				Pattern = new RecurrencePattern
				{
					Type = RecurrencePatternType.Weekly,
					DaysOfWeek = new List<DayOfWeekObject?>
					{
						DayOfWeekObject.Monday,
						DayOfWeekObject.Wednesday,
						DayOfWeekObject.Friday,
					},
					Interval = 1,
				},
				Range = new RecurrenceRange
				{
					Type = RecurrenceRangeType.NoEnd,
				},
			},
			TimeZone = "Pacific Standard Time",
			TimeSlots = null,
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"@odata.etag" , "1a371e53-f0a6-4327-a1ee-e3c56e4b38aa"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Settings.ShiftPreferences.PatchAsync(requestBody);
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

requestBody := graphmodels.NewShiftPreferences()
id := "SHPR_eeab4fb1-20e5-48ca-ad9b-98119d94bee7"
requestBody.SetId(&id) 


shiftAvailability := graphmodels.NewShiftAvailability()
recurrence := graphmodels.NewPatternedRecurrence()
pattern := graphmodels.NewRecurrencePattern()
type := graphmodels.WEEKLY_RECURRENCEPATTERNTYPE 
pattern.SetType(&type) 
daysOfWeek := []graphmodels.DayOfWeekable {
	dayOfWeek := graphmodels.MONDAY_DAYOFWEEK 
	pattern.SetDayOfWeek(&dayOfWeek) 
	dayOfWeek := graphmodels.WEDNESDAY_DAYOFWEEK 
	pattern.SetDayOfWeek(&dayOfWeek) 
	dayOfWeek := graphmodels.FRIDAY_DAYOFWEEK 
	pattern.SetDayOfWeek(&dayOfWeek)
}
pattern.SetDaysOfWeek(daysOfWeek)
interval := int32(1)
pattern.SetInterval(&interval) 
recurrence.SetPattern(pattern)
range := graphmodels.NewRecurrenceRange()
type := graphmodels.NOEND_RECURRENCERANGETYPE 
range.SetType(&type) 
recurrence.SetRange(range)
shiftAvailability.SetRecurrence(recurrence)
timeZone := "Pacific Standard Time"
shiftAvailability.SetTimeZone(&timeZone) 
timeSlots := null
shiftAvailability.SetTimeSlots(&timeSlots) 

availability := []graphmodels.ShiftAvailabilityable {
	shiftAvailability,
}
requestBody.SetAvailability(availability)
additionalData := map[string]interface{}{
	"@odata.etag" : "1a371e53-f0a6-4327-a1ee-e3c56e4b38aa", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
shiftPreferences, err := graphClient.Users().ByUserId("user-id").Settings().ShiftPreferences().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ShiftPreferences shiftPreferences = new ShiftPreferences();
shiftPreferences.setId("SHPR_eeab4fb1-20e5-48ca-ad9b-98119d94bee7");
LinkedList<ShiftAvailability> availability = new LinkedList<ShiftAvailability>();
ShiftAvailability shiftAvailability = new ShiftAvailability();
PatternedRecurrence recurrence = new PatternedRecurrence();
RecurrencePattern pattern = new RecurrencePattern();
pattern.setType(RecurrencePatternType.Weekly);
LinkedList<DayOfWeek> daysOfWeek = new LinkedList<DayOfWeek>();
daysOfWeek.add(DayOfWeek.Monday);
daysOfWeek.add(DayOfWeek.Wednesday);
daysOfWeek.add(DayOfWeek.Friday);
pattern.setDaysOfWeek(daysOfWeek);
pattern.setInterval(1);
recurrence.setPattern(pattern);
RecurrenceRange range = new RecurrenceRange();
range.setType(RecurrenceRangeType.NoEnd);
recurrence.setRange(range);
shiftAvailability.setRecurrence(recurrence);
shiftAvailability.setTimeZone("Pacific Standard Time");
shiftAvailability.setTimeSlots(null);
availability.add(shiftAvailability);
shiftPreferences.setAvailability(availability);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@odata.etag", "1a371e53-f0a6-4327-a1ee-e3c56e4b38aa");
shiftPreferences.setAdditionalData(additionalData);
ShiftPreferences result = graphClient.users().byUserId("{user-id}").settings().shiftPreferences().patch(shiftPreferences);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const shiftPreferences = {
    id: 'SHPR_eeab4fb1-20e5-48ca-ad9b-98119d94bee7',
    '@odata.etag': '1a371e53-f0a6-4327-a1ee-e3c56e4b38aa',
    availability: [
        {
            recurrence: {
                pattern: {
                    type: 'Weekly',
                    daysOfWeek: ['Monday', 'Wednesday', 'Friday'],
                    interval: 1
                },
                range: {
                    type: 'noEnd'
                }
            },
            timeZone: 'Pacific Standard Time',
            timeSlots: null
        }
    ]
};

await client.api('/users/871dbd5c-3a6a-4392-bfe1-042452793a50/settings/shiftPreferences')
	.update(shiftPreferences);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ShiftPreferences;
use Microsoft\Graph\Generated\Models\ShiftAvailability;
use Microsoft\Graph\Generated\Models\PatternedRecurrence;
use Microsoft\Graph\Generated\Models\RecurrencePattern;
use Microsoft\Graph\Generated\Models\RecurrencePatternType;
use Microsoft\Graph\Generated\Models\DayOfWeek;
use Microsoft\Graph\Generated\Models\RecurrenceRange;
use Microsoft\Graph\Generated\Models\RecurrenceRangeType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ShiftPreferences();
$requestBody->setId('SHPR_eeab4fb1-20e5-48ca-ad9b-98119d94bee7');
$availabilityShiftAvailability1 = new ShiftAvailability();
$availabilityShiftAvailability1Recurrence = new PatternedRecurrence();
$availabilityShiftAvailability1RecurrencePattern = new RecurrencePattern();
$availabilityShiftAvailability1RecurrencePattern->setType(new RecurrencePatternType('weekly'));
$availabilityShiftAvailability1RecurrencePattern->setDaysOfWeek([new DayOfWeek('monday'),new DayOfWeek('wednesday'),new DayOfWeek('friday'),	]);
$availabilityShiftAvailability1RecurrencePattern->setInterval(1);
$availabilityShiftAvailability1Recurrence->setPattern($availabilityShiftAvailability1RecurrencePattern);
$availabilityShiftAvailability1RecurrenceRange = new RecurrenceRange();
$availabilityShiftAvailability1RecurrenceRange->setType(new RecurrenceRangeType('noEnd'));
$availabilityShiftAvailability1Recurrence->setRange($availabilityShiftAvailability1RecurrenceRange);
$availabilityShiftAvailability1->setRecurrence($availabilityShiftAvailability1Recurrence);
$availabilityShiftAvailability1->setTimeZone('Pacific Standard Time');
$availabilityShiftAvailability1->setTimeSlots(null);
$availabilityArray []= $availabilityShiftAvailability1;
$requestBody->setAvailability($availabilityArray);

$additionalData = [
'@odata.etag' => '1a371e53-f0a6-4327-a1ee-e3c56e4b38aa',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->users()->byUserId('user-id')->settings()->shiftPreferences()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	id = "SHPR_eeab4fb1-20e5-48ca-ad9b-98119d94bee7"
	"@odata.etag" = "1a371e53-f0a6-4327-a1ee-e3c56e4b38aa"
	availability = @(
		@{
			recurrence = @{
				pattern = @{
					type = "Weekly"
					daysOfWeek = @(
					"Monday"
				"Wednesday"
			"Friday"
		)
		interval = 1
	}
	range = @{
		type = "noEnd"
	}
}
timeZone = "Pacific Standard Time"
timeSlots = $null
}
)
}

Update-MgUserSettingShiftPreference -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.shift_preferences import ShiftPreferences
from msgraph.generated.models.shift_availability import ShiftAvailability
from msgraph.generated.models.patterned_recurrence import PatternedRecurrence
from msgraph.generated.models.recurrence_pattern import RecurrencePattern
from msgraph.generated.models.recurrence_pattern_type import RecurrencePatternType
from msgraph.generated.models.day_of_week import DayOfWeek
from msgraph.generated.models.recurrence_range import RecurrenceRange
from msgraph.generated.models.recurrence_range_type import RecurrenceRangeType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ShiftPreferences(
	id = "SHPR_eeab4fb1-20e5-48ca-ad9b-98119d94bee7",
	availability = [
		ShiftAvailability(
			recurrence = PatternedRecurrence(
				pattern = RecurrencePattern(
					type = RecurrencePatternType.Weekly,
					days_of_week = [
						DayOfWeek.Monday,
						DayOfWeek.Wednesday,
						DayOfWeek.Friday,
					],
					interval = 1,
				),
				range = RecurrenceRange(
					type = RecurrenceRangeType.NoEnd,
				),
			),
			time_zone = "Pacific Standard Time",
			time_slots = None,
		),
	],
	additional_data = {
			"@odata_etag" : "1a371e53-f0a6-4327-a1ee-e3c56e4b38aa",
	}
)

result = await graph_client.users.by_user_id('user-id').settings.shift_preferences.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 NO CONTENT
```
