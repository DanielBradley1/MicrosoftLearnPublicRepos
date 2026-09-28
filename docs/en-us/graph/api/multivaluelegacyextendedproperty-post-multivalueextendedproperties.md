<!-- Source: https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-post-multivalueextendedproperties?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create multi-value extended property

Namespace: microsoft.graph

Create one or more multi-value extended properties in a new or existing instance of a resource.

The following user resources are supported:

- [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0)
- [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0)
- [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0)
- [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0)
- [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0)
- [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0)
- [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0)
- [note](https://learn.microsoft.com/en-us/graph/api/resources/note?view=graph-rest-1.0)

The following group resources are supported:

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

To create one or more extended properties in a *new* resource instance, use the same REST request as creating the instance, and include the properties of the new resource instance *and extended property* in the request body. Some resources support creation in more than one way. For more information on creating these resource instances, see the corresponding topics for creating a [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0), [mailFolder](https://learn.microsoft.com/en-us/graph/api/user-post-mailfolders?view=graph-rest-1.0), [event](https://learn.microsoft.com/en-us/graph/api/user-post-events?view=graph-rest-1.0), [calendar](https://learn.microsoft.com/en-us/graph/api/user-post-calendars?view=graph-rest-1.0), [contact](https://learn.microsoft.com/en-us/graph/api/user-post-contacts?view=graph-rest-1.0), [contactFolder](https://learn.microsoft.com/en-us/graph/api/user-post-contactfolders?view=graph-rest-1.0), [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/mailbox-post-folders?view=graph-rest-1.0), [group event](https://learn.microsoft.com/en-us/graph/api/group-post-events?view=graph-rest-1.0), and [group post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0).

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

Provide a JSON body of each [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) object in the **multiValueExtendedProperties** collection property of the resource instance.

| Property | Type | Description |
| :--- | :--- | :--- |
| multiValueExtendedProperties | [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) collection | An array of one or more multi-valued extended properties. |
| id | String | For each property in the **multiValueExtendedProperties** collection, specify this to identify the property. It must follow one of the supported formats. See [Outlook extended properties overview](https://learn.microsoft.com/en-us/graph/api/resources/extended-properties-overview?view=graph-rest-1.0) for more information. Required. |
| value | string | For each property in the **multiValueExtendedProperties** collection, specify the property value. Required. |

When creating an extended property in a *new* resource instance, in addition to the new **multiValueExtendedProperties** collection, provide a JSON representation of that resource instance as well \(that is, a [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0), [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0), [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0), etc.\).

## Response

#### Response code

An operation successful in creating an extended property in a new resource instance returns `201 Created`, except in a new group post, depending on the method used, the operation can return `200 OK` or `202 Accepted`.

In an existing resource instance, a successful create operation returns `200 OK`.

#### Response body

When creating an extended property in a supported resource other than [group post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0), the response includes only the new or existing instance but not the new extended property. To see the newly created extended property, [get the instance expanded with the extended property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-1.0).

When creating an extended property in a *new* group post, the response includes only a response code but not the new post nor the extended property. You can't create an extended property in an existing group post.

## Examples

### Example 1: Create multi-value extended property for event

#### Request

The first example creates a multi-value extended property in a new event all in the same POST operation. Apart from the properties you'd normally include for a new event, the request body includes the **multiValueExtendedProperties** collection that contains one extended property. The request body includes the following for that multi-value extended property:

- **id** which specifies the property as an array of strings with the specified GUID and the name `Recreation`.
- **value** which specifies `Recreation` as an array of 3 string values, `["Food", "Hiking", "Swimming"]`.

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
  "subject": "Family reunion",
  "body": {
    "contentType": "HTML",
    "content": "Let's get together this Thanksgiving!"
  },
  "start": {
      "dateTime": "2015-11-26T09:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "end": {
      "dateTime": "2015-11-29T21:00:00",
      "timeZone": "Pacific Standard Time"
  },
  "attendees": [
    {
      "emailAddress": {
        "address": "Terrie@contoso.com",
        "name": "Terrie Barrera"
      },
      "type": "Required"
    },
    {
      "emailAddress": {
        "address": "Lauren@contoso.com",
        "name": "Lauren Solis"
      },
      "type": "Required"
    }
  ],
  "multiValueExtendedProperties": [
     {
           "id":"StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation",
           "value": ["Food", "Hiking", "Swimming"]
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
	Subject = "Family reunion",
	Body = new ItemBody
	{
		ContentType = BodyType.Html,
		Content = "Let's get together this Thanksgiving!",
	},
	Start = new DateTimeTimeZone
	{
		DateTime = "2015-11-26T09:00:00",
		TimeZone = "Pacific Standard Time",
	},
	End = new DateTimeTimeZone
	{
		DateTime = "2015-11-29T21:00:00",
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
		new Attendee
		{
			EmailAddress = new EmailAddress
			{
				Address = "Lauren@contoso.com",
				Name = "Lauren Solis",
			},
			Type = AttendeeType.Required,
		},
	},
	MultiValueExtendedProperties = new List<MultiValueLegacyExtendedProperty>
	{
		new MultiValueLegacyExtendedProperty
		{
			Id = "StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation",
			Value = new List<string>
			{
				"Food",
				"Hiking",
				"Swimming",
			},
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
subject := "Family reunion"
requestBody.SetSubject(&subject) 
body := graphmodels.NewItemBody()
contentType := graphmodels.HTML_BODYTYPE 
body.SetContentType(&contentType) 
content := "Let's get together this Thanksgiving!"
body.SetContent(&content) 
requestBody.SetBody(body)
start := graphmodels.NewDateTimeTimeZone()
dateTime := "2015-11-26T09:00:00"
start.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
start.SetTimeZone(&timeZone) 
requestBody.SetStart(start)
end := graphmodels.NewDateTimeTimeZone()
dateTime := "2015-11-29T21:00:00"
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
attendee1 := graphmodels.NewAttendee()
emailAddress := graphmodels.NewEmailAddress()
address := "Lauren@contoso.com"
emailAddress.SetAddress(&address) 
name := "Lauren Solis"
emailAddress.SetName(&name) 
attendee1.SetEmailAddress(emailAddress)
type := graphmodels.REQUIRED_ATTENDEETYPE 
attendee1.SetType(&type) 

attendees := []graphmodels.Attendeeable {
	attendee,
	attendee1,
}
requestBody.SetAttendees(attendees)


multiValueLegacyExtendedProperty := graphmodels.NewMultiValueLegacyExtendedProperty()
id := "StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation"
multiValueLegacyExtendedProperty.SetId(&id) 
value := []string {
	"Food",
	"Hiking",
	"Swimming",
}
multiValueLegacyExtendedProperty.SetValue(value)

multiValueExtendedProperties := []graphmodels.MultiValueLegacyExtendedPropertyable {
	multiValueLegacyExtendedProperty,
}
requestBody.SetMultiValueExtendedProperties(multiValueExtendedProperties)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
events, err := graphClient.Me().Events().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Event event = new Event();
event.setSubject("Family reunion");
ItemBody body = new ItemBody();
body.setContentType(BodyType.Html);
body.setContent("Let's get together this Thanksgiving!");
event.setBody(body);
DateTimeTimeZone start = new DateTimeTimeZone();
start.setDateTime("2015-11-26T09:00:00");
start.setTimeZone("Pacific Standard Time");
event.setStart(start);
DateTimeTimeZone end = new DateTimeTimeZone();
end.setDateTime("2015-11-29T21:00:00");
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
Attendee attendee1 = new Attendee();
EmailAddress emailAddress1 = new EmailAddress();
emailAddress1.setAddress("Lauren@contoso.com");
emailAddress1.setName("Lauren Solis");
attendee1.setEmailAddress(emailAddress1);
attendee1.setType(AttendeeType.Required);
attendees.add(attendee1);
event.setAttendees(attendees);
LinkedList<MultiValueLegacyExtendedProperty> multiValueExtendedProperties = new LinkedList<MultiValueLegacyExtendedProperty>();
MultiValueLegacyExtendedProperty multiValueLegacyExtendedProperty = new MultiValueLegacyExtendedProperty();
multiValueLegacyExtendedProperty.setId("StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation");
LinkedList<String> value = new LinkedList<String>();
value.add("Food");
value.add("Hiking");
value.add("Swimming");
multiValueLegacyExtendedProperty.setValue(value);
multiValueExtendedProperties.add(multiValueLegacyExtendedProperty);
event.setMultiValueExtendedProperties(multiValueExtendedProperties);
Event result = graphClient.me().events().post(event);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const event = {
  subject: 'Family reunion',
  body: {
    contentType: 'HTML',
    content: 'Let\'s get together this Thanksgiving!'
  },
  start: {
      dateTime: '2015-11-26T09:00:00',
      timeZone: 'Pacific Standard Time'
  },
  end: {
      dateTime: '2015-11-29T21:00:00',
      timeZone: 'Pacific Standard Time'
  },
  attendees: [
    {
      emailAddress: {
        address: 'Terrie@contoso.com',
        name: 'Terrie Barrera'
      },
      type: 'Required'
    },
    {
      emailAddress: {
        address: 'Lauren@contoso.com',
        name: 'Lauren Solis'
      },
      type: 'Required'
    }
  ],
  multiValueExtendedProperties: [
     {
           id: 'StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation',
           value: ['Food', 'Hiking', 'Swimming']
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
use Microsoft\Graph\Generated\Models\MultiValueLegacyExtendedProperty;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Event();
$requestBody->setSubject('Family reunion');
$body = new ItemBody();
$body->setContentType(new BodyType('hTML'));
$body->setContent('Let\'s get together this Thanksgiving!');
$requestBody->setBody($body);
$start = new DateTimeTimeZone();
$start->setDateTime('2015-11-26T09:00:00');
$start->setTimeZone('Pacific Standard Time');
$requestBody->setStart($start);
$end = new DateTimeTimeZone();
$end->setDateTime('2015-11-29T21:00:00');
$end->setTimeZone('Pacific Standard Time');
$requestBody->setEnd($end);
$attendeesAttendee1 = new Attendee();
$attendeesAttendee1EmailAddress = new EmailAddress();
$attendeesAttendee1EmailAddress->setAddress('Terrie@contoso.com');
$attendeesAttendee1EmailAddress->setName('Terrie Barrera');
$attendeesAttendee1->setEmailAddress($attendeesAttendee1EmailAddress);
$attendeesAttendee1->setType(new AttendeeType('required'));
$attendeesArray []= $attendeesAttendee1;
$attendeesAttendee2 = new Attendee();
$attendeesAttendee2EmailAddress = new EmailAddress();
$attendeesAttendee2EmailAddress->setAddress('Lauren@contoso.com');
$attendeesAttendee2EmailAddress->setName('Lauren Solis');
$attendeesAttendee2->setEmailAddress($attendeesAttendee2EmailAddress);
$attendeesAttendee2->setType(new AttendeeType('required'));
$attendeesArray []= $attendeesAttendee2;
$requestBody->setAttendees($attendeesArray);

$multiValueExtendedPropertiesMultiValueLegacyExtendedProperty1 = new MultiValueLegacyExtendedProperty();
$multiValueExtendedPropertiesMultiValueLegacyExtendedProperty1->setId('StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation');
$multiValueExtendedPropertiesMultiValueLegacyExtendedProperty1->setValue(['Food', 'Hiking', 'Swimming', ]);
$multiValueExtendedPropertiesArray []= $multiValueExtendedPropertiesMultiValueLegacyExtendedProperty1;
$requestBody->setMultiValueExtendedProperties($multiValueExtendedPropertiesArray);


$result = $graphServiceClient->me()->events()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	subject = "Family reunion"
	body = @{
		contentType = "HTML"
		content = "Let's get together this Thanksgiving!"
	}
	start = @{
		dateTime = "2015-11-26T09:00:00"
		timeZone = "Pacific Standard Time"
	}
	end = @{
		dateTime = "2015-11-29T21:00:00"
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
		@{
			emailAddress = @{
				address = "Lauren@contoso.com"
				name = "Lauren Solis"
			}
			type = "Required"
		}
	)
	multiValueExtendedProperties = @(
		@{
			id = "StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation"
			value = @(
			"Food"
		"Hiking"
	"Swimming"
)
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
from msgraph.generated.models.multi_value_legacy_extended_property import MultiValueLegacyExtendedProperty
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Event(
	subject = "Family reunion",
	body = ItemBody(
		content_type = BodyType.Html,
		content = "Let's get together this Thanksgiving!",
	),
	start = DateTimeTimeZone(
		date_time = "2015-11-26T09:00:00",
		time_zone = "Pacific Standard Time",
	),
	end = DateTimeTimeZone(
		date_time = "2015-11-29T21:00:00",
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
		Attendee(
			email_address = EmailAddress(
				address = "Lauren@contoso.com",
				name = "Lauren Solis",
			),
			type = AttendeeType.Required,
		),
	],
	multi_value_extended_properties = [
		MultiValueLegacyExtendedProperty(
			id = "StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation",
			value = [
				"Food",
				"Hiking",
				"Swimming",
			],
		),
	],
)

result = await graph_client.me.events.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('4d29052a-70e8-4251-a7de-542b522cdf25')/events/$entity",
  "@odata.etag": "W/\"F458GvdYA0ijqgp2gyJwzAAAOCEJmw==\"",
  "id": "AAMkADI0NzVmYjQ0LWQyZTItNDIxYS1iMWE2LTIyZGJiOGM0N2YzMQBGAAAAAABaZwRaNsIxTp0lpjY1il_IBwAXjnwa91gDSKOqCnaDInDMAAAAAAENAAAXjnwa91gDSKOqCnaDInDMAAA4KToJAAA=",
  "createdDateTime": "2023-06-23T00:52:52.5418Z",
  "lastModifiedDateTime": "2023-06-23T00:52:53.570523Z",
  "changeKey": "F458GvdYA0ijqgp2gyJwzAAAOCEJmw==",
  "categories": [],
  "transactionId": null,
  "originalStartTimeZone": "Pacific Standard Time",
  "originalEndTimeZone": "Pacific Standard Time",
  "iCalUId": "040000008200E00074C5B7101A82E008000000001076340A6DA5D9010000000000000000100000003EE8BF77931D7D40B835A528EFD465E8",
  "reminderMinutesBeforeStart": 15,
  "isReminderOn": true,
  "hasAttachments": false,
  "subject": "Family reunion",
  "bodyPreview": "Let's get together this Thanksgiving!",
  "importance": "normal",
  "sensitivity": "normal",
  "isAllDay": false,
  "isCancelled": false,
  "isOrganizer": true,
  "responseRequested": true,
  "seriesMasterId": null,
  "showAs": "busy",
  "type": "singleInstance",
  "webLink": "https://outlook.office365.com/owa/?itemid=AAMkADI0NzVmYjQ0LWQyZTItNDIxYS1iMWE2LTIyZGJiOGM0N2YzMQBGAAAAAABaZwRaNsIxTp0lpjY1il%2BIBwAXjnwa91gDSKOqCnaDInDMAAAAAAENAAAXjnwa91gDSKOqCnaDInDMAAA4KToJAAA%3D&exvsurl=1&path=/calendar/item",
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
      "content": "<html><head><meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\"></head><body>Let's get together this Thanksgiving!</body></html>"
  },
  "start": {
      "dateTime": "2015-11-26T09:00:00.0000000",
      "timeZone": "Pacific Standard Time"
  },
  "end": {
      "dateTime": "2015-11-29T21:00:00.0000000",
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
      },
      {
          "type": "required",
          "status": {
              "response": "none",
              "time": "0001-01-01T00:00:00Z"
          },
          "emailAddress": {
              "name": "Lauren Solis",
              "address": "Lauren@contoso.com"
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

A successful response is indicated by an `HTTP 201 Created` response code, and includes the new event in the response body, similar to the response from [creating just an event](https://learn.microsoft.com/en-us/graph/api/user-post-events?view=graph-rest-1.0). The response doesn't include any newly created extended properties.

To see the newly created extended property, [get the event expanded with the extended property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-1.0).

### Example 2: Create multi-value extended properties for message

#### Request

The second example creates one multi-value extended property for the specified message. That extended property is the only element in the **multiValueExtendedProperties** collection. The request body includes the following for the extended property:

- **id** specifies the property as an array of strings with the specified GUID and the name `Palette`.
- **value** specifies `Palette` as an array of 3 string values, `["Green", "Aqua", "Blue"]`.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/v1.0/me/messages/AAMkAGE1M2_as77AACHsLrBBBA=
Content-Type: application/json

{
  "multiValueExtendedProperties": [
      {
         "id":"StringArray {66f5a359-4659-4830-9070-00049ec6ac6e} Name Palette",
         "value":["Green", "Aqua", "Blue"]
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
	MultiValueExtendedProperties = new List<MultiValueLegacyExtendedProperty>
	{
		new MultiValueLegacyExtendedProperty
		{
			Id = "StringArray {66f5a359-4659-4830-9070-00049ec6ac6e} Name Palette",
			Value = new List<string>
			{
				"Green",
				"Aqua",
				"Blue",
			},
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


multiValueLegacyExtendedProperty := graphmodels.NewMultiValueLegacyExtendedProperty()
id := "StringArray {66f5a359-4659-4830-9070-00049ec6ac6e} Name Palette"
multiValueLegacyExtendedProperty.SetId(&id) 
value := []string {
	"Green",
	"Aqua",
	"Blue",
}
multiValueLegacyExtendedProperty.SetValue(value)

multiValueExtendedProperties := []graphmodels.MultiValueLegacyExtendedPropertyable {
	multiValueLegacyExtendedProperty,
}
requestBody.SetMultiValueExtendedProperties(multiValueExtendedProperties)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
messages, err := graphClient.Me().Messages().ByMessageId("message-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Message message = new Message();
LinkedList<MultiValueLegacyExtendedProperty> multiValueExtendedProperties = new LinkedList<MultiValueLegacyExtendedProperty>();
MultiValueLegacyExtendedProperty multiValueLegacyExtendedProperty = new MultiValueLegacyExtendedProperty();
multiValueLegacyExtendedProperty.setId("StringArray {66f5a359-4659-4830-9070-00049ec6ac6e} Name Palette");
LinkedList<String> value = new LinkedList<String>();
value.add("Green");
value.add("Aqua");
value.add("Blue");
multiValueLegacyExtendedProperty.setValue(value);
multiValueExtendedProperties.add(multiValueLegacyExtendedProperty);
message.setMultiValueExtendedProperties(multiValueExtendedProperties);
Message result = graphClient.me().messages().byMessageId("{message-id}").patch(message);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const message = {
  multiValueExtendedProperties: [
      {
         id: 'StringArray {66f5a359-4659-4830-9070-00049ec6ac6e} Name Palette',
         value: ['Green', 'Aqua', 'Blue']
      }
    ]
};

await client.api('/me/messages/AAMkAGE1M2_as77AACHsLrBBBA=')
	.update(message);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\Message;
use Microsoft\Graph\Generated\Models\MultiValueLegacyExtendedProperty;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new Message();
$multiValueExtendedPropertiesMultiValueLegacyExtendedProperty1 = new MultiValueLegacyExtendedProperty();
$multiValueExtendedPropertiesMultiValueLegacyExtendedProperty1->setId('StringArray {66f5a359-4659-4830-9070-00049ec6ac6e} Name Palette');
$multiValueExtendedPropertiesMultiValueLegacyExtendedProperty1->setValue(['Green', 'Aqua', 'Blue', 	]);
$multiValueExtendedPropertiesArray []= $multiValueExtendedPropertiesMultiValueLegacyExtendedProperty1;
$requestBody->setMultiValueExtendedProperties($multiValueExtendedPropertiesArray);


$result = $graphServiceClient->me()->messages()->byMessageId('message-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Mail

$params = @{
	multiValueExtendedProperties = @(
		@{
			id = "StringArray {66f5a359-4659-4830-9070-00049ec6ac6e} Name Palette"
			value = @(
			"Green"
		"Aqua"
	"Blue"
)
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
from msgraph.generated.models.multi_value_legacy_extended_property import MultiValueLegacyExtendedProperty
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = Message(
	multi_value_extended_properties = [
		MultiValueLegacyExtendedProperty(
			id = "StringArray {66f5a359-4659-4830-9070-00049ec6ac6e} Name Palette",
			value = [
				"Green",
				"Aqua",
				"Blue",
			],
		),
	],
)

result = await graph_client.me.messages.by_message_id('message-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

A successful response is indicated by an `HTTP 200 OK` response code, and includes the specified message in the response body, similar to the response from [updating a message](https://learn.microsoft.com/en-us/graph/api/message-update?view=graph-rest-1.0). The response doesn't include the newly created extended property.

To see the newly created extended property, [get the message expanded with the extended property](https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-1.0).

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('c77f324266ba')/messages/$entity",
    "@odata.etag": "W/\"FwAAABYBVGD/o\"",
    "id": "AAMkADI4YzgwfyKAAA=",
    "createdDateTime": "2023-06-26T15:46:05Z",
    "lastModifiedDateTime": "2023-06-28T23:28:50Z",
    "changeKey": "FwAAGSOkFBVGD/o",
    "categories": [],
    "receivedDateTime": "2023-06-26T15:46:05Z",
    "sentDateTime": "2023-06-26T15:46:02Z",
    "hasAttachments": false,
    "internetMessageId": "<1c55OUTLOOK.COM>",
    "subject": "Undeliverable: Celebrate Thanksgiving",
    "bodyPreview": "Delivery has failed to these recipients or groups:Terrie@contoso.comYour message wasn't delivered because the recipient's email provider rejected it.Diagnostic information for administrators:Generating server: CYYP2AM",
    "importance": "normal",
    "parentFolderId": "AAMkADI4YzgwEMAAA=",
    "conversationId": "AAQkADI4Yzej5xL5tI=",
    "conversationIndex": "AQHZq6PnEvm0g==",
    "isDeliveryReceiptRequested": null,
    "isReadReceiptRequested": false,
    "isRead": false,
    "isDraft": false,
    "webLink": "https://outlook.office365.com/owa/?ItemID=AAMQ50XGSOkFdc5AABVNfyKAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
    "inferenceClassification": "focused",
    "body": {
        "contentType": "html",
        "content": "<html><head><meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\"></head><body><p><b><font color=\"#000066\" size=\"3\" face=\"Arial\">Delivery has failed to these recipients or groups:</font></b></p><font color=\"#000000\" size=\"2\" face=\"Tahoma\"><p><a href=\"mailto:Terrie@contoso.com\">Terrie@contoso.com</a><br></font><font color=\"#000000\" size=\"3\" face=\"Arial\">Your message wasn't delivered because the recipient's email provider rejected it.<br></font><font color=\"#000000\" size=\"2\" face=\"Tahoma\"><br></p></font><br><br><br><br><br><br><font color=\"#808080\" size=\"2\" face=\"Tahoma\"><p><b>Diagnostic information for administrators:</b></p><p>Generating server: CYYP223MB0786.NAMP223.PROD.OUTLOOK.COM<br></p><p>Terrie@contoso.com<br>Remote server returned '550 5.7.501 Service unavailable. Spam abuse detected from IP range. For more information please go to http://go.microsoft.com/fwlink/?LinkId=526653. S(2017052602) [SJ1P223MB0482.NAMP223.PROD.OUTLOOK.COM 2023-06-26T15:46:02.597Z 08DB747F4B5EA12D]'<br></p><p>Original message headers:</p><pre>Received: from CYYP223MB0786.NAMP223.PROD.OUTLOOK.COM ([fe80::f789:3002:5514:2e9d]) by CYYP223MB0786.NAMP223.PROD.OUTLOOK.COM ([fe80::f789:3002:5514:2e9d%3]) with mapi id 15.20.6521.024; Mon, 26 Jun 2023 15:46:02 +0000MIME-Version: 1.0Content-Type: text/plainDate: Mon, 26 Jun 2023 15:46:02 +0000Message-ID:&lt;CYYP223MB078658B6CCF8BDDCC31FA5E6AC26A@CYYP223MB0786.NAMP223.PROD.OUTLOOK.COM&gt;Subject: Celebrate Thanksgiving</pre></font></body></html>"
    },
    "sender": {
        "emailAddress": {
            "name": "Microsoft Outlook",
            "address": "MicrosoftExchange329e71ec88ae4615bbc36ab6ce41109e@contoso.com"
        }
    },
    "from": {
        "emailAddress": {
            "name": "Microsoft Outlook",
            "address": "MicrosoftExchange329e71ec88ae4615bbc36ab6ce41109e@contoso.com"
        }
    },
    "toRecipients": [
        {
            "emailAddress": {
                "name": "Terrie@contoso.com",
                "address": "Terrie@contoso.com"
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
