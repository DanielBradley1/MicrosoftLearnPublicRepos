<!-- Source: https://learn.microsoft.com/en-us/graph/outlook-share-or-delegate-calendar -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Share or delegate a calendar in Outlook

In Outlook, a calendar owner can share the calendar with another user. The owner can specify which information in non-private events is viewable, and can give write access to the calendar to users in the same organization.

The owner can also delegate another user to manage meetings in the owner's *primary* calendar. Delegates are share recipients who can view all information in and have write access to non-private events. They also receive meeting requests and responses, and respond to meeting requests on behalf of the owner. Additionally, the owner can give explicit permissions to delegates to view the owner's *private* events on the calendar.

Before calendar sharing or delegation can take effect, the owner sends a share recipient or delegate an invitation, and the share recipient or delegate accepts the invitation, or, explicitly adds the shared or delegated calendar for access. The invitation and adding a shared or delegated calendar occur in an Outlook client.

After sharing or delegation is set up in Outlook, apps can then use the Microsoft Graph API to manage the sharing and delegation.

The rest of this article is based on the following example scenario:

- Alex Wilber has delegated Megan Bowen to his primary calendar, and also permitted Megan to view private events in that calendar.
- Alex shared a "Kids parties" calendar with Adele Vance and Megan Bowen, and gave both Adele and Megan `read` permissions to all the details of non-private events on the "Kids parties" calendar, and free/busy status for private events.

This article describes programmatically carrying out the following tasks with a shared or delegated calendar:

