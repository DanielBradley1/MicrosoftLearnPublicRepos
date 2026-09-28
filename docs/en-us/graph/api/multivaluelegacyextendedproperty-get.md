<!-- Source: https://learn.microsoft.com/en-us/graph/api/multivaluelegacyextendedproperty-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# Get multiValueLegacyExtendedProperty

Namespace: microsoft.graph

Get a resource instance that contains a multi-value extended property by using `$expand`.

Using the query parameter `$expand` allows you to get the specified instance expanded with the indicated extended property. This is currently the only way to get the [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) object that represents an extended property.

The following user resources are supported:

- [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0)
- [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0)
- [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0)
- [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0)
- [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0)
- [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0)
- [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0)
- [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0)

As well as the following group resources:

- group [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0)
- group [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0)
- group [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0)

See [Extended properties overview](https://learn.microsoft.com/en-us/graph/api/resources/extended-properties-overview?view=graph-rest-1.0) for more information about when to use open extensions or extended properties, and how to specify extended properties.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Depending on the resource you're getting the extended property from and the permission type \(delegated or application\) you request, the permission specified in the following table is the minimum required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Supported resource | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | Calendars.Read | Calendars.Read | Calendars.Read |
| [contact](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0) | Contacts.Read | Contacts.Read | Contacts.Read |
| [contactFolder](https://learn.microsoft.com/en-us/graph/api/resources/contactfolder?view=graph-rest-1.0) | Contacts.Read | Contacts.Read | Contacts.Read |
| [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Calendars.Read | Calendars.Read | Calendars.Read |
| group [calendar](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0) | Group.Read.All | Not supported | Not supported |
| group [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0) | Group.Read.All | Not supported | Not supported |
| group [post](https://learn.microsoft.com/en-us/graph/api/resources/post?view=graph-rest-1.0) | Group.Read.All | Not supported | Group.Read.All |
| [mailboxFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailboxfolder?view=graph-rest-1.0) | MailboxFolder.Read | Not supported. | MailboxFolder.Read.All |
| [mailboxItem](https://learn.microsoft.com/en-us/graph/api/resources/mailboxitem?view=graph-rest-1.0) | MailboxItem.Read | Not supported. | MailboxItem.Read.All |
| [mailFolder](https://learn.microsoft.com/en-us/graph/api/resources/mailfolder?view=graph-rest-1.0) | Mail.Read | Mail.Read | Mail.Read |
| [message](https://learn.microsoft.com/en-us/graph/api/resources/message?view=graph-rest-1.0) | Mail.Read | Mail.Read | Mail.Read |

## HTTP request

Get a resource instance expanded with the extended property which matches a filter on the **id** property. Make sure you apply [URL encoding](https://www.w3schools.com/tags/ref_urlencode.asp) to the space characters in the filter string.

Get a **message** instance:

```http
GET /me/messages/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/{id|userPrincipalName}/messages/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /me/mailFolders/{id}/messages/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

Get a **mailFolder** instance:

```http
GET /me/mailFolders/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/{id|userPrincipalName}/mailFolders/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

Get an **event** instance:

```http
GET /me/events/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/{id|userPrincipalName}/events/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

Get a **calendar** instance:

```http
GET /me/calendars/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/{id|userPrincipalName}/calendars/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

Get a **contact** instance:

```http
GET /me/contacts/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/{id|userPrincipalName}/contacts/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /me/contactFolders/{id}/contacts/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/{id|userPrincipalName}/contactFolders/{id}/contacts/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

Get a **contactFolder** instance:

```http
GET /me/contactfolders/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /users/{id|userPrincipalName}/contactFolders/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

Get a **mailboxItem** instance:

```http
GET /admin/exchange/mailboxes/{mailboxId}/folders/{mailboxFolderId}/items?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /admin/exchange/mailboxes/{mailboxId}/folders/{mailboxFolderId}/items/{mailboxItemId}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

Get a **mailboxFolder** instance:

```http
GET /admin/exchange/mailboxes/{mailboxId}/folders?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /admin/exchange/mailboxes/{mailboxId}/folders/{mailboxFolderId}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

Get a group **event** instance:

```http
GET /groups/{id}/events/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

Get a group **post** instance:

```http
GET /groups/{id}/threads/{id}/posts/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
GET /groups/{id}/conversations/{id}/threads/{id}/posts/{id}?$expand=multiValueExtendedProperties($filter=id eq '{id_value}')
```

## Path parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| id\_value | String | The ID of the extended property to match. It must follow one of the supported formats. See [Outlook extended properties overview](https://learn.microsoft.com/en-us/graph/api/resources/extended-properties-overview?view=graph-rest-1.0) for more information. Required. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code.

The response body includes an object representing the requested resource instance, expanded with the matching [multiValueLegacyExtendedProperty](https://learn.microsoft.com/en-us/graph/api/resources/multivaluelegacyextendedproperty?view=graph-rest-1.0) object.

## Example

### Request

This example gets and expands the specified event by including a multi-value extended property. The filter returns the extended property that has its **id** matching the string `StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation` \(with URL encoding removed here for ease of reading\).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/v1.0/me/events/AAMkADI0NzVmYjQ0LWQyZTItNDIxYS1iMWE2LTIyZGJiOGM0N2YzMQBGAAAAAABaZwRaNsIxTp0lpjY1il_IBwAXjnwa91gDSKOqCnaDInDMAAAAAAENAAAXjnwa91gDSKOqCnaDInDMAAAtgOgIAAA=?$expand=multiValueExtendedProperties($filter=id%20eq%20'StringArray%20{66f5a359-4659-4830-9070-00050ec6ac6e}%20Name%20Recreation')
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Events["{event-id}"].GetAsync((requestConfiguration) =>
{
	requestConfiguration.QueryParameters.Expand = new string []{ "multiValueExtendedProperties($filter=id eq 'StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation')" };
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  //other-imports
)

requestParameters := &graphusers.EventsItemRequestBuilderGetQueryParameters{
	Expand: [] string {"multiValueExtendedProperties($filter=id eq 'StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation')"},
}
configuration := &graphusers.EventsItemRequestBuilderGetRequestConfiguration{
	QueryParameters: requestParameters,
}

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
events, err := graphClient.Me().Events().ByEventId("event-id").Get(context.Background(), configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Event result = graphClient.me().events().byEventId("{event-id}").get(requestConfiguration -> {
	requestConfiguration.queryParameters.expand = new String []{"multiValueExtendedProperties($filter=id eq 'StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation')"};
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let event = await client.api('/me/events/AAMkADI0NzVmYjQ0LWQyZTItNDIxYS1iMWE2LTIyZGJiOGM0N2YzMQBGAAAAAABaZwRaNsIxTp0lpjY1il_IBwAXjnwa91gDSKOqCnaDInDMAAAAAAENAAAXjnwa91gDSKOqCnaDInDMAAAtgOgIAAA=')
	.expand('multiValueExtendedProperties($filter=id eq \'StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation\')')
	.get();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Events\Item\EventItemRequestBuilderGetRequestConfiguration;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestConfiguration = new EventItemRequestBuilderGetRequestConfiguration();
$queryParameters = EventItemRequestBuilderGetRequestConfiguration::createQueryParameters();
$queryParameters->expand = ["multiValueExtendedProperties(\$filter=id eq 'StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation')"];
$requestConfiguration->queryParameters = $queryParameters;


$result = $graphServiceClient->me()->events()->byEventId('event-id')->get($requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

# A UPN can also be used as -UserId.
Get-MgUserEvent -UserId $userId -EventId $eventId -ExpandProperty "multiValueExtendedProperties(`$filter=id eq 'StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation')" 
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.events.item.event_item_request_builder import EventItemRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
query_params = EventItemRequestBuilder.EventItemRequestBuilderGetQueryParameters(
		expand = ["multiValueExtendedProperties($filter=id eq 'StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation')"],
)

request_configuration = RequestConfiguration(
query_parameters = query_params,
)

result = await graph_client.me.events.by_event_id('event-id').get(request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The response body includes all the properties of the specified event and extended property returned from the filter.

Note: The **event** object shown here is truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('4d29052a-70e8-4251-a7de-542b522cdf25')/events(multiValueExtendedProperties())/$entity",
    "@odata.etag": "W/\"F458GvdYA0ijqgp2gyJwzAAALXs9wA==\"",
    "id": "AAMkADI0NzVmYjQ0LWQyZTItNDIxYS1iMWE2LTIyZGJiOGM0N2YzMQBGAAAAAABaZwRaNsIxTp0lpjY1il_IBwAXjnwa91gDSKOqCnaDInDMAAAAAAENAAAXjnwa91gDSKOqCnaDInDMAAAtgOgIAAA=",
    "createdDateTime": "2023-06-13T23:13:17.305298Z",
    "lastModifiedDateTime": "2023-06-13T23:15:17.761448Z",
    "changeKey": "F458GvdYA0ijqgp2gyJwzAAALXs9wA==",
    "categories": [],
    "transactionId": null,
    "originalStartTimeZone": "Pacific Standard Time",
    "originalEndTimeZone": "Pacific Standard Time",
    "iCalUId": "040000008200E00074C5B7101A82E00800000000742AF7A24C9ED901000000000000000010000000C525CA622368B44D89B3B78E4B44A92A",
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
    "webLink": "https://outlook.office365.com/owa/?itemid=AAMkADI0NzVmYjQ0LWQyZTItNDIxYS1iMWE2LTIyZGJiOGM0N2YzMQBGAAAAAABaZwRaNsIxTp0lpjY1il%2BIBwAXjnwa91gDSKOqCnaDInDMAAAAAAENAAAXjnwa91gDSKOqCnaDInDMAAAtgOgIAAA%3D&exvsurl=1&path=/calendar/item",
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
        "dateTime": "2015-11-26T17:00:00.0000000",
        "timeZone": "UTC"
    },
    "end": {
        "dateTime": "2015-11-30T05:00:00.0000000",
        "timeZone": "UTC"
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
    "onlineMeeting": null,
    "multiValueExtendedProperties": [
        {
            "id": "StringArray {66f5a359-4659-4830-9070-00050ec6ac6e} Name Recreation",
            "value": [
                "Food",
                "Hiking",
                "Swimming"
            ]
        }
    ],
    "calendar@odata.associationLink": "https://graph.microsoft.com/v1.0/users('4d29052a-70e8-4251-a7de-542b522cdf25')/calendars('AAMkADI0NzVmYjQ0LWQyZTItNDIxYS1iMWE2LTIyZGJiOGM0N2YzMQAuAAAAAABaZwRaNsIxTp0lpjY1il_IAQAXjnwa91gDSKOqCnaDInDMAAAAAAENAAA=')/$ref",
    "calendar@odata.navigationLink": "https://graph.microsoft.com/v1.0/users('4d29052a-70e8-4251-a7de-542b522cdf25')/calendars('AAMkADI0NzVmYjQ0LWQyZTItNDIxYS1iMWE2LTIyZGJiOGM0N2YzMQAuAAAAAABaZwRaNsIxTp0lpjY1il_IAQAXjnwa91gDSKOqCnaDInDMAAAAAAENAAA=')"
}
```
