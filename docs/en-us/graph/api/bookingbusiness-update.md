<!-- Source: https://learn.microsoft.com/en-us/graph/api/bookingbusiness-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-07 -->

# Update bookingbusiness

Namespace: microsoft.graph

Update the properties of a [bookingBusiness](https://learn.microsoft.com/en-us/graph/api/resources/bookingbusiness?view=graph-rest-1.0) object.

Important

Using the PATCH method to set the email or display name isn't supported. To update these properties for a booking business, use the `Set-Mailbox cmdlet` in Exchange Online PowerShell.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Bookings.ReadWrite.All | Bookings.Manage.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Bookings.ReadWrite.All | Bookings.Manage.All |

## HTTP request

```http
PATCH /solutions/bookingBusinesses/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The street address of the business. The attribute **type** of physicalAddress is not supported in v1.0. Internally, we map the addresses to the type `others`. |
| businessHours | [bookingWorkHours](https://learn.microsoft.com/en-us/graph/api/resources/bookingworkhours?view=graph-rest-1.0) collection | The hours of operation for the business. |
| businessType | String | The type of business. |
| defaultCurrencyIso | String | The code for the currency that the business operates in on Microsoft Bookings. |
| phone | String | The telephone number for the business. |
| schedulingPolicy | [bookingSchedulingPolicy](https://learn.microsoft.com/en-us/graph/api/resources/bookingschedulingpolicy?view=graph-rest-1.0) | Specifies how bookings can be created for this business. |
| webSiteUrl | String | The URL of the business website. |

## Response

If successful, this method returns a `204 No Content` response code. It doesn't return anything in the response body.

## Example

### Request

The following example updates the business email address and scheduling policy to change the business default booking time slot to an hour, and advance booking up to 30 days.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
PATCH https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/fabrikam@contoso.com
Content-type: application/json

{
  "email": "admin@fabrikam.com",
  "schedulingPolicy": {
      "timeSlotInterval": "PT60M",
      "minimumLeadTime": "P1D",
      "maximumAdvance": "P30D",
      "sendConfirmationsToOwner": true,
      "allowStaffSelection": true
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new BookingBusiness
{
	Email = "admin@fabrikam.com",
	SchedulingPolicy = new BookingSchedulingPolicy
	{
		TimeSlotInterval = TimeSpan.Parse("PT60M"),
		MinimumLeadTime = TimeSpan.Parse("P1D"),
		MaximumAdvance = TimeSpan.Parse("P30D"),
		SendConfirmationsToOwner = true,
		AllowStaffSelection = true,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Solutions.BookingBusinesses["{bookingBusiness-id}"].PatchAsync(requestBody);
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

requestBody := graphmodels.NewBookingBusiness()
email := "admin@fabrikam.com"
requestBody.SetEmail(&email) 
schedulingPolicy := graphmodels.NewBookingSchedulingPolicy()
timeSlotInterval , err := abstractions.ParseISODuration("PT60M")
schedulingPolicy.SetTimeSlotInterval(&timeSlotInterval) 
minimumLeadTime , err := abstractions.ParseISODuration("P1D")
schedulingPolicy.SetMinimumLeadTime(&minimumLeadTime) 
maximumAdvance , err := abstractions.ParseISODuration("P30D")
schedulingPolicy.SetMaximumAdvance(&maximumAdvance) 
sendConfirmationsToOwner := true
schedulingPolicy.SetSendConfirmationsToOwner(&sendConfirmationsToOwner) 
allowStaffSelection := true
schedulingPolicy.SetAllowStaffSelection(&allowStaffSelection) 
requestBody.SetSchedulingPolicy(schedulingPolicy)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
bookingBusinesses, err := graphClient.Solutions().BookingBusinesses().ByBookingBusinessId("bookingBusiness-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

BookingBusiness bookingBusiness = new BookingBusiness();
bookingBusiness.setEmail("admin@fabrikam.com");
BookingSchedulingPolicy schedulingPolicy = new BookingSchedulingPolicy();
PeriodAndDuration timeSlotInterval = PeriodAndDuration.ofDuration(Duration.parse("PT60M"));
schedulingPolicy.setTimeSlotInterval(timeSlotInterval);
PeriodAndDuration minimumLeadTime = PeriodAndDuration.ofDuration(Duration.parse("P1D"));
schedulingPolicy.setMinimumLeadTime(minimumLeadTime);
PeriodAndDuration maximumAdvance = PeriodAndDuration.ofDuration(Duration.parse("P30D"));
schedulingPolicy.setMaximumAdvance(maximumAdvance);
schedulingPolicy.setSendConfirmationsToOwner(true);
schedulingPolicy.setAllowStaffSelection(true);
bookingBusiness.setSchedulingPolicy(schedulingPolicy);
BookingBusiness result = graphClient.solutions().bookingBusinesses().byBookingBusinessId("{bookingBusiness-id}").patch(bookingBusiness);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const bookingBusiness = {
  email: 'admin@fabrikam.com',
  schedulingPolicy: {
      timeSlotInterval: 'PT60M',
      minimumLeadTime: 'P1D',
      maximumAdvance: 'P30D',
      sendConfirmationsToOwner: true,
      allowStaffSelection: true
  }
};

await client.api('/solutions/bookingBusinesses/fabrikam@contoso.com')
	.update(bookingBusiness);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\BookingBusiness;
use Microsoft\Graph\Generated\Models\BookingSchedulingPolicy;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new BookingBusiness();
$requestBody->setEmail('admin@fabrikam.com');
$schedulingPolicy = new BookingSchedulingPolicy();
$schedulingPolicy->setTimeSlotInterval(new \DateInterval('PT60M'));
$schedulingPolicy->setMinimumLeadTime(new \DateInterval('P1D'));
$schedulingPolicy->setMaximumAdvance(new \DateInterval('P30D'));
$schedulingPolicy->setSendConfirmationsToOwner(true);
$schedulingPolicy->setAllowStaffSelection(true);
$requestBody->setSchedulingPolicy($schedulingPolicy);

$result = $graphServiceClient->solutions()->bookingBusinesses()->byBookingBusinessId('bookingBusiness-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Bookings

$params = @{
	email = "admin@fabrikam.com"
	schedulingPolicy = @{
		timeSlotInterval = "PT60M"
		minimumLeadTime = "P1D"
		maximumAdvance = "P30D"
		sendConfirmationsToOwner = $true
		allowStaffSelection = $true
	}
}

Update-MgBookingBusiness -BookingBusinessId $bookingBusinessId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.booking_business import BookingBusiness
from msgraph.generated.models.booking_scheduling_policy import BookingSchedulingPolicy
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = BookingBusiness(
	email = "admin@fabrikam.com",
	scheduling_policy = BookingSchedulingPolicy(
		time_slot_interval = "PT60M",
		minimum_lead_time = "P1D",
		maximum_advance = "P30D",
		send_confirmations_to_owner = True,
		allow_staff_selection = True,
	),
)

result = await graph_client.solutions.booking_businesses.by_booking_business_id('bookingBusiness-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
```
