<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualeventtownhall-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Update virtualEventTownhall

Namespace: microsoft.graph

Update the properties of a [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) object.

Only the **Organizer** and **Co-organizer** can make changes to a townhall event.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | VirtualEvent.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /solutions/virtualEvents/townhalls/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| coOrganizers | [communicationsUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsuseridentity?view=graph-rest-1.0) collection | Identity information of coorganizers of the virtual event. |
| description | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | Description of the virtual event. |
| displayName | String | Display name of the virtual event. |
| endDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | Date and time when the virtual event ends. |
| invitedAttendees | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-1.0) collection | The identities of the attendees invited to the town hall. The supported identities are: [communicationsGuestIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsguestidentity?view=graph-rest-1.0) and [communicationsUserIdentity](https://learn.microsoft.com/en-us/graph/api/resources/communicationsuseridentity?view=graph-rest-1.0). |
| isRegistrationRequired | Boolean | Indicates whether attendee registration is enabled for the town hall. Inherited from [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0). Optional. |
| settings | [virtualEventSettings](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventsettings?view=graph-rest-1.0) | The virtual event settings. |
| startDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | Date and time when the virtual event starts. |

## Response

If successful, this method returns a `200 OK` response code and an updated [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) object in the response body.

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
PATCH https://graph.microsoft.com/v1.0/solutions/virtualEvents/townhalls/fc6e8c15-2fd7-1dd5-caa0-87056e6a12be
Content-Type: application/json

{
  "startDateTime": {
    "dateTime": "2024-03-31T10:00:00",
    "timeZone": "Pacific Standard Time"
  },
  "endDateTime": {
    "dateTime": "2024-03-31T17:00:00",
    "timeZone": "Pacific Standard Time"
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new VirtualEventTownhall
{
	StartDateTime = new DateTimeTimeZone
	{
		DateTime = "2024-03-31T10:00:00",
		TimeZone = "Pacific Standard Time",
	},
	EndDateTime = new DateTimeTimeZone
	{
		DateTime = "2024-03-31T17:00:00",
		TimeZone = "Pacific Standard Time",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.VirtualEvents.Townhalls["{virtualEventTownhall-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewVirtualEventTownhall()
startDateTime := graphmodels.NewDateTimeTimeZone()
dateTime := "2024-03-31T10:00:00"
startDateTime.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
startDateTime.SetTimeZone(&timeZone) 
requestBody.SetStartDateTime(startDateTime)
endDateTime := graphmodels.NewDateTimeTimeZone()
dateTime := "2024-03-31T17:00:00"
endDateTime.SetDateTime(&dateTime) 
timeZone := "Pacific Standard Time"
endDateTime.SetTimeZone(&timeZone) 
requestBody.SetEndDateTime(endDateTime)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
townhalls, err := graphClient.Solutions().VirtualEvents().Townhalls().ByVirtualEventTownhallId("virtualEventTownhall-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

VirtualEventTownhall virtualEventTownhall = new VirtualEventTownhall();
DateTimeTimeZone startDateTime = new DateTimeTimeZone();
startDateTime.setDateTime("2024-03-31T10:00:00");
startDateTime.setTimeZone("Pacific Standard Time");
virtualEventTownhall.setStartDateTime(startDateTime);
DateTimeTimeZone endDateTime = new DateTimeTimeZone();
endDateTime.setDateTime("2024-03-31T17:00:00");
endDateTime.setTimeZone("Pacific Standard Time");
virtualEventTownhall.setEndDateTime(endDateTime);
VirtualEventTownhall result = graphClient.solutions().virtualEvents().townhalls().byVirtualEventTownhallId("{virtualEventTownhall-id}").patch(virtualEventTownhall);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const virtualEventTownhall = {
  startDateTime: {
    dateTime: '2024-03-31T10:00:00',
    timeZone: 'Pacific Standard Time'
  },
  endDateTime: {
    dateTime: '2024-03-31T17:00:00',
    timeZone: 'Pacific Standard Time'
  }
};

await client.api('/solutions/virtualEvents/townhalls/fc6e8c15-2fd7-1dd5-caa0-87056e6a12be')
	.update(virtualEventTownhall);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\VirtualEventTownhall;
use Microsoft\Graph\Generated\Models\DateTimeTimeZone;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new VirtualEventTownhall();
$startDateTime = new DateTimeTimeZone();
$startDateTime->setDateTime('2024-03-31T10:00:00');
$startDateTime->setTimeZone('Pacific Standard Time');
$requestBody->setStartDateTime($startDateTime);
$endDateTime = new DateTimeTimeZone();
$endDateTime->setDateTime('2024-03-31T17:00:00');
$endDateTime->setTimeZone('Pacific Standard Time');
$requestBody->setEndDateTime($endDateTime);

$result = $graphServiceClient->solutions()->virtualEvents()->townhalls()->byVirtualEventTownhallId('virtualEventTownhall-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	startDateTime = @{
		dateTime = "2024-03-31T10:00:00"
		timeZone = "Pacific Standard Time"
	}
	endDateTime = @{
		dateTime = "2024-03-31T17:00:00"
		timeZone = "Pacific Standard Time"
	}
}

Update-MgVirtualEventTownhall -VirtualEventTownhallId $virtualEventTownhallId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.virtual_event_townhall import VirtualEventTownhall
from msgraph.generated.models.date_time_time_zone import DateTimeTimeZone
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = VirtualEventTownhall(
	start_date_time = DateTimeTimeZone(
		date_time = "2024-03-31T10:00:00",
		time_zone = "Pacific Standard Time",
	),
	end_date_time = DateTimeTimeZone(
		date_time = "2024-03-31T17:00:00",
		time_zone = "Pacific Standard Time",
	),
)

result = await graph_client.solutions.virtual_events.townhalls.by_virtual_event_townhall_id('virtualEventTownhall-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.virtualEventTownhall",
  "id": "a57082a9-7629-4f74-8da0-8d621aab4d2d@4aa05bcc-1cac-4a83-a9ae-0db84b88f4ba",
  "status": "draft",
  "displayName": "The Impact of Tech on Our Lives",
  "description": {
    "content": "<p>Discusses how technology has changed the way we communicate, work, and interact with each other.<p>",
    "contentType": "html"
  },
  "startDateTime": {
    "dateTime": "2024-03-31T10:00:00",
    "timeZone": "Pacific Standard Time"
  },
  "endDateTime": {
    "dateTime": "2024-03-31T17:00:00",
    "timeZone": "Pacific Standard Time"
  },
  "createdBy": {
    "application": null,
    "device": null,
    "user": {
      "@odata.type": "#microsoft.graph.communicationsUserIdentity",
      "id": "b7ef013a-c73c-4ec7-8ccb-e56290f45f68",
      "displayName": "Diane Demoss",
      "tenantId": "77229959-e479-4a73-b6e0-ddac27be315c"
    }
  },
  "audience": "organization",
  "isInviteOnly": false,  
  "coOrganizers": [
    {
      "id": "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b",
      "displayName": "Kenneth Brown",
      "tenantId": "77229959-e479-4a73-b6e0-ddac27be315c"
    }
  ],
  "invitedAttendees": [
    {
      "@odata.type": "microsoft.graph.communicationsUserIdentity",
      "id": "127962bb-84e1-7b62-fd98-1c9d39def7b6",
      "displayName": "Emilee Pham",
      "tenantId": "77229959-e479-4a73-b6e0-ddac27be315c"
    }
  ],
  "settings": {
    "isAttendeeEmailNotificationEnabled": false
  },
  "externalEventInformation": [
    {
      "applicationId" : "1b7ba4d1-c377-4b2f-ad0e-a3fc50bc987b",
      "externalEventId": "myExternalEventId"
    }
  ]
}
```
