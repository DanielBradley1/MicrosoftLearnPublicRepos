<!-- Source: https://learn.microsoft.com/en-us/graph/api/place-post-checkins?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Create checkInClaim

Namespace: microsoft.graph

Create a new [checkInClaim](https://learn.microsoft.com/en-us/graph/api/resources/checkinclaim?view=graph-rest-1.0) object to record the check-in status for a specific place, such as a [desk](https://learn.microsoft.com/en-us/graph/api/resources/desk?view=graph-rest-1.0) or a [room](https://learn.microsoft.com/en-us/graph/api/resources/room?view=graph-rest-1.0), associated with a specific calendar reservation. This check-in confirms that the reserved space is in use and prevents automatic release if auto-release policies are configured for that place.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Calendars.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /places/{placesId}/checkIns
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [checkInClaim](https://learn.microsoft.com/en-us/graph/api/resources/checkinclaim?view=graph-rest-1.0) object.

You can specify the following properties when creating a **checkInClaim**.

| Property | Type | Description |
| :--- | :--- | :--- |
| calendarEventId | String | The unique identifier for an Outlook calendar event associated with the **checkInClaim** object. For more information, see the **iCalUId** property in [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0). Read-only. Required. |
| checkInMethod | [checkInMethod](https://learn.microsoft.com/en-us/graph/api/resources/checkinclaim?view=graph-rest-1.0#checkinmethod-values) | Indicates the method of check-in. The possible values are: `unspecified`, `manual`, `inferred`, `verified`, `unknownFutureValue`. The default value is `unspecified`. Required. |

## Response

If successful, this method returns a `201 Created` response code and a [checkInClaim](https://learn.microsoft.com/en-us/graph/api/resources/checkinclaim?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/places/c8aaf4d8-6c73-46c4-bf28-b2adadafb5be/checkIns
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.checkInClaim",
  "calendarEventId": "040000008200E00074C5B7101A82E00800000000D02AC02D26EFDB010000000000000000100000005A18ADA04F0A24489AE13ED3CC367978",
  "checkInMethod": "verified"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new CheckInClaim
{
	OdataType = "#microsoft.graph.checkInClaim",
	CalendarEventId = "040000008200E00074C5B7101A82E00800000000D02AC02D26EFDB010000000000000000100000005A18ADA04F0A24489AE13ED3CC367978",
	CheckInMethod = CheckInMethod.Verified,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Places["{place-id}"].CheckIns.PostAsync(requestBody);
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

requestBody := graphmodels.NewCheckInClaim()
calendarEventId := "040000008200E00074C5B7101A82E00800000000D02AC02D26EFDB010000000000000000100000005A18ADA04F0A24489AE13ED3CC367978"
requestBody.SetCalendarEventId(&calendarEventId) 
checkInMethod := graphmodels.VERIFIED_CHECKINMETHOD 
requestBody.SetCheckInMethod(&checkInMethod) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
checkIns, err := graphClient.Places().ByPlaceId("place-id").CheckIns().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

CheckInClaim checkInClaim = new CheckInClaim();
checkInClaim.setOdataType("#microsoft.graph.checkInClaim");
checkInClaim.setCalendarEventId("040000008200E00074C5B7101A82E00800000000D02AC02D26EFDB010000000000000000100000005A18ADA04F0A24489AE13ED3CC367978");
checkInClaim.setCheckInMethod(CheckInMethod.Verified);
CheckInClaim result = graphClient.places().byPlaceId("{place-id}").checkIns().post(checkInClaim);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const checkInClaim = {
  '@odata.type': '#microsoft.graph.checkInClaim',
  calendarEventId: '040000008200E00074C5B7101A82E00800000000D02AC02D26EFDB010000000000000000100000005A18ADA04F0A24489AE13ED3CC367978',
  checkInMethod: 'verified'
};

await client.api('/places/c8aaf4d8-6c73-46c4-bf28-b2adadafb5be/checkIns')
	.post(checkInClaim);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\CheckInClaim;
use Microsoft\Graph\Generated\Models\CheckInMethod;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new CheckInClaim();
$requestBody->setOdataType('#microsoft.graph.checkInClaim');
$requestBody->setCalendarEventId('040000008200E00074C5B7101A82E00800000000D02AC02D26EFDB010000000000000000100000005A18ADA04F0A24489AE13ED3CC367978');
$requestBody->setCheckInMethod(new CheckInMethod('verified'));

$result = $graphServiceClient->places()->byPlaceId('place-id')->checkIns()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Calendar

$params = @{
	"@odata.type" = "#microsoft.graph.checkInClaim"
	calendarEventId = "040000008200E00074C5B7101A82E00800000000D02AC02D26EFDB010000000000000000100000005A18ADA04F0A24489AE13ED3CC367978"
	checkInMethod = "verified"
}

New-MgPlaceCheck -PlaceId $placeId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.check_in_claim import CheckInClaim
from msgraph.generated.models.check_in_method import CheckInMethod
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = CheckInClaim(
	odata_type = "#microsoft.graph.checkInClaim",
	calendar_event_id = "040000008200E00074C5B7101A82E00800000000D02AC02D26EFDB010000000000000000100000005A18ADA04F0A24489AE13ED3CC367978",
	check_in_method = CheckInMethod.Verified,
)

result = await graph_client.places.by_place_id('place-id').check_ins.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.checkInClaim",
  "calendarEventId": "040000008200E00074C5B7101A82E00800000000D02AC02D26EFDB010000000000000000100000005A18ADA04F0A24489AE13ED3CC367978",
  "checkInMethod": "verified",
  "createdDateTime": "2025-06-28T12:34:56.789Z"
}
```
