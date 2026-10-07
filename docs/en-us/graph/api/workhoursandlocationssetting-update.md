<!-- Source: https://learn.microsoft.com/en-us/graph/api/workhoursandlocationssetting-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-03 -->

# Update workHoursAndLocationsSetting

Namespace: microsoft.graph

Update the properties of a user's [workHoursAndLocationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/workhoursandlocationssetting?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Calendars.ReadWrite | MailboxSettings.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

> **Note:** Application permissions are supported only when using the `/users/{id}` endpoint.

## HTTP request

```http
PATCH /me/settings/workHoursAndLocations
```

Note

Calling the `/me` endpoint requires a signed-in user and therefore a delegated permission. Application permissions aren't supported when using the `/me` endpoint.

When using delegated permissions with the `/users/{id}` endpoint, the ID must be the signed-in user's ID.

```http
PATCH /users/{id | userPrincipalName}/settings/workHoursAndLocations
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
| maxSharedWorkLocationDetails | [maxWorkLocationDetails](https://learn.microsoft.com/en-us/graph/api/resources/workhoursandlocationssetting?view=graph-rest-1.0#maxworklocationdetails-values) | Controls the level of work location details that can be shared with colleagues. Supports a subset of the values of **maxSharedWorkLocationDetails**. The possible values are: `none`, `approximate`, `specific`. |

## Response

If successful, this method returns a `200 OK` response code and an updated [workHoursAndLocationsSetting](https://learn.microsoft.com/en-us/graph/api/resources/workhoursandlocationssetting?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request to update the maximum level of work location details that can be shared.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/me/settings/workHoursAndLocations
Content-Type: application/json

{
  "maxSharedWorkLocationDetails": "approximate"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new WorkHoursAndLocationsSetting
{
	MaxSharedWorkLocationDetails = MaxWorkLocationDetails.Approximate,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.Settings.WorkHoursAndLocations.PatchAsync(requestBody);
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

requestBody := graphmodels.NewWorkHoursAndLocationsSetting()
maxSharedWorkLocationDetails := graphmodels.APPROXIMATE_MAXWORKLOCATIONDETAILS 
requestBody.SetMaxSharedWorkLocationDetails(&maxSharedWorkLocationDetails) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
workHoursAndLocations, err := graphClient.Me().Settings().WorkHoursAndLocations().Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

WorkHoursAndLocationsSetting workHoursAndLocationsSetting = new WorkHoursAndLocationsSetting();
workHoursAndLocationsSetting.setMaxSharedWorkLocationDetails(MaxWorkLocationDetails.Approximate);
WorkHoursAndLocationsSetting result = graphClient.me().settings().workHoursAndLocations().patch(workHoursAndLocationsSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const workHoursAndLocationsSetting = {
  maxSharedWorkLocationDetails: 'approximate'
};

await client.api('/me/settings/workHoursAndLocations')
	.update(workHoursAndLocationsSetting);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\WorkHoursAndLocationsSetting;
use Microsoft\Graph\Generated\Models\MaxWorkLocationDetails;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new WorkHoursAndLocationsSetting();
$requestBody->setMaxSharedWorkLocationDetails(new MaxWorkLocationDetails('approximate'));

$result = $graphServiceClient->me()->settings()->workHoursAndLocations()->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = @{
	maxSharedWorkLocationDetails = "approximate"
}

# A UPN can also be used as -UserId.
Update-MgUserSettingWorkHourAndLocation -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.work_hours_and_locations_setting import WorkHoursAndLocationsSetting
from msgraph.generated.models.max_work_location_details import MaxWorkLocationDetails
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = WorkHoursAndLocationsSetting(
	max_shared_work_location_details = MaxWorkLocationDetails.Approximate,
)

result = await graph_client.me.settings.work_hours_and_locations.patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('12345678-1234-1234-1234-123456789012')/settings/workHoursAndLocations/$entity",
  "maxSharedWorkLocationDetails": "approximate"
}
```
