<!-- Source: https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-post-singlevalueextendedproperties?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# Create single-value extended property

Namespace: microsoft.graph

Create one or more single-value extended properties in a new or existing instance of a resource.

The following user resources are supported:

- [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0)
- [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0)
- [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0)
- [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0)
- [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0)
- [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0)
- [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0)
- [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0)

The following group resources:

- group [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0)
- group [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0)
- group [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0)

See [Extended properties overview](https://learn.microsoft.com/en-us/graph/api/resources/extended-properties-overview?view=graph-rest-1.0) for more information about when to use open extensions or extended properties, and how to specify extended properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Depending on the resource you're creating the extended property in and the permission type \(delegated or application\) you request, the permission specified in the following table is the minimum required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | Calendars.ReadWrite | Calendars.ReadWrite | Calendars.ReadWrite |
| [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Contacts.ReadWrite | Contacts.ReadWrite | Contacts.ReadWrite |
| [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0) | Contacts.ReadWrite | Contacts.ReadWrite | Contacts.ReadWrite |
| [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Calendars.ReadWrite | Calendars.ReadWrite | Calendars.ReadWrite |
| group [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | Group.ReadWrite.All | Not supported | Not supported |
| group [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Group.ReadWrite.All | Not supported | Not supported |
| group [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | Group.ReadWrite.All | Not supported | Not supported |
| [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) | MailboxFolder.Read | Not supported. | MailboxFolder.Read.All |
| [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0) | Mail.ReadWrite | Mail.ReadWrite | Mail.ReadWrite |
| [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Mail.ReadWrite | Mail.ReadWrite | Mail.ReadWrite |
| [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0) | ShortNotes.ReadWrite | ShortNotes.ReadWrite | ShortNotes.ReadWrite.All |

## HTTP request

You can create extended properties in a new or existing resource instance.

To create one or more extended properties in a *new* resource instance, use the same REST request as creating the instance, and include the properties of the new resource instance *and extended property* in the request body. Some resources support creation in more than one way. For more information on creating these resource instances, see the corresponding articles for creating a [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0), [mailFolder](https://learn.microsoft.com/en-us/graph/api/user-post-mailfolders?view=graph-rest-1.0), [event](https://learn.microsoft.com/en-us/graph/api/user-post-events?view=graph-rest-1.0), [calendar](https://learn.microsoft.com/en-us/graph/api/user-post-calendars?view=graph-rest-1.0), [contact](https://learn.microsoft.com/en-us/graph/api/user-post-contacts?view=graph-rest-1.0), [contactFolder](https://learn.microsoft.com/en-us/graph/api/user-post-contactfolders?view=graph-rest-1.0), [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/mailbox-post-folders?view=graph-rest-1.0), [group event](https://learn.microsoft.com/en-us/graph/api/group-post-events?view=graph-rest-1.0), and [group post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0).

The following is the syntax of the requests.

```http
POST /me/messages
POST /users/{id|userPrincipalName}/messages
POST /me/mailFolders/{id}/messages

POST /me/mailFolders
POST /users/{id|userPrincipalName}/mailFolders

POST /me/events
POST /users/{id|userPrincipalName}/events

POST /me/calendars
POST /users/{id|userPrincipalName}/calendars

POST /me/contacts
POST /users/{id|userPrincipalName}/contacts

POST /me/contactFolders
POST /users/{id|userPrincipalName}/contactFolders

POST /admin/exchange/mailboxes/{mailboxId}/folders

POST /me/notes
POST /users/{id|userPrincipalName}/notes

POST /groups/{id}/events

POST /groups/{id}/threads/{id}/posts/{id}/reply
POST /groups/{id}/conversations/{id}/threads/{id}/posts/{id}/reply
POST /groups/{id}/threads/{id}/reply
POST /groups/{id}/conversations/{id}/threads/{id}/reply
POST /groups/{id}/threads
POST /groups/{id}/conversations
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

To create one or more extended properties in an existing resource instance, specify the instance in the request, and include the extended property in the request body.

**Note** You can't create an extended property in an existing group post.

```http
PATCH /me/messages/{id}
PATCH /users/{id|userPrincipalName}/messages/{id}
PATCH /me/mailFolders/{id}/messages/{id}

PATCH /me/mailFolders/{id}
PATCH /users/{id|userPrincipalName}/mailFolders/{id}

PATCH /me/events/{id}
PATCH /users/{id|userPrincipalName}/events/{id}

PATCH /me/calendars/{id}
PATCH /users/{id|userPrincipalName}/calendars/{id}

PATCH /me/contacts/{id}
PATCH /users/{id|userPrincipalName}/contacts/{id}

PATCH /me/contactFolders/{id}
PATCH /users/{id|userPrincipalName}/contactFolders/{id}

PATCH /admin/exchange/mailboxes/{mailboxId}/folders/{mailboxFolderId}

PATCH /me/notes/{id}
PATCH /users/{id|userPrincipalName}/notes/{id}

PATCH /groups/{id}/events/{id}
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

## Request headers

| Name | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json |

## Request body

Provide a JSON body of each [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0) object in the **singleValueExtendedProperties** collection property of the resource instance.

| Property | Type | Description |
| :--- | :--- | :--- |
| singleValueExtendedProperties | [singleValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/singlevaluelegacyextendedproperty?view=graph-rest-1.0) collection | An array of one or more single-valued extended properties. |
| id | String | For each property in the **singleValueExtendedProperties** collection, specify this to identify the property. It must follow one of the supported formats. See [Outlook extended properties overview](https://learn.microsoft.com/en-us/graph/api/resources/extended-properties-overview?view=graph-rest-1.0) for more information. Required. |
| value | string | For each property in the **singleValueExtendedProperties** collection, specify the property value. Required. |

When creating an extended property in a *new* resource instance, in addition to the new **singleValueExtendedProperties** collection, provide a JSON representation of that resource instance \(that is, a [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0), [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0), [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0), etc.\)

## Response

#### Response code

An operation successful in creating an extended property in a new resource instance returns `201 Created`, except in a new group post, depending on the method used, the operation can return `200 OK` or `202 Accepted`.

In an existing resource instance, a successful create operation returns `200 OK`.

#### Response body

When creating an extended property, the response includes only the new or existing instance but not the new extended property. To see the newly created extended property, [get the instance expanded with the extended property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-1.0).

When creating an extended property in a *new* [group post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) by replying to a thread or post, the response includes only a response code but not the new post nor the extended property.

## Examples

### Example 1: Create a new event and a single-value extended property

#### Request

The first example creates a new event and a single-value extended property in the same POST operation. Apart from the properties you'd normally include for a new event, the request body includes the **singleValueExtendedProperties** collection that contains one single-value extended property, and the following for the property:

- **id** specifies the property type as `String`, the GUID, and the property named `Fun`.
- **value** specifies `Food` as the value of the `Fun` property.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/me/events
Content-Type: application/json

{
  "subject": "Celebrate Thanksgiving",
  "body": {
    "contentType": "HTML",
    "content": "Let's get together!"
  },
  "start": {
      "dateTime": "2015-11-26T18:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "end": {
      "dateTime": "2015-11-26T23:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "attendees": [
    {
      "emailAddress": {
        "address": "Terrie@contoso.com",
        "name": "Terrie Barrera"
      },
      "type": "Required"
    }
  ],
  "singleValueExtendedProperties": [
     {
           "id":"String {66f5a359-4659-4830-9070-00040ec6ac6e} Name Fun",
           "value":"Food"
     }
  ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Event
{
	Subject = "Celebrate Thanksgiving",
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "Let's get together!",
	},
	Start = new DateTimeTimeZone
	{
		DateTime = "2015-11-26T18:00:00",
		TimeZone = "Pacific Standard Time",
	},
	End = new DateTimeTimeZone
	{
		DateTime = "2015-11-26T23:00:00",
		TimeZone = "Pacific Standard Time",
	},
	Attendees = new List<Attendee>
	{
		new Attendee
		{
			EmailAddress = new EmailAddress
			{
				Address = "Terrie@contoso.com",
				Name = "Terrie Barrera",
			},
			Type = AttendeeType.Required,
		},
	},
	SingleValueExtendedProperties = new List<SingleValueLegacyExtendedProperty>
	{
		new SingleValueLegacyExtendedProperty
		{
			Id = "String {66f5a359-4659-4830-9070-00040ec6ac6e} Name Fun",
			Value = "Food",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Events.PostAsync(requestBody);
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

requestBody := graphmodels.NewEvent()
subject := "Celebrate Thanksgiving"
requestBody.SetSubject(&subject) 
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "Let's get together!"
body.SetContent(&content) 
requestBody.SetBody(body)
start := graphmodels.NewDateTimeTimeZone()
dateTime := "2015-11-26T18:00:00"
start.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
start.SetTimeZone(&timeZone) 
requestBody.SetStart(start)
end := graphmodels.NewDateTimeTimeZone()
dateTime := "2015-11-26T23:00:00"
end.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
end.SetTimeZone(&timeZone) 
requestBody.SetEnd(end)


attendee := graphmodels.NewAttendee()
emailAddress := graphmodels.NewEmailAddress()
address := "Terrie@contoso.com"
emailAddress.SetAddress(&address) 
name := "Terrie Barrera"
emailAddress.SetName(&name) 
attendee.SetEmailAddress(emailAddress)
type := graphmodels.REQUIRED_ATTENDEETYPE 
attendee.SetType(&type) 

attendees := []graphmodels.Attendeeable {
	attendee,
}
requestBody.SetAttendees(attendees)


singleValueLegacyExtendedProperty := graphmodels.NewSingleValueLegacyExtendedProperty()
id := "String {66f5a359-4659-4830-9070-00040ec6ac6e} Name Fun"
singleValueLegacyExtendedProperty.SetId(&id) 
value := "Food"
singleValueLegacyExtendedProperty.SetValue(&value) 

singleValueExtendedProperties := []graphmodels.SingleValueLegacyExtendedPropertyable {
	singleValueLegacyExtendedProperty,
}
requestBody.SetSingleValueExtendedProperties(singleValueExtendedProperties)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
events, err := graphClient.Me().Events().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Event event = new Event();
event.setSubject("Celebrate Thanksgiving");
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("Let's get together!");
event.setBody(body);
DateTimeTimeZone start = new DateTimeTimeZone();
start.setDateTime("2015-11-26T18:00:00");
start.setTimeZone("Pacific Standard Time");
event.setStart(start);
DateTimeTimeZone end = new DateTimeTimeZone();
end.setDateTime("2015-11-26T23:00:00");
end.setTimeZone("Pacific Standard Time");
event.setEnd(end);
LinkedList<Attendee> attendees = new LinkedList<Attendee>();
Attendee attendee = new Attendee();
EmailAddress emailAddress = new EmailAddress();
emailAddress.setAddress("Terrie@contoso.com");
emailAddress.setName("Terrie Barrera");
attendee.setEmailAddress(emailAddress);
attendee.setType(AttendeeType.Required);
attendees.add(attendee);
event.setAttendees(attendees);
LinkedList<SingleValueLegacyExtendedProperty> singleValueExtendedProperties = new LinkedList<SingleValueLegacyExtendedProperty>();
SingleValueLegacyExtendedProperty singleValueLegacyExtendedProperty = new SingleValueLegacyExtendedProperty();
singleValueLegacyExtendedProperty.setId("String {66f5a359-4659-4830-9070-00040ec6ac6e} Name Fun");
singleValueLegacyExtendedProperty.setValue("Food");
singleValueExtendedProperties.add(singleValueLegacyExtendedProperty);
event.setSingleValueExtendedProperties(singleValueExtendedProperties);
Event result = graphClient.me().events().post(event);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const event = {
  subject: 'Celebrate Thanksgiving',
  body: {
    contentType: 'HTML',
    content: 'Let\'s get together!'
  },
  start: {
      dateTime: '2015-11-26T18:00:00',
      timeZone: 'Pacific Standard Time'
  },
  end: {
      dateTime: '2015-11-26T23:00:00',
      timeZone: 'Pacific Standard Time'
  },
  attendees: [
    {
      emailAddress: {
        address: 'Terrie@contoso.com',
        name: 'Terrie Barrera'
      },
      type: 'Required'
    }
  ],
  singleValueExtendedProperties: [
     {
           id: 'String {66f5a359-4659-4830-9070-00040ec6ac6e} Name Fun',
           value: 'Food'
     }
  ]
};

await client.api('/me/events')
	.post(event);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Event;
use Microsoft\Graph\Generated\Models\ItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;
use Microsoft\Graph\Generated\Models\Attendee;
use Microsoft\Graph\Generated\Models\EmailAddress;
use Microsoft\Graph\Generated\Models\AttendeeType;
use Microsoft\Graph\Generated\Models\SingleValueLegacyExtendedProperty;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Event();
$requestBody->setSubject('Celebrate Thanksgiving');
$body = new ItemBody();
$body->setContentType(new BodyType('hTML'));
$body->setContent('Let\'s get together!');
$requestBody->setBody($body);
$start = new DateTimeTimeZone();
$start->setDateTime('2015-11-26T18:00:00');
$start->setTimeZone('Pacific Standard Time');
$requestBody->setStart($start);
$end = new DateTimeTimeZone();
$end->setDateTime('2015-11-26T23:00:00');
$end->setTimeZone('Pacific Standard Time');
$requestBody->setEnd($end);
$attendeesAttendee1 = new Attendee();
$attendeesAttendee1EmailAddress = new EmailAddress();
$attendeesAttendee1EmailAddress->setAddress('Terrie@contoso.com');
$attendeesAttendee1EmailAddress->setName('Terrie Barrera');
$attendeesAttendee1->setEmailAddress($attendeesAttendee1EmailAddress);
$attendeesAttendee1->setType(new AttendeeType('required'));
$attendeesArray []= $attendeesAttendee1;
$requestBody->setAttendees($attendeesArray);

$singleValueExtendedPropertiesSingleValueLegacyExtendedProperty1 = new SingleValueLegacyExtendedProperty();
$singleValueExtendedPropertiesSingleValueLegacyExtendedProperty1->setId('String {66f5a359-4659-4830-9070-00040ec6ac6e} Name Fun');
$singleValueExtendedPropertiesSingleValueLegacyExtendedProperty1->setValue('Food');
$singleValueExtendedPropertiesArray []= $singleValueExtendedPropertiesSingleValueLegacyExtendedProperty1;
$requestBody->setSingleValueExtendedProperties($singleValueExtendedPropertiesArray);


$result = $graphServiceClient->me()->events()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	subject = "Celebrate Thanksgiving"
	body = @{
		contentType = "HTML"
		content = "Let's get together!"
	}
	start = @{
		dateTime = "2015-11-26T18:00:00"
		timeZone = "Pacific Standard Time"
	}
	end = @{
		dateTime = "2015-11-26T23:00:00"
		timeZone = "Pacific Standard Time"
	}
	attendees = @(
		@{
			emailAddress = @{
				address = "Terrie@contoso.com"
				name = "Terrie Barrera"
			}
			type = "Required"
		}
	)
	singleValueExtendedProperties = @(
		@{
			id = "String {66f5a359-4659-4830-9070-00040ec6ac6e} Name Fun"
			value = "Food"
		}
	)
}

# A UPN can also be used as -UserId.
New-MgUserEvent -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.event import Event
from msgraph.generated.models.item_body import ItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
from msgraph.generated.models.attendee import Attendee
from msgraph.generated.models.email_address import EmailAddress
from msgraph.generated.models.attendee_type import AttendeeType
from msgraph.generated.models.single_value_legacy_extended_property import SingleValueLegacyExtendedProperty
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Event(
	subject = "Celebrate Thanksgiving",
	body = ItemBody(
		content_type = BodyType.Html,
		content = "Let's get together!",
	),
	start = DateTimeTimeZone(
		date_time = "2015-11-26T18:00:00",
		time_zone = "Pacific Standard Time",
	),
	end = DateTimeTimeZone(
		date_time = "2015-11-26T23:00:00",
		time_zone = "Pacific Standard Time",
	),
	attendees = [
		Attendee(
			email_address = EmailAddress(
				address = "Terrie@contoso.com",
				name = "Terrie Barrera",
			),
			type = AttendeeType.Required,
		),
	],
	single_value_extended_properties = [
		SingleValueLegacyExtendedProperty(
			id = "String {66f5a359-4659-4830-9070-00040ec6ac6e} Name Fun",
			value = "Food",
		),
	],
)

result = await graph_client.me.events.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

A successful response is indicated by an `HTTP 201 Created` response code, and includes the new event in the response body, similar to the response from [creating just an event](https://learn.microsoft.com/en-us/graph/api/user-post-events?view=graph-rest-1.0). The response doesn't include any newly created extended properties.

To see the newly created extended property, [get the event expanded with the extended property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-1.0).

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('c71-86a-a0-92-906ba')/events/$entity",
    "@odata.etag": "W/\"oBeN/g==\"",
    "id": "AAMkADI4Yzc5AABVNeEhAAA=",
    "createdDateTime": "2023-06-26T15:46:00.9307807Z",
    "lastModifiedDateTime": "2023-06-26T15:46:02.0775731Z",
    "changeKey": "oBEEg==",
    "categories": [],
    "transactionId": null,
    "originalStartTimeZone": "Pacific Standard Time",
    "originalEndTimeZone": "Pacific Standard Time",
    "iCalUId": "04049ACBF84A7AC7CB34D",
    "reminderMinutesBeforeStart": 15,
    "isReminderOn": true,
    "hasAttachments": false,
    "subject": "Celebrate Thanksgiving",
    "bodyPreview": "Let's get together!",
    "importance": "normal",
    "sensitivity": "normal",
    "isAllDay": false,
    "isCancelled": false,
    "isOrganizer": true,
    "responseRequested": true,
    "seriesMasterId": null,
    "showAs": "busy",
    "type": "singleInstance",
    "webLink": "https://outlook.office365.com/owa/?itemid=AAMkAA%3D&exvsurl=1&path=/calendar/item",
    "onlineMeetingUrl": null,
    "isOnlineMeeting": false,
    "onlineMeetingProvider": "unknown",
    "allowNewTimeProposals": true,
    "occurrenceId": null,
    "isDraft": false,
    "hideAttendees": false,
    "responseStatus": {
        "response": "organizer",
        "time": "0001-01-01T00:00:00Z"
    },
    "body": {
        "contentType": "html",
        "content": "<html><head><meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\"></head><body>Let's get together!</body></html>"
    },
    "start": {
        "dateTime": "2015-11-26T18:00:00.0000000",
        "timeZone": "Pacific Standard Time"
    },
    "end": {
        "dateTime": "2015-11-26T23:00:00.0000000",
        "timeZone": "Pacific Standard Time"
    },
    "location": {
        "displayName": "",
        "locationType": "default",
        "uniqueIdType": "unknown",
        "address": {},
        "coordinates": {}
    },
    "locations": [],
    "recurrence": null,
    "attendees": [
        {
            "type": "required",
            "status": {
                "response": "none",
                "time": "0001-01-01T00:00:00Z"
            },
            "emailAddress": {
                "name": "Terrie Barrera",
                "address": "Terrie@contoso.com"
            }
        }
    ],
    "organizer": {
        "emailAddress": {
            "name": "MOD Administrator",
            "address": "admin@contoso.com"
        }
    },
    "onlineMeeting": null
}
```

### Example 2: Create a single-value extended property for a message

#### Request

The second example creates one single-value extended property for the specified existing message. That extended property is the only element in the **singleValueExtendedProperties** array. The request body includes the following for the extended property:

- **id** specifies the property type as `String`, the GUID, and the property named `Color`.
- **value** specifies `Green` as the value of the `Color` property.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/me/messages/AAMkAGE1M2_bs88AACHsLqWAAA=
Content-Type: application/json

{
  "singleValueExtendedProperties": [
      {
         "id":"String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
         "value":"Green"
      }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new Message
{
	SingleValueExtendedProperties = new List<SingleValueLegacyExtendedProperty>
	{
		new SingleValueLegacyExtendedProperty
		{
			Id = "String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
			Value = "Green",
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Messages["{message-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewMessage()


singleValueLegacyExtendedProperty := graphmodels.NewSingleValueLegacyExtendedProperty()
id := "String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color"
singleValueLegacyExtendedProperty.SetId(&id) 
value := "Green"
singleValueLegacyExtendedProperty.SetValue(&value) 

singleValueExtendedProperties := []graphmodels.SingleValueLegacyExtendedPropertyable {
	singleValueLegacyExtendedProperty,
}
requestBody.SetSingleValueExtendedProperties(singleValueExtendedProperties)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Me().Messages().ByMessageId("message-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Message message = new Message();
LinkedList<SingleValueLegacyExtendedProperty> singleValueExtendedProperties = new LinkedList<SingleValueLegacyExtendedProperty>();
SingleValueLegacyExtendedProperty singleValueLegacyExtendedProperty = new SingleValueLegacyExtendedProperty();
singleValueLegacyExtendedProperty.setId("String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color");
singleValueLegacyExtendedProperty.setValue("Green");
singleValueExtendedProperties.add(singleValueLegacyExtendedProperty);
message.setSingleValueExtendedProperties(singleValueExtendedProperties);
Message result = graphClient.me().messages().byMessageId("{message-id}").patch(message);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const message = {
  singleValueExtendedProperties: [
      {
         id: 'String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color',
         value: 'Green'
      }
    ]
};

await client.api('/me/messages/AAMkAGE1M2_bs88AACHsLqWAAA=')
	.update(message);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Message;
use Microsoft\Graph\Generated\Models\SingleValueLegacyExtendedProperty;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Message();
$singleValueExtendedPropertiesSingleValueLegacyExtendedProperty1 = new SingleValueLegacyExtendedProperty();
$singleValueExtendedPropertiesSingleValueLegacyExtendedProperty1->setId('String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color');
$singleValueExtendedPropertiesSingleValueLegacyExtendedProperty1->setValue('Green');
$singleValueExtendedPropertiesArray []= $singleValueExtendedPropertiesSingleValueLegacyExtendedProperty1;
$requestBody->setSingleValueExtendedProperties($singleValueExtendedPropertiesArray);


$result = $graphServiceClient->me()->messages()->byMessageId('message-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Mail

$params = @{
	singleValueExtendedProperties = @(
		@{
			id = "String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color"
			value = "Green"
		}
	)
}

# A UPN can also be used as -UserId.
Update-MgUserMessage -UserId $userId -MessageId $messageId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.message import Message
from msgraph.generated.models.single_value_legacy_extended_property import SingleValueLegacyExtendedProperty
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Message(
	single_value_extended_properties = [
		SingleValueLegacyExtendedProperty(
			id = "String {66f5a359-4659-4830-9070-00047ec6ac6e} Name Color",
			value = "Green",
		),
	],
)

result = await graph_client.me.messages.by_message_id('message-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

A successful response is indicated by an `HTTP 200 OK` response code, and includes the specified message in the response body, similar to the response from [updating a message](https://learn.microsoft.com/en-us/graph/api/message-update?view=graph-rest-1.0). The response doesn't include the newly created extended property.

To see the newly created extended property, [get the message expanded with the extended property](https://learn.microsoft.com/en-us/graph/api/singlevaluelegacyextendedproperty-get?view=graph-rest-1.0).

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('3cc-ad3-4b9-9a-54')/messages/$entity",
    "@odata.etag": "W/\"CQAAABTiMty\"",
    "id": "AAMkADQzZ1NzItKbS4P8E6VEAAA3LwToAAA=",
    "createdDateTime": "2023-05-12T15:55:56Z",
    "lastModifiedDateTime": "2023-06-23T17:45:43Z",
    "changeKey": "CQAAAAABTiMty",
    "categories": [],
    "receivedDateTime": "2023-05-12T15:55:57Z",
    "sentDateTime": "2023-05-12T15:55:48Z",
    "hasAttachments": false,
    "internetMessageId": "<odspmicro-PlannerDueDate-06c7f00e-6b5f793846-DispatchToRecipients-PreprocessPayload-r0-SendEmail@59C185B>",
    "subject": "You have upcoming tasks due",
    "bodyPreview": "Hi Alex. You have 2 tasks due.        You have upcoming tasksSubmit your expensesIn the plan  Event Plan        5/19/2023Due in 7 daysSubmit your expensesIn the plan  Event Plan        5/19/2023Due in 7 daysView tasks in  Microsoft To ",
    "importance": "normal",
    "parentFolderId": "AQMkc0BAIptLg-wTpUQAAAIBDAAAAA==",
    "conversationId": "AAQkADQzZmJLgzlRSFD0=",
    "conversationIndex": "AQHIUPQ==",
    "isDeliveryReceiptRequested": null,
    "isReadReceiptRequested": false,
    "isRead": false,
    "isDraft": false,
    "webLink": "https://outlook.office365.com/owa/?ItemID=AAP8E6vsurl=1&viewmodel=ReadMessageItem",
    "inferenceClassification": "focused",
    "body": {
        "contentType": "html",
        "content": "<html aria-hidden=\"true\" role=\"presentation\" height=\"1\" width=\"1\"></html>"
    },
    "sender": {
        "emailAddress": {
            "name": "Microsoft on behalf of your organization",
            "address": "noreply@planner.office365.com"
        }
    },
    "from": {
        "emailAddress": {
            "name": "Microsoft on behalf of your organization",
            "address": "noreply@planner.office365.com"
        }
    },
    "toRecipients": [
        {
            "emailAddress": {
                "name": "Alex Wilber",
                "address": "AlexW@contoso.com"
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