- [Get calendar information about share recipients, delegates, and allowed permissions, and update individual permissions](#get-calendar-information-about-share-recipients-and-delegates-and-update-individual-permissions)
- [Get the properties that describe the sharing or delegation of the calendar](#get-properties-of-a-shared-or-delegated-calendar).
- [Get or set mailbox setting to receive meeting requests and responses for a delegated calendar](#get-or-set-mailbox-setting-to-receive-meeting-requests-and-responses).
- [Delete a share recipient or delegate of a calendar](#delete-a-sharee-or-delegate-of-a-calendar).

Apps can also do the following using API that is generally available:

- [Get shared or delegated Outlook calendar or its events](https://learn.microsoft.com/en-us/graph/outlook-get-shared-events-calendars)
- [Create Outlook events in a shared or delegated calendar](https://learn.microsoft.com/en-us/graph/outlook-create-event-in-shared-delegated-calendar)

Note

The properties and API for calendar sharing and delegating as described in this topic are currently available in the v1.0 endpoint, with the exception of the calendar properties **isShared** and **isSharedWithMe**. These two properties are exposed in only the beta endpoint.

## Get calendar information about share recipients and delegates, and update individual permissions

In this section:

- [Calendar owner: Get sharing or delegation information and permissions](#calendar-owner-get-sharing-or-delegation-information-and-permissions)
- [Calendar owner: Update permissions for an existing share recipient or delegate on a calendar](#calendar-owner-update-permissions-for-an-existing-share-recipient-or-delegate-on-a-calendar)

Each calendar is associated with a collection of [calendarPermission](https://learn.microsoft.com/en-us/graph/api/resources/calendarpermission) objects, each of which describes a share recipient or delegate and the associated permission that the calendar owner has set up. The [calendarRoleType](https://learn.microsoft.com/en-us/graph/api/resources/calendarpermission#calendarroletype-values) enumeration defines the range of permissions that Microsoft Graph supports:

- `none` This value applies to only `My Organization` which doesn't have any permissions to the calendar. It doesn't apply to individual users, as only users with permissions are associated with a **calendarPermission** object for the calendar.
- `freeBusyRead` The share recipient can view the owner's free/busy status, but not other details on the calendar.
- `limitedRead` The share recipient can view the owner's free/busy status, and the titles and locations of non-private events on the calendar.
- `read` The share recipient can view the owner's free/busy status in private events, and all the details of non-private events on the calendar.
- `write` The share recipient can view the owner's free/busy status in private events, and can view all the details and edit \(create, update, or delete\) non-private events on the calendar.
- `delegateWithoutPrivateEventAccess` The *delegate* can view the owner's free/busy status in private events, and has `write` access to non-private events on the calendar.
- `delegateWithPrivateEventAccess` The *delegate* can view details of the owner's private and non-private events, and has `write` access to all the events on the calendar.

The primary calendar of a user is always shared with "My Organization", which represents the users in the same organization as the owner. By default, they can read the owner's free/busy status on that calendar and have the `freeBusyRead` permission.

### Calendar owner: Get sharing or delegation information and permissions

This example shows with the consent of Alex or administrator, how to get the **calendarPermission** objects associated with Alex' primary calendar. The request returns two such permission objects:

- The first **calendarPermission** object is assigned to the delegate, Megan, and has the following property values:

  - **isRemovable** is set to true, providing Alex the option to cancel the delegation.
  - **isInsideOrganization** is true as only users in the same organization can be delegates.
  - **role** for Megan is `delegateWithPrivateEventAccess`, as set up by Alex.
  - **allowedRoles** includes the role types `delegateWithoutPrivateEventAccess` and `delegateWithPrivateEventAccess` that support delegation.
  - **emailAddress** specifies Megan.

- The second **calendarPermission** object is a default object assigned to "My Organization", and has the following property values:

  - **isRemovable** is set to false, since the primary calendar is always shared with the owner's organization.
  - **isInsideOrganization** is true.
  - **role** is `freeBusyRead`, the default setting for "My Organization".
  - **emailAddress** specifies the **name** sub-property as "My Organization"; **address** for "My Organization" is by default null.

**Microsoft Graph permissions**

Use the least privileged delegated or application permission, `Calendars.Read`, as appropriate, for this operation. For more information, see [calendar permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```msgraph
GET https://graph.microsoft.com/beta/users/AlexW@contoso.com/calendar/calendarPermissions
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Calendar.CalendarPermissions.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calendarPermissions, err := graphClient.Users().ByUserId("user-id").Calendar().CalendarPermissions().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CalendarPermissionCollectionResponse result = graphClient.users().byUserId("{user-id}").calendar().calendarPermissions().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let calendarPermissions = await client.api('/users/AlexW@contoso.com/calendar/calendarPermissions')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->calendar()->calendarPermissions()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Calendar

Get-MgBetaUserCalendarPermission -UserId $userId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').calendar.calendar_permissions.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('64339082-ed84-4b0b-b4ab-004ae54f3747')/calendar/calendarPermissions",
    "value": [
        {
            "id": "L289RXhjaGFuZ2VMYWJTWVnYW5C",
            "isRemovable": true,
            "isInsideOrganization": true,
            "role": "delegateWithPrivateEventAccess",
            "allowedRoles": [
                "freeBusyRead",
                "limitedRead",
                "read",
                "write",
                "delegateWithoutPrivateEventAccess",
                "delegateWithPrivateEventAccess"
            ],
            "emailAddress": {
                "name": "Megan Bowen",
                "address": "MeganB@contoso.com"
            }
        },
        {
            "id": "RGVmYXVsdA==",
            "isRemovable": false,
            "isInsideOrganization": true,
            "role": "freeBusyRead",
            "allowedRoles": [
                "none",
                "freeBusyRead",
                "limitedRead",
                "read",
                "write"
            ],
            "emailAddress": {
                "name": "My Organization"
            }
        }
    ]
}
```

### Calendar owner: Update permissions for an existing share recipient or delegate on a calendar

With the consent of Alex or administrator, you can update the permissions assigned to an existing share recipient or delegate \(specified by the **role** property\), as long as the new permissions are supported by those **allowedRoles** set up initially for the share recipient or delegate for that calendar.

Aside from the **role** property, you can't update other properties of an existing share recipient or delegate. Changing the **emailAddress** property value requires deleting the share recipient or delegate and setting up a new instance of **calendarPermission** again.

The example in this section updates the **role** property, changing the permission of an existing share recipient, Adele, from `read` to `write` for the custom calendar "Kids parties".

**Microsoft Graph permissions**

Use the least privileged delegated or application permission, `Calendars.ReadWrite`, as appropriate, for this operation. For more information, see [calendar permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
PATCH https://graph.microsoft.com/beta/users/AlexW@contoso.com/calendars/AAMkADAwAABf02bAAAA=/calendarPermissions/L289RXhjaGFuZ2VMYWJQWRlbGVW
Content-type: application/json

{
  "role": "write"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new CalendarPermission
{
	Role = CalendarRoleType.Write,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Calendars["{calendar-id}"].CalendarPermissions["{calendarPermission-id}"].PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewCalendarPermission()
role := graphmodels.WRITE_CALENDARROLETYPE 
requestBody.SetRole(&role) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calendarPermissions, err := graphClient.Users().ByUserId("user-id").Calendars().ByCalendarId("calendar-id").CalendarPermissions().ByCalendarPermissionId("calendarPermission-id").Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CalendarPermission calendarPermission = new CalendarPermission();
calendarPermission.setRole(CalendarRoleType.Write);
CalendarPermission result = graphClient.users().byUserId("{user-id}").calendars().byCalendarId("{calendar-id}").calendarPermissions().byCalendarPermissionId("{calendarPermission-id}").patch(calendarPermission);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const calendarPermission = {
  role: 'write'
};

await client.api('/users/AlexW@contoso.com/calendars/AAMkADAwAABf02bAAAA=/calendarPermissions/L289RXhjaGFuZ2VMYWJQWRlbGVW')
	.version('beta')
	.update(calendarPermission);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\CalendarPermission;
use Microsoft\Graph\Beta\Generated\Models\CalendarRoleType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CalendarPermission();
$requestBody->setRole(new CalendarRoleType('write'));

$result = $graphServiceClient->users()->byUserId('user-id')->calendars()->byCalendarId('calendar-id')->calendarPermissions()->byCalendarPermissionId('calendarPermission-id')->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.calendar_permission import CalendarPermission
from msgraph_beta.generated.models.calendar_role_type import CalendarRoleType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CalendarPermission(
	role = CalendarRoleType.Write,
)

result = await graph_client.users.by_user_id('user-id').calendars.by_calendar_id('calendar-id').calendar_permissions.by_calendar_permission_id('calendarPermission-id').patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('64339082-ed84-4b0b-b4ab-004ae54f3747')/calendars('AAMkADAwAABf02bAAAA%3D')/calendarPermissions/$entity",
    "id": "L289RXhjaGFuZ2VMYWJQWRlbGVW",
    "isRemovable": true,
    "isInsideOrganization": true,
    "role": "write",
    "allowedRoles": [
        "freeBusyRead",
        "limitedRead",
        "read",
        "write"
    ],
    "emailAddress": {
        "name": "Adele Vance",
        "address": "AdeleV@contoso.com"
    }
}
```

## Get properties of a shared or delegated calendar

In this section:

- [Calendar owner: Get properties of a shared or delegated calendar](#calendar-owner-get-properties-of-a-shared-or-delegated-calendar)
- [share recipient or delegate: Get properties of shared or delegated calendar](#share-recipient-or-delegate-get-properties-of-shared-or-delegated-calendar)

Recalling in this example, Alex has delegated his primary calendar and given the delegate, Megan Bowen, the permission to view calendar items that are marked private. This section shows the properties of the delegated calendar, first from the perspective of and with the consent of the owner, Alex, and then from the perspective of and with the consent of the delegate, Megan. Consent from the administrator also works for each case.

### Calendar owner: Get properties of a shared or delegated calendar

The example in this section gets the properties of the primary calendar from the perspective of the owner, Alex.

Note the following properties on Alex' behalf:

- **canShare** is true as Alex is the owner.
- **canViewPrivateItems** is true since Alex is the owner.
- **isShared** is set to true, as Alex has set up a delegate for this calendar.
- **isSharedWithMe** is always false for the calendar owner.
- **owner** shows Alex as the owner.

**Microsoft Graph permissions**

Use the least privileged delegated or application permission, `Calendars.Read`, as appropriate, for this operation. For more information, see [calendar permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

- [HTTP](#tabpanel_3_http)
- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [JavaScript](#tabpanel_3_javascript)
- [PHP](#tabpanel_3_php)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)

```msgraph
GET https://graph.microsoft.com/beta/users/AlexW@contoso.com/calendar
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Calendar.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calendar, err := graphClient.Users().ByUserId("user-id").Calendar().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Calendar result = graphClient.users().byUserId("{user-id}").calendar().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let calendar = await client.api('/users/AlexW@contoso.com/calendar')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->calendar()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Calendar

Get-MgBetaUserDefaultCalendar -UserId $userId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').calendar.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('64339082-ed84-4b0b-b4ab-004ae54f3747')/calendar/$entity",
    "id": "AQMkADAw7QAAAJfygAAAA==",
    "name": "Calendar",
    "color": "auto",
    "hexColor": "",
    "changeKey": "NEXywgsVrkeNsFsyVyRrtAAAAAACOg==",
    "canShare": true,
    "canViewPrivateItems": true,
    "isShared": true,
    "isSharedWithMe": false,
    "canEdit": true,
    "allowedOnlineMeetingProviders": [
        "teamsForBusiness"
    ],
    "defaultOnlineMeetingProvider": "teamsForBusiness",
    "isTallyingResponses": true,
    "isRemovable": false,
    "owner": {
        "name": "Alex Wilber",
        "address": "AlexW@contoso.com"
    }
}
```

### Share recipient or delegate: Get properties of shared or delegated calendar

The example in this section gets the properties of the same calendar from the perspective of the delegate, Megan.

Note the following properties:

- **name** of the calendar is by default the owner's display name. In this case, it's "Alex Wilber", since this is Alex' calendar delegated to Megan.
- **canShare** is false, since Megan is not the owner of this calendar.
- **canViewPrivateItems** is true for the delegate Megan, as set up by Alex. For a sharee that is not a delegate, this property is always false.
- **isShared** is false. This property indicates only to a calendar *owner* whether the calendar has been shared or delegated.
- **isSharedWithMe** property is true, since Megan is a delegate.
- **canEdit** is true, since delegates, including Megan, have write access.
- **owner** is set to Alex.

Note

A sharee or delegate can customize only the **name** property of a shared/delegated calendar. The update is visible only to themselves; the calendar owner does not see such calendar name changes.

**Microsoft Graph permissions**

Use the least privileged delegated permission, `Calendars.Read.Shared`, or application permission, `Calendars.Read`, as appropriate, for this operation. For more information, see [calendar permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

- [HTTP](#tabpanel_4_http)
- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [JavaScript](#tabpanel_4_javascript)
- [PHP](#tabpanel_4_php)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)

```msgraph
GET https://graph.microsoft.com/beta/users/meganb@contoso.com/calendars/AAMkADlAABhbftjAAA=
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].Calendars["{calendar-id}"].GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calendars, err := graphClient.Users().ByUserId("user-id").Calendars().ByCalendarId("calendar-id").Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

Calendar result = graphClient.users().byUserId("{user-id}").calendars().byCalendarId("{calendar-id}").get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let calendar = await client.api('/users/meganb@contoso.com/calendars/AAMkADlAABhbftjAAA=')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->calendars()->byCalendarId('calendar-id')->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Calendar

Get-MgBetaUserCalendar -UserId $userId -CalendarId $calendarId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').calendars.by_calendar_id('calendar-id').get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('meganb%40contoso.com')/calendars/$entity",
    "id": "AAMkADlAABhbftjAAA=",
    "name": "Alex Wilber",
    "color": "auto",
    "hexColor": "",
    "changeKey": "E6LznKWmX0KTsAD9qRJjeAAAYWo3EQ==",
    "canShare": false,
    "canViewPrivateItems": true,
    "isShared": false,
    "isSharedWithMe": true,
    "canEdit": true,
    "allowedOnlineMeetingProviders": [
        "teamsForBusiness"
    ],
    "defaultOnlineMeetingProvider": "teamsForBusiness",
    "isTallyingResponses": true,
    "isRemovable": true,
    "owner": {
        "name": "Alex Wilber",
        "address": "AlexW@contoso.com"
    }
}
```

## Get or set mailbox setting to receive meeting requests and responses

In this section:

- [Get delegation delivery setting for a user's mailbox](#get-delegation-delivery-setting-for-a-users-mailbox)
- [Set delegation delivery setting for a user's mailbox](#set-delegation-delivery-setting-for-a-users-mailbox)

Depending on the level of delegation a calendar owner prefers, the owner can specify who should receive meeting requests and responses to manage meetings on the calendar.

Programmatically, you can get or set the **delegateMeetingMessageDeliveryOptions** property of the calendar owner's [mailboxSettings](https://learn.microsoft.com/en-us/graph/api/resources/mailboxsettings) to specify to whom Outlook should direct [eventMessageRequest](https://learn.microsoft.com/en-us/graph/api/resources/eventmessagerequest) and [eventMessageResponse](https://learn.microsoft.com/en-us/graph/api/resources/eventmessageresponse) instances:

- `sendToDelegateOnly`

  Outlook to direct **eventMessageRequest** and **eventMessageResponse** instances to only delegates. This is the default setting. The owner can see responses to a meeting or respond to an invitation through the corresponding **event** in the delegated calendar.
- `sendToDelegateAndInformationToPrincipal`

  Outlook to direct **eventMessageRequest** and **eventMessageResponse** instances to delegates and the calendar owner. Only the delegates see the option to accept or decline a meeting request, and the notification sent to the owner appears like a normal email message. The owner can still respond to the meeting by opening the **event** in the delegated calendar and responding.
- `sendToDelegateAndPrincipal`

  Outlook to direct **eventMessageRequest** and **eventMessageResponse** instances to delegates and the calendar owner, either of whom can respond to the meeting request.

This is a mailbox-wide setting, so the same setting applies to all delegates of the mailbox owner.

### Get delegation delivery setting for a user's mailbox

The example in this section gets the **mailboxSettings** of a calendar owner who lets Outlook direct meeting requests and responses to only calendar delegates; that is, **delegateMeetingMessageDeliveryOptions** is set to `sendToDelegateOnly`.

**Microsoft Graph permissions**

Use the least privileged delegated or application permission, `MailboxSettings.Read`, as appropriate, for this operation. For more information about mailbox permissions, see [mail permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

- [HTTP](#tabpanel_5_http)
- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [JavaScript](#tabpanel_5_javascript)
- [PHP](#tabpanel_5_php)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)

```msgraph
GET https://graph.microsoft.com/beta/users/AlexW@contoso.com/mailboxsettings
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].MailboxSettings.GetAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
mailboxSettings, err := graphClient.Users().ByUserId("user-id").MailboxSettings().Get(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MailboxSettings result = graphClient.users().byUserId("{user-id}").mailboxSettings().get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let mailboxSettings = await client.api('/users/AlexW@contoso.com/mailboxsettings')
	.version('beta')
	.get();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$result = $graphServiceClient->users()->byUserId('user-id')->mailboxSettings()->get()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Users

Get-MgBetaUserMailboxSetting -UserId $userId
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

result = await graph_client.users.by_user_id('user-id').mailbox_settings.get()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('64339082-ed84-4b0b-b4ab-004ae54f3747')/mailboxSettings",
    "archiveFolder": "AQMkADAwAGVQAAAKfowAAAA==",
    "timeZone": "Pacific Standard Time",
    "delegateMeetingMessageDeliveryOptions": "sendToDelegateOnly",
    "dateFormat": "M/d/yyyy",
    "timeFormat": "h:mm tt",
    "automaticRepliesSetting": {
        "status": "disabled",
        "externalAudience": "all",
        "internalReplyMessage": "",
        "externalReplyMessage": "",
        "scheduledStartDateTime": {
            "dateTime": "2019-12-24T05:00:00.0000000",
            "timeZone": "UTC"
        },
        "scheduledEndDateTime": {
            "dateTime": "2019-12-25T05:00:00.0000000",
            "timeZone": "UTC"
        }
    },
    "language": {
        "locale": "en-US",
        "displayName": "English (United States)"
    },
    "workingHours": {
        "daysOfWeek": [
            "monday",
            "tuesday",
            "wednesday",
            "thursday",
            "friday"
        ],
        "startTime": "08:00:00.0000000",
        "endTime": "17:00:00.0000000",
        "timeZone": {
            "name": "Pacific Standard Time"
        }
    }
}
```

### Set delegation delivery setting for a user's mailbox

The example in this section updates the **delegateMeetingMessageDeliveryOptions** property to `sendToDelegateAndPrincipal`, to have Outlook direct meeting requests and responses of the delegated calendar to all delegates and the owner.

**Microsoft Graph permissions**

Use the least privileged delegated or application permission, `MailboxSettings.ReadWrite`, as appropriate, for this operation. For more information about mailbox permissions, see [mail permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

- [HTTP](#tabpanel_6_http)
- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [JavaScript](#tabpanel_6_javascript)
- [PHP](#tabpanel_6_php)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)

```http
PATCH https://graph.microsoft.com/beta/users/AlexW@contoso.com/mailboxsettings
Content-type: application/json

{
  "delegateMeetingMessageDeliveryOptions": "sendToDelegateAndPrincipal"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Models;

var requestBody = new MailboxSettings
{
	DelegateMeetingMessageDeliveryOptions = DelegateMeetingMessageDeliveryOptions.SendToDelegateAndPrincipal,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Users["{user-id}"].MailboxSettings.PatchAsync(requestBody);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewMailboxSettings()
delegateMeetingMessageDeliveryOptions := graphmodels.SENDTODELEGATEANDPRINCIPAL_DELEGATEMEETINGMESSAGEDELIVERYOPTIONS 
requestBody.SetDelegateMeetingMessageDeliveryOptions(&delegateMeetingMessageDeliveryOptions) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
mailboxSettings, err := graphClient.Users().ByUserId("user-id").MailboxSettings().Patch(context.Background(), requestBody, nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

MailboxSettings mailboxSettings = new MailboxSettings();
mailboxSettings.setDelegateMeetingMessageDeliveryOptions(DelegateMeetingMessageDeliveryOptions.SendToDelegateAndPrincipal);
MailboxSettings result = graphClient.users().byUserId("{user-id}").mailboxSettings().patch(mailboxSettings);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const mailboxSettings = {
  delegateMeetingMessageDeliveryOptions: 'sendToDelegateAndPrincipal'
};

await client.api('/users/AlexW@contoso.com/mailboxsettings')
	.version('beta')
	.update(mailboxSettings);
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\Models\MailboxSettings;
use Microsoft\Graph\Beta\Generated\Models\DelegateMeetingMessageDeliveryOptions;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new MailboxSettings();
$requestBody->setDelegateMeetingMessageDeliveryOptions(new DelegateMeetingMessageDeliveryOptions('sendToDelegateAndPrincipal'));

$result = $graphServiceClient->users()->byUserId('user-id')->mailboxSettings()->patch($requestBody)->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```powershell

Import-Module Microsoft.Graph.Beta.Users

$params = @{
	delegateMeetingMessageDeliveryOptions = "sendToDelegateAndPrincipal"
}

Update-MgBetaUserMailboxSetting -UserId $userId -BodyParameter $params
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.models.mailbox_settings import MailboxSettings
from msgraph_beta.generated.models.delegate_meeting_message_delivery_options import DelegateMeetingMessageDeliveryOptions
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = MailboxSettings(
	delegate_meeting_message_delivery_options = DelegateMeetingMessageDeliveryOptions.SendToDelegateAndPrincipal,
)

result = await graph_client.users.by_user_id('user-id').mailbox_settings.patch(request_body)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#users('64339082-ed84-4b0b-b4ab-004ae54f3747')/mailboxSettings",
    "delegateMeetingMessageDeliveryOptions": "sendToDelegateAndPrincipal"
}
```

## Delete a sharee or delegate of a calendar

In the example below, Alex deletes Megan as a sharee of the "Kids parties" calendar.

**Microsoft Graph permissions**

Use the least privileged delegated or application permission, `Calendars.ReadWrite`, as appropriate, for this operation. For more information, see [calendar permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

- [HTTP](#tabpanel_7_http)
- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [JavaScript](#tabpanel_7_javascript)
- [PHP](#tabpanel_7_php)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)

```http
DELETE https://graph.microsoft.com/beta/users/AlexW@contoso.com/calendars/AAMkADAwAABf02bAAAA=/calendarPermissions/L289RXhjaGFuZ2VMYWJTWVnYW5C
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Users["{user-id}"].Calendars["{calendar-id}"].CalendarPermissions["{calendarPermission-id}"].DeleteAsync();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  //other-imports
)


// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Users().ByUserId("user-id").Calendars().ByCalendarId("calendar-id").CalendarPermissions().ByCalendarPermissionId("calendarPermission-id").Delete(context.Background(), nil)
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

graphClient.users().byUserId("{user-id}").calendars().byCalendarId("{calendar-id}").calendarPermissions().byCalendarPermissionId("{calendarPermission-id}").delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/users/AlexW@contoso.com/calendars/AAMkADAwAABf02bAAAA=/calendarPermissions/L289RXhjaGFuZ2VMYWJTWVnYW5C')
	.version('beta')
	.delete();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);


$graphServiceClient->users()->byUserId('user-id')->calendars()->byCalendarId('calendar-id')->calendarPermissions()->byCalendarPermissionId('calendarPermission-id')->delete()->wait();
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```
Snippet not available
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python

await graph_client.users.by_user_id('user-id').calendars.by_calendar_id('calendar-id').calendar_permissions.by_calendar_permission_id('calendarPermission-id').delete()
```

> Read the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview) for details on how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance.

```http
HTTP/1.1 204 No Content
```

## Related content

- [Share an Outlook calendar with other people](https://support.office.com/article/share-an-outlook-calendar-with-other-people-353ed2c1-3ec5-449d-8c73-6931a0adab88)
- [Allow someone else to manage your mail and calendar as a delegate](https://support.office.com/article/allow-someone-else-to-manage-your-mail-and-calendar-41c40c04-3bd1-4d22-963a-28eafec25926)
- [Share your calendar in Outlook on the web](https://support.office.com/article/share-your-calendar-in-outlook-on-the-web-7ecef8ae-139c-40d9-bae2-a23977ee58d5)
- [Calendar delegation in Outlook on the web](https://support.office.com/article/calendar-delegation-in-outlook-on-the-web-532e6410-ee80-42b5-9b1b-a09345ccef1b)
- [Get Outlook events in a shared or delegated calendar](https://learn.microsoft.com/en-us/graph/outlook-get-shared-events-calendars)
- [Create Outlook events in a shared or delegated calendar](https://learn.microsoft.com/en-us/graph/outlook-create-event-in-shared-delegated-calendar)
