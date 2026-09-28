<!-- Source: https://learn.microsoft.com/en-us/graph/api/calendar-post-calendarpermissions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-05 -->

# Create calendarPermission

Namespace: microsoft.graph

Create a [calendarPermission](https://learn.microsoft.com/en-us/graph/api/resources/calendarpermission?view=graph-rest-1.0) resource to specify the identity and role of the user with whom the specified calendar is being shared or delegated.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Depending on the type of calendar that the event is in and the permission type \(delegated or application\) requested, one of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Calendar | Delegated \(work or school account\) | Delegated \(personal Microsoft account\) | Application |
| :--- | :--- | :--- | :--- |
| user calendar | Calendars.Read, Calendars.ReadWrite | Calendars.Read, Calendars.ReadWrite | Calendars.Read, Calendars.ReadWrite |
| group calendar | Group.Read.All, Group.ReadWrite.All | Not supported. | Not supported. |

## HTTP request

Create the specified permissions of a user's primary calendar:

```http
POST /users/{id}/calendar/calendarPermissions
```

Create the specified permissions of a group calendar:

```http
POST /groups/{id}/calendar/calendarPermissions
```

Create the specified permissions of the user calendar that contains the identified event:

```http
POST /users/{id}/events/{id}/calendar/calendarPermissions
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of a [calendarPermission](https://learn.microsoft.com/en-us/graph/api/resources/calendarpermission?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `200 OK` response code and a collection of calendarPermission objects in the response body.

## Examples

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
POST https://graph.microsoft.com/v1.0/me/calendar/calendarPermissions

{
    "emailAddress": {
        "name": "Samantha Booth",
        "address": "samanthab@contoso.com"
    },
    "isInsideOrganization": true,
    "isRemovable": true,
    "role": "read"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CalendarPermission
{
	EmailAddress = new EmailAddress
	{
		Name = "Samantha Booth",
		Address = "samanthab@contoso.com",
	},
	IsInsideOrganization = true,
	IsRemovable = true,
	Role = CalendarRoleType.Read,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Calendar.CalendarPermissions.PostAsync(requestBody);
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

requestBody := graphmodels.NewCalendarPermission()
emailAddress := graphmodels.NewEmailAddress()
name := "Samantha Booth"
emailAddress.SetName(&name) 
address := "samanthab@contoso.com"
emailAddress.SetAddress(&address) 
requestBody.SetEmailAddress(emailAddress)
isInsideOrganization := true
requestBody.SetIsInsideOrganization(&isInsideOrganization) 
isRemovable := true
requestBody.SetIsRemovable(&isRemovable) 
role := graphmodels.READ_CALENDARROLETYPE 
requestBody.SetRole(&role) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
calendarPermissions, err := graphClient.Me().Calendar().CalendarPermissions().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CalendarPermission calendarPermission = new CalendarPermission();
EmailAddress emailAddress = new EmailAddress();
emailAddress.setName("Samantha Booth");
emailAddress.setAddress("samanthab@contoso.com");
calendarPermission.setEmailAddress(emailAddress);
calendarPermission.setIsInsideOrganization(true);
calendarPermission.setIsRemovable(true);
calendarPermission.setRole(CalendarRoleType.Read);
CalendarPermission result = graphClient.me().calendar().calendarPermissions().post(calendarPermission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const calendarPermission = {
    emailAddress: {
        name: 'Samantha Booth',
        address: 'samanthab@contoso.com'
    },
    isInsideOrganization: true,
    isRemovable: true,
    role: 'read'
};

await client.api('/me/calendar/calendarPermissions')
	.post(calendarPermission);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CalendarPermission;
use Microsoft\Graph\Generated\Models\EmailAddress;
use Microsoft\Graph\Generated\Models\CalendarRoleType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CalendarPermission();
$emailAddress = new EmailAddress();
$emailAddress->setName('Samantha Booth');
$emailAddress->setAddress('samanthab@contoso.com');
$requestBody->setEmailAddress($emailAddress);
$requestBody->setIsInsideOrganization(true);
$requestBody->setIsRemovable(true);
$requestBody->setRole(new CalendarRoleType('read'));

$result = $graphServiceClient->me()->calendar()->calendarPermissions()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	emailAddress = @{
		name = "Samantha Booth"
		address = "samanthab@contoso.com"
	}
	isInsideOrganization = $true
	isRemovable = $true
	role = "read"
}

# A UPN can also be used as -UserId.
New-MgUserCalendarPermission -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.calendar_permission import CalendarPermission
from msgraph.generated.models.email_address import EmailAddress
from msgraph.generated.models.calendar_role_type import CalendarRoleType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CalendarPermission(
	email_address = EmailAddress(
		name = "Samantha Booth",
		address = "samanthab@contoso.com",
	),
	is_inside_organization = True,
	is_removable = True,
	role = CalendarRoleType.Read,
)

result = await graph_client.me.calendar.calendar_permissions.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('458d4c95-124e-49da-ba9d-1dd0387e682e')/calendar/calendarPermissions/$entity",
    "id": "RXhjaGFuZ2VQdWJsaXNoZWRVc2VyLnNhbWFudGhhYkBhZGF0dW0ub25taWNyb3NvZnQuY29t",
    "isRemovable": true,
    "isInsideOrganization": true,
    "role": "read",
    "allowedRoles": [
        "freeBusyRead",
        "limitedRead",
        "read"
    ],
    "emailAddress": {
        "name": "Samantha Booth",
        "address": "samanthab@contoso.com"
    }
}
```
