<!-- Source: https://learn.microsoft.com/en-us/graph/api/user-update-mailboxsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update user mailbox settings

Namespace: microsoft.graph

Enable, configure, or disable one or more of the following settings as part of a user's [mailboxSettings](https://learn.microsoft.com/en-us/graph/api/resources/mailboxsettings?view=graph-rest-1.0):

- [automatic replies](https://learn.microsoft.com/en-us/graph/api/resources/automaticrepliessetting?view=graph-rest-1.0) \(notify people automatically upon receipt of their email\)
- dateFormat
- delegateMeetingMessageDeliveryOptions
- [locale](https://learn.microsoft.com/en-us/graph/api/resources/localeinfo?view=graph-rest-1.0) \(language and country/region\)
- timeFormat
- time zone
- [working hours](https://learn.microsoft.com/en-us/graph/api/resources/workinghours?view=graph-rest-1.0)

When updating the preferred date or time format for a user, specify it in respectively, the [short date](https://learn.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings#ShortDate) or [short time](https://learn.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings#ShortTime) format.

When updating the preferred time zone for a user, specify it in the Windows or [Internet Assigned Numbers Authority \(IANA\) time zone](https://www.iana.org/time-zones) \(also known as Olson time zone\) format. You can also further customize the time zone as shown in [example 2](#example-2) below.

Tip

You cannot create or delete any mailbox settings.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | MailboxSettings.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | MailboxSettings.ReadWrite | Not available. |
| Application | MailboxSettings.ReadWrite | Not available. |

## HTTP request

```http
PATCH /me/mailboxSettings
PATCH /users/{id|userPrincipalName}/mailboxSettings
```

## Optional query parameters

This method supports the [OData Query Parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply the values for the relevant properties that should be updated. Existing properties that are not included in the request body will maintain their previous values or be recalculated based on changes to other property values. For best performance you shouldn't include existing values that haven't changed. The following are the writable/updatable properties:

| Property | Type | Description |
| :--- | :--- | :--- |
| automaticRepliesSetting | [automaticRepliesSetting](https://learn.microsoft.com/en-us/graph/api/resources/automaticrepliessetting?view=graph-rest-1.0) | Configuration settings to automatically notify the sender of an incoming email with a message from the signed-in user. You can set such notifications for only a future date range. |
| dateFormat | string | The date format for the user's mailbox. |
| delegateMeetingMessageDeliveryOptions | delegateMeetingMessageDeliveryOptions | If the user has a calendar delegate, this specifies whether the delegate, mailbox owner, or both receive meeting messages and meeting responses. The possible values are: `sendToDelegateAndInformationToPrincipal`, `sendToDelegateAndPrincipal`, `sendToDelegateOnly`. |
| language | [localeInfo](https://learn.microsoft.com/en-us/graph/api/resources/localeinfo?view=graph-rest-1.0) | The locale information for the user, including the preferred language and country/region. |
| timeFormat | string | The time format for the user's mailbox. |
| timeZone | string | The default time zone for the user's mailbox. |
| workingHours | [workingHours](https://learn.microsoft.com/en-us/graph/api/resources/workinghours?view=graph-rest-1.0) | The hours, days of a week, and time zone that the user works. |

## Response

If successful, this method returns a `200 OK` response code and the updated properties of a [mailboxSettings](https://learn.microsoft.com/en-us/graph/api/resources/mailboxsettings?view=graph-rest-1.0) object in the response body.

## Errors

Setting working hours with inappropriate values may return the following errors.

| Scenario | HTTP status code | Error code | Error message |
| :--- | :--- | :--- | :--- |
| Invalid **startTime** or **endTime** | 400 | RequestBodyRead | Cannot convert the literal '08' to the expected type 'Edm.TimeOfDay'. |
| Start time is greater than end time | 400 | ErrorInvalidTimeSettings | Start Time should occur before End Time. |
| Invalid day in **daysOfWeek** | 400 | InvalidArguments | Requested value 'RandomDay' was not found. |
| Invalid **timeZone** | 400 | InvalidTimeZone | Time Zone settings provided are invalid. |

## Examples

### Example 1

#### Request

The first example enables automatic replies for a date range, by setting the following properties of the **automaticRepliesSetting** property: **status**, **scheduledStartDateTime** and **scheduledEndDateTime**.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/me/mailboxSettings
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/mailboxSettings",
    "automaticRepliesSetting": {
        "status": "Scheduled",
        "scheduledStartDateTime": {
          "dateTime": "2016-03-20T18:00:00.0000000",
          "timeZone": "UTC"
        },
        "scheduledEndDateTime": {
          "dateTime": "2016-03-28T18:00:00.0000000",
          "timeZone": "UTC"
        }
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new MailboxSettings
{
	AutomaticRepliesSetting = new AutomaticRepliesSetting
	{
		Status = AutomaticRepliesStatus.Scheduled,
		ScheduledStartDateTime = new DateTimeTimeZone
		{
			DateTime = "2016-03-20T18:00:00.0000000",
			TimeZone = "UTC",
		},
		ScheduledEndDateTime = new DateTimeTimeZone
		{
			DateTime = "2016-03-28T18:00:00.0000000",
			TimeZone = "UTC",
		},
	},
	AdditionalData = new Dictionary<string, object>
	{
		{
			"@odata.context" , "https://graph.microsoft.com/v1.0/$metadata#Me/mailboxSettings"
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.MailboxSettings.PatchAsync(requestBody);
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

requestBody := graphmodels.NewMailboxSettings()
automaticRepliesSetting := graphmodels.NewAutomaticRepliesSetting()
status := graphmodels.SCHEDULED_AUTOMATICREPLIESSTATUS 
automaticRepliesSetting.SetStatus(&status) 
scheduledStartDateTime := graphmodels.NewDateTimeTimeZone()
dateTime := "2016-03-20T18:00:00.0000000"
scheduledStartDateTime.SetDateTime(&dateTime) 
timeZone := "UTC"
scheduledStartDateTime.SetTimeZone(&timeZone) 
automaticRepliesSetting.SetScheduledStartDateTime(scheduledStartDateTime)
scheduledEndDateTime := graphmodels.NewDateTimeTimeZone()
dateTime := "2016-03-28T18:00:00.0000000"
scheduledEndDateTime.SetDateTime(&dateTime) 
timeZone := "UTC"
scheduledEndDateTime.SetTimeZone(&timeZone) 
automaticRepliesSetting.SetScheduledEndDateTime(scheduledEndDateTime)
requestBody.SetAutomaticRepliesSetting(automaticRepliesSetting)
additionalData := map[string]interface{}{
	"@odata.context" : "https://graph.microsoft.com/v1.0/$metadata#Me/mailboxSettings", 
}
requestBody.SetAdditionalData(additionalData)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
mailboxSettings, err := graphClient.Me().MailboxSettings().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MailboxSettings mailboxSettings = new MailboxSettings();
AutomaticRepliesSetting automaticRepliesSetting = new AutomaticRepliesSetting();
automaticRepliesSetting.setStatus(AutomaticRepliesStatus.Scheduled);
DateTimeTimeZone scheduledStartDateTime = new DateTimeTimeZone();
scheduledStartDateTime.setDateTime("2016-03-20T18:00:00.0000000");
scheduledStartDateTime.setTimeZone("UTC");
automaticRepliesSetting.setScheduledStartDateTime(scheduledStartDateTime);
DateTimeTimeZone scheduledEndDateTime = new DateTimeTimeZone();
scheduledEndDateTime.setDateTime("2016-03-28T18:00:00.0000000");
scheduledEndDateTime.setTimeZone("UTC");
automaticRepliesSetting.setScheduledEndDateTime(scheduledEndDateTime);
mailboxSettings.setAutomaticRepliesSetting(automaticRepliesSetting);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("@odata.context", "https://graph.microsoft.com/v1.0/$metadata#Me/mailboxSettings");
mailboxSettings.setAdditionalData(additionalData);
MailboxSettings result = graphClient.me().mailboxSettings().patch(mailboxSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const mailboxSettings = {
    '@odata.context': 'https://graph.microsoft.com/v1.0/$metadata#Me/mailboxSettings',
    automaticRepliesSetting: {
        status: 'Scheduled',
        scheduledStartDateTime: {
          dateTime: '2016-03-20T18:00:00.0000000',
          timeZone: 'UTC'
        },
        scheduledEndDateTime: {
          dateTime: '2016-03-28T18:00:00.0000000',
          timeZone: 'UTC'
        }
    }
};

await client.api('/me/mailboxSettings')
	.update(mailboxSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\MailboxSettings;
use Microsoft\Graph\Generated\Models\AutomaticRepliesSetting;
use Microsoft\Graph\Generated\Models\AutomaticRepliesStatus;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MailboxSettings();
$automaticRepliesSetting = new AutomaticRepliesSetting();
$automaticRepliesSetting->setStatus(new AutomaticRepliesStatus('scheduled'));
$automaticRepliesSettingScheduledStartDateTime = new DateTimeTimeZone();
$automaticRepliesSettingScheduledStartDateTime->setDateTime('2016-03-20T18:00:00.0000000');
$automaticRepliesSettingScheduledStartDateTime->setTimeZone('UTC');
$automaticRepliesSetting->setScheduledStartDateTime($automaticRepliesSettingScheduledStartDateTime);
$automaticRepliesSettingScheduledEndDateTime = new DateTimeTimeZone();
$automaticRepliesSettingScheduledEndDateTime->setDateTime('2016-03-28T18:00:00.0000000');
$automaticRepliesSettingScheduledEndDateTime->setTimeZone('UTC');
$automaticRepliesSetting->setScheduledEndDateTime($automaticRepliesSettingScheduledEndDateTime);
$requestBody->setAutomaticRepliesSetting($automaticRepliesSetting);
$additionalData = [
	'@odata.context' => 'https://graph.microsoft.com/v1.0/$metadata#Me/mailboxSettings',
];
$requestBody->setAdditionalData($additionalData);

$result = $graphServiceClient->me()->mailboxSettings()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	"@odata.context" = "https://graph.microsoft.com/v1.0/$metadata#Me/mailboxSettings"
	automaticRepliesSetting = @{
		status = "Scheduled"
		scheduledStartDateTime = @{
			dateTime = "2016-03-20T18:00:00.0000000"
			timeZone = "UTC"
		}
		scheduledEndDateTime = @{
			dateTime = "2016-03-28T18:00:00.0000000"
			timeZone = "UTC"
		}
	}
}

# A UPN can also be used as -UserId.
Update-MgUserMailboxSetting -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.mailbox_settings import MailboxSettings
from msgraph.generated.models.automatic_replies_setting import AutomaticRepliesSetting
from msgraph.generated.models.automatic_replies_status import AutomaticRepliesStatus
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MailboxSettings(
	automatic_replies_setting = AutomaticRepliesSetting(
		status = AutomaticRepliesStatus.Scheduled,
		scheduled_start_date_time = DateTimeTimeZone(
			date_time = "2016-03-20T18:00:00.0000000",
			time_zone = "UTC",
		),
		scheduled_end_date_time = DateTimeTimeZone(
			date_time = "2016-03-28T18:00:00.0000000",
			time_zone = "UTC",
		),
	),
	additional_data = {
			"@odata_context" : "https://graph.microsoft.com/v1.0/$metadata#Me/mailboxSettings",
	}
)

result = await graph_client.me.mailbox_settings.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The response includes the updated settings for automatic replies.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/mailboxSettings",
    "automaticRepliesSetting": {
        "status": "scheduled",
        "externalAudience": "all",
        "scheduledStartDateTime": {
            "dateTime": "2016-03-20T02:00:00.0000000",
            "timeZone": "UTC"
        },
        "scheduledEndDateTime": {
            "dateTime": "2016-03-28T02:00:00.0000000",
            "timeZone": "UTC"
        },
    "internalReplyMessage": "<html>\n<body>\n<p>I'm at our company's worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n",
    "externalReplyMessage": "<html>\n<body>\n<p>I'm at the Contoso worldwide reunion and will respond to your message as soon as I return.<br>\n</p></body>\n</html>\n"
    }
}
```

### Example 2

#### Request

The second example customizes the time zone for the working hours of the signed-in user, by setting the **timeZone** property to a [custom time zone](https://learn.microsoft.com/en-us/graph/api/resources/customtimezone?view=graph-rest-1.0).

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/me/mailboxSettings
Content-Type: application/json

{
  "workingHours": {
      "endTime" : "18:30:00.0000000", 
      "daysOfWeek": [ 
          "Monday", 
          "Tuesday", 
          "Wednesday", 
          "Thursday", 
          "Friday", 
          "Saturday" 
      ], 
      "timeZone" : { 
         "@odata.type": "#microsoft.graph.customTimeZone", 
         "bias":-300, 
         "name": "Customized Time Zone",
         "standardOffset":{   
           "time":"02:00:00.0000000", 
           "dayOccurrence":2, 
           "dayOfWeek":"Sunday", 
           "month":10, 
           "year":0 
         }, 
         "daylightOffset":{   
           "daylightBias":100, 
           "time":"02:00:00.0000000", 
           "dayOccurrence":4, 
           "dayOfWeek":"Sunday", 
           "month":5, 
           "year":0 
         } 
      } 
  }
} 
```

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const mailboxSettings = {
  workingHours: {
      endTime: '18:30:00.0000000', 
      daysOfWeek: [ 
          'Monday', 
          'Tuesday', 
          'Wednesday', 
          'Thursday', 
          'Friday', 
          'Saturday' 
      ], 
      timeZone: { 
         '@odata.type': '#microsoft.graph.customTimeZone', 
         bias: -300, 
         name: 'Customized Time Zone',
         standardOffset: {   
           time: '02:00:00.0000000', 
           dayOccurrence: 2, 
           dayOfWeek: 'Sunday', 
           month: 10, 
           year: 0 
         }, 
         daylightOffset: {   
           daylightBias: 100, 
           time: '02:00:00.0000000', 
           dayOccurrence: 4, 
           dayOfWeek: 'Sunday', 
           month: 5, 
           year: 0 
         } 
      } 
  }
};

await client.api('/me/mailboxSettings')
	.update(mailboxSettings);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#users('94447c6e-ea4c-494c-a9ed-d905e366c5cb')/mailboxSettings",
    "workingHours":{
        "daysOfWeek":[
            "monday",
            "tuesday",
            "wednesday",
            "thursday",
            "friday",
            "saturday"
        ],
        "startTime":"09:00:00.0000000",
        "endTime":"18:30:00.0000000",
        "timeZone":{
            "@odata.type":"#microsoft.graph.customTimeZone",
            "bias":-200,
            "name":"Customized Time Zone",
            "standardOffset":{
                "time":"02:00:00.0000000",
                "dayOccurrence":4,
                "dayOfWeek":"sunday",
                "month":5,
                "year":0
            },
            "daylightOffset":{
                "daylightBias":-100,
                "time":"02:00:00.0000000",
                "dayOccurrence":2,
                "dayOfWeek":"sunday",
                "month":10,
                "year":0
            }
        }
    }
}
```
