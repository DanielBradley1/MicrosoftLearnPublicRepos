<!-- Source: https://learn.microsoft.com/en-us/graph/api/workplanoccurrence-setcurrentlocation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-03 -->

# workPlanOccurrence: setCurrentLocation

Namespace: microsoft.graph

Update a user's [work](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0) location for the current day or current active segment. This action quickly updates the user's work location without modifying individual occurrences.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Calendars.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

> **Note:** Application permissions are supported only when using the `/users/{id}` endpoint.

## HTTP request

```http
POST /me/settings/workHoursAndLocations/occurrences/setCurrentLocation
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

When using delegated permissions with the `/users/{id}` endpoint, the ID must be the signed-in user's ID.

```http
POST /users/{id | userPrincipalName}/settings/workHoursAndLocations/occurrences/setCurrentLocation
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, provide a JSON object with the following parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| placeId | String | Identifier of a place from the Microsoft Graph Places Directory API. Only applicable when **workLocationType** is set to `office`. |
| updateScope | [workLocationUpdateScope](#worklocationupdatescope-values) | The scope of the update. Supports a subset of the values of **workLocationUpdateScope**. The possible values are: `currentSegment`, `currentDay`. |
| workLocationType | [workLocationType](https://learn.microsoft.com/en-us/graph/api/resources/workplanoccurrence?view=graph-rest-1.0#worklocationtype-values) | The new work location type to set. Supports a subset of the values of **workLocationType**. The possible values are: `office`, `remote`. |

### workLocationUpdateScope values

| Member | Description |
| :--- | :--- |
| currentSegment | Update only the current time segment. |
| currentDay | Update the entire current day. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Example 1: Set the current location to office

The following example shows how to set the current location to office.

#### Request

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
POST https://graph.microsoft.com/v1.0/me/settings/workHoursAndLocations/occurrences/setCurrentLocation
Content-type: application/json

{
  "updateScope": "currentDay",
  "workLocationType": "office",
  "placeId": "12345678-1234-1234-1234-123456789012"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.Settings.WorkHoursAndLocations.Occurrences.SetCurrentLocation;
using Microsoft.Graph.Models;

var requestBody = new SetCurrentLocationPostRequestBody
{
	UpdateScope = WorkLocationUpdateScope.CurrentDay,
	WorkLocationType = WorkLocationType.Office,
	PlaceId = "12345678-1234-1234-1234-123456789012",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Me.Settings.WorkHoursAndLocations.Occurrences.SetCurrentLocation.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphusers.NewItemSetCurrentLocationPostRequestBody()
updateScope := graphmodels.CURRENTDAY_WORKLOCATIONUPDATESCOPE 
requestBody.SetUpdateScope(&updateScope) 
workLocationType := graphmodels.OFFICE_WORKLOCATIONTYPE 
requestBody.SetWorkLocationType(&workLocationType) 
placeId := "12345678-1234-1234-1234-123456789012"
requestBody.SetPlaceId(&placeId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Me().Settings().WorkHoursAndLocations().Occurrences().SetCurrentLocation().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.settings.workhoursandlocations.occurrences.setcurrentlocation.SetCurrentLocationPostRequestBody setCurrentLocationPostRequestBody = new com.microsoft.graph.users.item.settings.workhoursandlocations.occurrences.setcurrentlocation.SetCurrentLocationPostRequestBody();
setCurrentLocationPostRequestBody.setUpdateScope(WorkLocationUpdateScope.CurrentDay);
setCurrentLocationPostRequestBody.setWorkLocationType(WorkLocationType.Office);
setCurrentLocationPostRequestBody.setPlaceId("12345678-1234-1234-1234-123456789012");
graphClient.me().settings().workHoursAndLocations().occurrences().setCurrentLocation().post(setCurrentLocationPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const setCurrentLocation = {
  updateScope: 'currentDay',
  workLocationType: 'office',
  placeId: '12345678-1234-1234-1234-123456789012'
};

await client.api('/me/settings/workHoursAndLocations/occurrences/setCurrentLocation')
	.post(setCurrentLocation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Settings\WorkHoursAndLocations\Occurrences\SetCurrentLocation\SetCurrentLocationPostRequestBody;
use Microsoft\Graph\Generated\Models\WorkLocationUpdateScope;
use Microsoft\Graph\Generated\Models\WorkLocationType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SetCurrentLocationPostRequestBody();
$requestBody->setUpdateScope(new WorkLocationUpdateScope('currentDay'));
$requestBody->setWorkLocationType(new WorkLocationType('office'));
$requestBody->setPlaceId('12345678-1234-1234-1234-123456789012');

$graphServiceClient->me()->settings()->workHoursAndLocations()->occurrences()->setCurrentLocation()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	updateScope = "currentDay"
	workLocationType = "office"
	placeId = "12345678-1234-1234-1234-123456789012"
}

# A UPN can also be used as -UserId.
Set-MgUserSettingWorkHourAndLocationOccurrenceCurrentLocation -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.settings.workhoursandlocations.occurrences.set_current_location.set_current_location_post_request_body import SetCurrentLocationPostRequestBody
from msgraph.generated.models.work_location_update_scope import WorkLocationUpdateScope
from msgraph.generated.models.work_location_type import WorkLocationType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SetCurrentLocationPostRequestBody(
	update_scope = WorkLocationUpdateScope.CurrentDay,
	work_location_type = WorkLocationType.Office,
	place_id = "12345678-1234-1234-1234-123456789012",
)

await graph_client.me.settings.work_hours_and_locations.occurrences.set_current_location.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Set current location to remote

The following example shows how to set the current location to remote.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/me/settings/workHoursAndLocations/occurrences/setCurrentLocation
Content-type: application/json

{
  "updateScope": "currentSegment",
  "workLocationType": "remote"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Me.Settings.WorkHoursAndLocations.Occurrences.SetCurrentLocation;
using Microsoft.Graph.Models;

var requestBody = new SetCurrentLocationPostRequestBody
{
	UpdateScope = WorkLocationUpdateScope.CurrentSegment,
	WorkLocationType = WorkLocationType.Remote,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
await graphClient.Me.Settings.WorkHoursAndLocations.Occurrences.SetCurrentLocation.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphusers "github.com/microsoftgraph/msgraph-sdk-go/users"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphusers.NewItemSetCurrentLocationPostRequestBody()
updateScope := graphmodels.CURRENTSEGMENT_WORKLOCATIONUPDATESCOPE 
requestBody.SetUpdateScope(&updateScope) 
workLocationType := graphmodels.REMOTE_WORKLOCATIONTYPE 
requestBody.SetWorkLocationType(&workLocationType) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
graphClient.Me().Settings().WorkHoursAndLocations().Occurrences().SetCurrentLocation().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.users.item.settings.workhoursandlocations.occurrences.setcurrentlocation.SetCurrentLocationPostRequestBody setCurrentLocationPostRequestBody = new com.microsoft.graph.users.item.settings.workhoursandlocations.occurrences.setcurrentlocation.SetCurrentLocationPostRequestBody();
setCurrentLocationPostRequestBody.setUpdateScope(WorkLocationUpdateScope.CurrentSegment);
setCurrentLocationPostRequestBody.setWorkLocationType(WorkLocationType.Remote);
graphClient.me().settings().workHoursAndLocations().occurrences().setCurrentLocation().post(setCurrentLocationPostRequestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const setCurrentLocation = {
  updateScope: 'currentSegment',
  workLocationType: 'remote'
};

await client.api('/me/settings/workHoursAndLocations/occurrences/setCurrentLocation')
	.post(setCurrentLocation);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Users\Item\Settings\WorkHoursAndLocations\Occurrences\SetCurrentLocation\SetCurrentLocationPostRequestBody;
use Microsoft\Graph\Generated\Models\WorkLocationUpdateScope;
use Microsoft\Graph\Generated\Models\WorkLocationType;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SetCurrentLocationPostRequestBody();
$requestBody->setUpdateScope(new WorkLocationUpdateScope('currentSegment'));
$requestBody->setWorkLocationType(new WorkLocationType('remote'));

$graphServiceClient->me()->settings()->workHoursAndLocations()->occurrences()->setCurrentLocation()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	updateScope = "currentSegment"
	workLocationType = "remote"
}

# A UPN can also be used as -UserId.
Set-MgUserSettingWorkHourAndLocationOccurrenceCurrentLocation -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.users.item.settings.workhoursandlocations.occurrences.set_current_location.set_current_location_post_request_body import SetCurrentLocationPostRequestBody
from msgraph.generated.models.work_location_update_scope import WorkLocationUpdateScope
from msgraph.generated.models.work_location_type import WorkLocationType
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SetCurrentLocationPostRequestBody(
	update_scope = WorkLocationUpdateScope.CurrentSegment,
	work_location_type = WorkLocationType.Remote,
)

await graph_client.me.settings.work_hours_and_locations.occurrences.set_current_location.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
