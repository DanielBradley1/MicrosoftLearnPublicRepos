<!-- Source: https://learn.microsoft.com/en-us/graph/outlook-create-event-in-shared-delegated-calendar -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create Outlook events in a shared or delegated calendar

In Outlook, customers can share a calendar with other users and let them view, create, or modify events in that calendar. Customers can also grant a delegate to act on their behalf to receive or respond to meeting requests or create or change items in the calendar.

Programmatically, Microsoft Graph supports reading or writing events in calendars that have been shared by other users, as well as reading the shared calendars, and updating the calendar name for sharees. The support also applies to calendars that have been delegated. The rest of this article walks through creating a meeting event in a shared or delegated calendar. For getting events, refer to [Get Outlook events in a shared or delegated calendar](https://learn.microsoft.com/en-us/graph/outlook-get-shared-events-calendars).

The walkthrough below uses the example scenario where Alex has delegated his primary calendar to Adele in Outlook, and kept the default Outlook mailbox setting to direct meeting requests and responses to only delegates. \(This setting corresponds to the **delegateMeetingMessageDeliveryOptions** property of Alex' [mailboxSettings](https://learn.microsoft.com/en-us/graph/api/resources/mailboxsettings) set as the default value `sendToDelegateOnly`.\)

The walkthrough describes a few subsequent steps:

1. [Adele gets the calendar that Alex has delegated to her](#step-1-adele-gets-the-delegated-calendar).
2. [Adele sends a meeting invitation to Christie and Megan on Alex' behalf](#step-2-adele-creates-and-sends-an-invitation-on-alex-behalf).
3. Christie receives the meeting request, and inspects the associated event in her calenda
4. [Christie responds tentative to the invitation](#step-4-christie-responds-to-the-meeting-request).
5. [Adele receives Christie's response message](#step-5-adele-receives-the-response-message).
6. [Alex checks attendees' responses as part of the event](#step-6-alex-accesses-responses-as-part-of-the-event).

If Alex has shared and not delegated his calendar with Adele:

- Signed in as Adele, an app can [get the calendar that Alex has shared with Adele](#step-1-adele-gets-the-delegated-calendar)
- The app can use the requests and responses in steps 2 to 4 to apply to the shared calendar the same way as the delegated calendar.
- In step 5, the app can sign in as Alex, instead of Adele, to receive Christie's response message.

## Step 1: Adele gets the delegated calendar

Signed in as Adele, get the calendars she has access to and identify the one Alex has delegated to her, so to use it in the next step to create an event in that calendar.

**Microsoft Graph permissions**

Use the least privileged delegated permission, `Calendars.Read.Shared`. For more information, see the [Calendars.Read.Shared permission in the permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference#calendarsreadshared).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/calendars
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Calendars.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calendars, err := graphClient.Me().Calendars().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CalendarCollectionResponse result = graphClient.me().calendars().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let calendars = await client.api('/me/calendars')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->me()->calendars()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Calendar

# A UPN can also be used as -UserId.
Get-MgUserCalendar -UserId $userId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.calendars.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

Notice a successful response includes the response code HTTP 200, Adele's own primary calendar, and a copy of the calendar delegated by Alex in Adele's mailbox, with the following properties:

- **canShare** is false since Adele is only a delegate and not the calendar owner.
- **canEdit** is true since as delegate, Adele has write access to non-private events in the delegated calendar.
- **owner** is `Alex Wilber` indicating it is Alex' calendar.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('d3b9214b-dd8b-441d-b7dc-c446c9fa0e69')/calendars",
    "value": [
        {
            "id": "AQMkADGkAAAJMjAAAAA==",
            "name": "Calendar",
            "color": "auto",
            "changeKey": "NDznl+Uh50WkanaCOKHkaQAAAAACXQ==",
            "canShare": true,
            "canViewPrivateItems": true,
            "canEdit": true,
            "owner": {
                "name": "Adele Vance",
                "address": "AdeleV@contoso.com"
            }
        },
        {
            "id": "AAMkADRpAABf0JlzAAA=",
            "name": "Alex Wilber",
            "color": "auto",
            "changeKey": "NDznl+Uh50WkanaCOKHkaQAAX8m4eQ==",
            "canShare": false,
            "canViewPrivateItems": false,
            "canEdit": true,
            "owner": {
                "name": "Alex Wilber",
                "address": "AlexW@contoso.com"
            }
        }
    ]
}
```

Note

Signed in as Adele, you can alternatively get the delegated calendar directly from Alex' mailbox, by specifying Alex' identity and the `calendar` shortcut, as in `GET https://graph.microsoft.com/v1.0/users/AlexW@contoso.com/calendar`. The returned calendar ID corresponds to only Alex' mailbox.

## Step 2: Adele creates and sends an invitation on Alex' behalf

Signed in as Adele, use the calendar ID obtained from step 1 to create an [event](https://learn.microsoft.com/en-us/graph/api/resources/event) in the delegated calendar and send it to Christie and Megan, on Alex' behalf.

**Microsoft Graph permissions**

Use the least privileged delegated permission, `Calendars.ReadWrite.Shared`. For more information, see [Calendars.ReadWrite.Shared permission in the permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference#calendarsreadwriteshared).

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/me/calendars/AAMkADRpAABf0JlzAAA=/events

Prefer: outlook.timezone="Pacific Standard Time"
Content-type: application/json

{
  "subject": "Christmas dinner",
  "body": {
    "contentType": "HTML",
    "content": "Happy holidays!"
  },
  "start": {
      "dateTime": "2019-12-25T18:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "end": {
      "dateTime": "2019-12-25T22:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "location":{
      "displayName":"Alex' home"
  },
  "attendees": [
    {
      "emailAddress": {
        "address":"meganb@contoso.com",
        "name": "Megan Bowen"
      },
      "type": "required"
    },
    {
      "emailAddress": {
        "address":"ChristieC@contoso.com",
        "name": "Christie Cline"
      },
      "type": "required"
    }
  ]
}
```

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const event = Prefer: outlook.timezone='Pacific Standard Time'
Content-type: application/json

{
  subject: 'Christmas dinner',
  body: {
    contentType: 'HTML',
    content: 'Happy holidays!'
  },
  start: {
      dateTime: '2019-12-25T18:00:00',
      timeZone: 'Pacific Standard Time'
  },
  end: {
      dateTime: '2019-12-25T22:00:00',
      timeZone: 'Pacific Standard Time'
  },
  location: {
      displayName: 'Alex\' home'
  },
  attendees: [
    {
      emailAddress: {
        address: 'meganb@contoso.com',
        name: 'Megan Bowen'
      },
      type: 'required'
    },
    {
      emailAddress: {
        address: 'ChristieC@contoso.com',
        name: 'Christie Cline'
      },
      type: 'required'
    }
  ]
};

await client.api('/me/calendars/AAMkADRpAABf0JlzAAA=/events')
	.post(event);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

Notice a successful response includes the response code HTTP 200 and the following [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage) properties:

- **meetingMessageType** specifies this message is `meetingRequest`.
- **sender** is Adele.
- **from** is Alex.
- **toRecipients** include Megan and Christie.

And the following [event](https://learn.microsoft.com/en-us/graph/api/resources/event) properties:

- **attendees** include Alex, Megan, and Christie.
- **organizer** is Alex.

Adele's identity appears only in the **sender** property of the **eventMessage** and not in the associated **event**.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('662b947c-d9a1-4064-926c-eba1316d4462')/messages(microsoft.graph.eventMessage/event())/$entity",
    "@odata.type": "#microsoft.graph.eventMessage",
    "@odata.etag": "W/\"CwAAABYAAADK82uJYVo4RrFV3ADVj3fyAABZ378h\"",
    "id": "AAMkADADVj3fyAABZ5hYdAAA=",
    "createdDateTime": "2019-12-21T04:59:03Z",
    "lastModifiedDateTime": "2019-12-21T04:59:04Z",
    "changeKey": "CwAAABYAAADK82uJYVo4RrFV3ADVj3fyAABZ378h",
    "categories": [],
    "receivedDateTime": "2019-12-21T04:59:03Z",
    "sentDateTime": "2019-12-21T04:59:01Z",
    "hasAttachments": false,
    "internetMessageId": "<DM6PR17MB3593711A1C0A098167F5A977A12C0@DM6PR17MB3593.namprd17.prod.outlook.com>",
    "subject": "Christmas dinner",
    "bodyPreview": "Happy holidays!",
    "importance": "normal",
    "parentFolderId": "AQMkADIAAAIBDAAAAA==",
    "conversationId": "AAQkADNqQlzYAM8jQM=",
    "conversationIndex": "AdW3u1xx5S7TYrbluE2pCXNgAzyNAw==",
    "isDeliveryReceiptRequested": null,
    "isReadReceiptRequested": false,
    "isRead": true,
    "isDraft": false,
    "webLink": "https://outlook.office365.com/owa/?ItemID=AAMkADADVj3fyAABZ5hYdAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
    "inferenceClassification": "focused",
    "meetingMessageType": "meetingRequest",
    "body": {
        "contentType": "html",
        "content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nHappy holidays!\r\n</body>\r\n</html>\r\n"
    },
    "sender": {
        "emailAddress": {
            "name": "Adele Vance",
            "address": "AdeleV@contoso.com"
        }
    },
    "from": {
        "emailAddress": {
            "name": "Alex Wilber",
            "address": "AlexW@contoso.com"
        }
    },
    "toRecipients": [
        {
            "emailAddress": {
                "name": "Megan Bowen",
                "address": "MeganB@contoso.com"
            }
        },
        {
            "emailAddress": {
                "name": "Christie Cline",
                "address": "ChristieC@contoso.com"
            }
        }
    ],
    "ccRecipients": [],
    "bccRecipients": [],
    "replyTo": [],
    "flag": {
        "flagStatus": "notFlagged"
    },
    "event": {
        "@odata.etag": "W/\"yvNriWFaOEaxVdwA1Y938gAAX+T7Jg==\"",
        "id": "AAMkADADVj3fyAABZ5ieyAAA=",
        "createdDateTime": "2019-12-21T04:59:03.4336242Z",
        "lastModifiedDateTime": "2019-12-27T01:38:32.3766961Z",
        "changeKey": "yvNriWFaOEaxVdwA1Y938gAAX+T7Jg==",
        "categories": [],
        "originalStartTimeZone": "Pacific Standard Time",
        "originalEndTimeZone": "Pacific Standard Time",
        "iCalUId": "040000008200FEFE0BA532444B5FD89BDE22BA103",
        "reminderMinutesBeforeStart": 15,
        "isReminderOn": true,
        "hasAttachments": false,
        "subject": "Christmas dinner",
        "bodyPreview": "Happy holidays!",
        "importance": "normal",
        "sensitivity": "normal",
        "isAllDay": false,
        "isCancelled": false,
        "isOrganizer": false,
        "responseRequested": true,
        "seriesMasterId": null,
        "showAs": "tentative",
        "type": "singleInstance",
        "webLink": "https://outlook.office365.com/owa/?itemid=AAMkADADVj3fyAABZ5ieyAAA%3D&exvsurl=1&path=/calendar/item",
        "onlineMeetingUrl": null,
        "recurrence": null,
        "responseStatus": {
            "response": "none",
            "time": "2019-12-21T05:16:48.8931825Z"
        },
        "body": {
            "contentType": "html",
            "content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nHappy holidays!\r\n</body>\r\n</html>\r\n"
        },
        "start": {
            "dateTime": "2019-12-26T02:00:00.0000000",
            "timeZone": "UTC"
        },
        "end": {
            "dateTime": "2019-12-26T06:00:00.0000000",
            "timeZone": "UTC"
        },
        "location": {
            "displayName": "Alex' home",
            "locationType": "default",
            "uniqueId": "Alex' home",
            "uniqueIdType": "private"
        },
        "locations": [
            {
                "displayName": "Alex' home",
                "locationType": "default",
                "uniqueId": "1396aaf3-e344-4567-a4e3-797557ec24c8",
                "uniqueIdType": "locationStore"
            }
        ],
        "attendees": [
            {
                "type": "required",
                "status": {
                    "response": "none",
                    "time": "0001-01-01T00:00:00Z"
                },
                "emailAddress": {
                    "name": "Alex Wilber",
                    "address": "AlexW@contoso.com"
                }
            },
            {
                "type": "required",
                "status": {
                    "response": "none",
                    "time": "0001-01-01T00:00:00Z"
                },
                "emailAddress": {
                    "name": "Megan Bowen",
                    "address": "MeganB@contoso.com"
                }
            },
            {
                "type": "required",
                "status": {
                    "response": "none",
                    "time": "0001-01-01T00:00:00Z"
                },
                "emailAddress": {
                    "name": "Christie Cline",
                    "address": "ChristieC@contoso.com"
                }
            }
        ],
        "organizer": {
            "emailAddress": {
                "name": "Alex Wilber",
                "address": "AlexW@contoso.com"
            }
        }
    }
}
```

## Step 4: Christie responds to the meeting request

Signed in as Christie, reply to the **event** as tentative, and include a reply message in the response:

**Microsoft Graph permissions**

Use the least privileged delegated permission, `Calendars.ReadWrite.Shared`. For more information, see [Calendars.ReadWrite.Shared permission in the permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference#calendarsreadwriteshared).

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```http
POST https://graph.microsoft.com/v1.0/me/events/AAMkADADVj3fyAABZ5ieyAAA=/tentativelyAccept
Content-type: application/json

{
  "comment": "I will probably be able to make it.",
  "sendResponse": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.Events.Item.TentativelyAccept;

var requestBody = new TentativelyAcceptPostRequestBody
{
	Comment = "I will probably be able to make it.",
	SendResponse = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Me.Events["{event-id}"].TentativelyAccept.PostAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

requestBody := graphusers.NewItemTentativelyAcceptPostRequestBody()
comment := "I will probably be able to make it."
requestBody.SetComment(&comment) 
sendResponse := true
requestBody.SetSendResponse(&sendResponse) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Me().Events().ByEventId("event-id").TentativelyAccept().Post(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.events.item.tentativelyaccept.TentativelyAcceptPostRequestBody tentativelyAcceptPostRequestBody = new com.microsoft.graph.users.item.events.item.tentativelyaccept.TentativelyAcceptPostRequestBody();
tentativelyAcceptPostRequestBody.setComment("I will probably be able to make it.");
tentativelyAcceptPostRequestBody.setSendResponse(true);
graphClient.me().events().byEventId("{event-id}").tentativelyAccept().post(tentativelyAcceptPostRequestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const tentativelyAccept = {
  comment: 'I will probably be able to make it.',
  sendResponse: true
};

await client.api('/me/events/AAMkADADVj3fyAABZ5ieyAAA=/tentativelyAccept')
	.post(tentativelyAccept);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Events\Item\TentativelyAccept\TentativelyAcceptPostRequestBody;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new TentativelyAcceptPostRequestBody();
$requestBody->setComment('I will probably be able to make it.');
$requestBody->setSendResponse(true);

$graphServiceClient->me()->events()->byEventId('event-id')->tentativelyAccept()->post($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	comment = "I will probably be able to make it."
	sendResponse = $true
}

# A UPN can also be used as -UserId.
Invoke-MgAcceptUserEventTentatively -UserId $userId -EventId $eventId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.events.item.tentatively_accept.tentatively_accept_post_request_body import TentativelyAcceptPostRequestBody
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = TentativelyAcceptPostRequestBody(
	comment = "I will probably be able to make it.",
	send_response = True,
)

await graph_client.me.events.by_event_id('event-id').tentatively_accept.post(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

A successful response returns HTTP 202 Accepted.

```http
HTTP/1.1 202 Accepted
```

## Step 5: Adele receives the response message

Because Adele is a delegate of Alex' primary calendar, Adele receives all meeting responses for that calendar on Alex' behalf.

Signed in as Adele, get the [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage) that represents the response from Christie in step 4.

**Microsoft Graph permissions**

Use the least privileged delegated permission, `Mail.Read.Shared`. For more information, see [Mail.Read.Shared permission in the permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference#mailreadshared).

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/messages/AAMkADI4oeRpAABf0HJUAAA=
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Messages["{message-id}"].GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Me().Messages().ByMessageId("message-id").Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Message result = graphClient.me().messages().byMessageId("{message-id}").get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let message = await client.api('/me/messages/AAMkADI4oeRpAABf0HJUAAA=')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->me()->messages()->byMessageId('message-id')->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Mail

# A UPN can also be used as -UserId.
Get-MgUserMessage -UserId $userId -MessageId $messageId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.messages.by_message_id('message-id').get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

Notice a successful response includes the response code HTTP 200 and the following [eventMessage](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage) properties:

- **meetingMessageType** is `meetingTenativelyAccepted`.
- **from** is Christie.
- **toRecipients** includes only Adele, but not the calendar owner Alex. This is because Alex kept the default to have Outlook direct all meeting responses to only delegates.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('d3b9214b-dd8b-441d-b7dc-c446c9fa0e69')/messages/$entity",
    "@odata.type": "#microsoft.graph.eventMessage",
    "@odata.etag": "W/\"DAAAABYAAAA0POeX5SHnRaRqdoI4oeRpAABfybkT\"",
    "id": "AAMkADI4oeRpAABf0HJUAAA=",
    "createdDateTime": "2019-12-21T05:16:55Z",
    "lastModifiedDateTime": "2019-12-21T05:16:57Z",
    "changeKey": "DAAAABYAAAA0POeX5SHnRaRqdoI4oeRpAABfybkT",
    "categories": [],
    "receivedDateTime": "2019-12-21T05:16:56Z",
    "sentDateTime": "2019-12-21T05:16:49Z",
    "hasAttachments": false,
    "internetMessageId": "<86880ccb8ec64184996e46eaddaed279@DM6PR17MB3593.namprd17.prod.outlook.com>",
    "subject": "Tentative: Christmas dinner",
    "bodyPreview": "I will probably be able to make it.",
    "importance": "normal",
    "parentFolderId": "AQMkAD5GkAAAIBDAAAAA==",
    "conversationId": "AAQkADK25bhNqQlzYAM8jQM=",
    "conversationIndex": "AdW3u1xx5S7TYrbluE2pCXNgAzyNAwAAoBoZ",
    "isDeliveryReceiptRequested": null,
    "isReadReceiptRequested": false,
    "isRead": false,
    "isDraft": false,
    "webLink": "https://outlook.office365.com/owa/?ItemID=AAMkADI4oeRpAABf0HJUAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
    "inferenceClassification": "focused",
    "meetingMessageType": "meetingTenativelyAccepted",
    "body": {
        "contentType": "html",
        "content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nI will probably be able to make it.\r\n</body>\r\n</html>\r\n"
    },
    "sender": {
        "emailAddress": {
            "name": "Christie Cline",
            "address": "ChristieC@contoso.com"
        }
    },
    "from": {
        "emailAddress": {
            "name": "Christie Cline",
            "address": "ChristieC@contoso.com"
        }
    },
    "toRecipients": [
        {
            "emailAddress": {
                "name": "Adele Vance",
                "address": "AdeleV@contoso.com"
            }
        }
    ],
    "ccRecipients": [],
    "bccRecipients": [],
    "replyTo": [],
    "flag": {
        "flagStatus": "notFlagged"
    }
}
```

## Step 6: Alex accesses responses as part of the event

Because Alex kept the default to have Outlook direct all meeting requests and responses to only delegates, Alex does not receive Christie's response from step 4. He can however get the response through the [event](https://learn.microsoft.com/en-us/graph/api/resources/event) in his primary calendar.

Signed in as Alex, get the [event](https://learn.microsoft.com/en-us/graph/api/resources/event) that Adele created in step 2 and get responses from the **attendees** property.

**Microsoft Graph permissions**

Use the least privileged delegated permission, `Calendars.Read`. For more information, see [Calendars.Read permission in the permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference#calendarsread).

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/calendar/events/AAMkADJXJGu0AABf02qwAAA=
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Calendar.Events["{event-id}"].GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
events, err := graphClient.Me().Calendar().Events().ByEventId("event-id").Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Event result = graphClient.me().calendar().events().byEventId("{event-id}").get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let event = await client.api('/me/calendar/events/AAMkADJXJGu0AABf02qwAAA=')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->me()->calendar()->events()->byEventId('event-id')->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.me.calendar.events.by_event_id('event-id').get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

Notice a successful response includes the response code HTTP 200 and the following [event](https://learn.microsoft.com/en-us/graph/api/resources/event) properties:

- **isOrganizer** is true.
- **attendees** include only Megan and Christie.
- The **status** property of each **attendee** instance indicates any response from the attendee:

  - Megan's response is `none`.
  - Christie's response is `tentativelyAccepted`.

- **organizer** is Alex.
- No property in the returned **event** indicates the delegate, Adele.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('64339082-ed84-4b0b-b4ab-004ae54f3747')/calendars('AQMkADAw7QAAAJfygAAAA%3D%3D')/events/$entity",
    "@odata.etag": "W/\"NEXywgsVrkeNsFsyVyRrtAAAX8xuhA==\"",
    "id": "AAMkADJXJGu0AABf02qwAAA=",
    "createdDateTime": "2019-12-21T04:59:01.4435895Z",
    "lastModifiedDateTime": "2019-12-21T05:16:54.689345Z",
    "changeKey": "NEXywgsVrkeNsFsyVyRrtAAAX8xuhA==",
    "categories": [],
    "originalStartTimeZone": "Pacific Standard Time",
    "originalEndTimeZone": "Pacific Standard Time",
    "iCalUId": "040000008200FEFE0BA532444B5FD89BDE22BA103",
    "reminderMinutesBeforeStart": 15,
    "isReminderOn": true,
    "hasAttachments": false,
    "subject": "Christmas dinner",
    "bodyPreview": "Happy holidays!",
    "importance": "normal",
    "sensitivity": "normal",
    "isAllDay": false,
    "isCancelled": false,
    "isOrganizer": true,
    "responseRequested": true,
    "seriesMasterId": null,
    "showAs": "busy",
    "type": "singleInstance",
    "webLink": "https://outlook.office365.com/owa/?itemid=AAMkADJXJGu0AABf02qwAAA%3D&exvsurl=1&path=/calendar/item",
    "onlineMeetingUrl": null,
    "recurrence": null,
    "responseStatus": {
        "response": "organizer",
        "time": "0001-01-01T00:00:00Z"
    },
    "body": {
        "contentType": "html",
        "content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nHappy holidays!\r\n</body>\r\n</html>\r\n"
    },
    "start": {
        "dateTime": "2019-12-26T02:00:00.0000000",
        "timeZone": "UTC"
    },
    "end": {
        "dateTime": "2019-12-26T06:00:00.0000000",
        "timeZone": "UTC"
    },
    "location": {
        "displayName": "Alex' home",
        "locationType": "default",
        "uniqueId": "Alex' home",
        "uniqueIdType": "private"
    },
    "locations": [
        {
            "displayName": "Alex' home",
            "locationType": "default",
            "uniqueId": "Alex' home",
            "uniqueIdType": "private"
        }
    ],
    "attendees": [
        {
            "type": "required",
            "status": {
                "response": "none",
                "time": "0001-01-01T00:00:00Z"
            },
            "emailAddress": {
                "name": "Megan Bowen",
                "address": "MeganB@contoso.com"
            }
        },
        {
            "type": "required",
            "status": {
                "response": "tentativelyAccepted",
                "time": "2019-12-21T05:16:48.8931825Z"
            },
            "emailAddress": {
                "name": "Christie Cline",
                "address": "ChristieC@contoso.com"
            }
        }
    ],
    "organizer": {
        "emailAddress": {
            "name": "Alex Wilber",
            "address": "AlexW@contoso.com"
        }
    }
}
```

## Related content

- [Get Outlook events in a shared or delegated calendar](https://learn.microsoft.com/en-us/graph/outlook-get-shared-events-calendars)
- [Share or delegate a calendar in Outlook \(preview\)](https://learn.microsoft.com/en-us/graph/outlook-share-or-delegate-calendar)
