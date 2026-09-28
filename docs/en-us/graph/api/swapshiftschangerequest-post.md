<!-- Source: https://learn.microsoft.com/en-us/graph/api/swapshiftschangerequest-post?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create swapShiftsChangeRequest

Namespace: microsoft.graph

Create an instance of a [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.ReadWrite.All | Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

> **Note**: This API supports admin permissions. Users with admin roles can access groups that they are not a member of.

## HTTP request

```http
POST /teams/{teamId}/schedule/swapShiftsChangeRequests
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

In the request body, provide a JSON representation of a new [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `200 OK` response code and the created [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/teams/788b75d2-a911-48c0-a5e2-dc98480457e3/schedule/swapShiftsChangeRequests
Authorization: Bearer {token}
Content-type: application/json

{
  "senderShiftId": "5ad10161-6524-4c7c-9beb-4e8677ba2f6d",
  "senderMessage": "I can't make my shift, any chance we can swap?",
  "recipientUserId": "567c8ea5-9e32-422a-a663-8270201699cd",
  "recipientShiftId": "e73408ca-3ea5-4bbf-96a8-2e06c95f7a2c"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new SwapShiftsChangeRequest
{
	SenderShiftId = "5ad10161-6524-4c7c-9beb-4e8677ba2f6d",
	SenderMessage = "I can't make my shift, any chance we can swap?",
	RecipientUserId = "567c8ea5-9e32-422a-a663-8270201699cd",
	RecipientShiftId = "e73408ca-3ea5-4bbf-96a8-2e06c95f7a2c",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Teams["{team-id}"].Schedule.SwapShiftsChangeRequests.PostAsync(requestBody, (requestConfiguration) =>
{
	requestConfiguration.Headers.Add("Authorization", "Bearer {token}");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  graphteams "github.com/microsoftgraph/msgraph-sdk-go/teams"
	  //other-imports
)

headers := abstractions.NewRequestHeaders()
headers.Add("Authorization", "Bearer {token}")

configuration := &graphteams.ItemScheduleSwapShiftsChangeRequestsRequestBuilderPostRequestConfiguration{
	Headers: headers,
}
requestBody := graphmodels.NewSwapShiftsChangeRequest()
senderShiftId := "5ad10161-6524-4c7c-9beb-4e8677ba2f6d"
requestBody.SetSenderShiftId(&senderShiftId) 
senderMessage := "I can't make my shift, any chance we can swap?"
requestBody.SetSenderMessage(&senderMessage) 
recipientUserId := "567c8ea5-9e32-422a-a663-8270201699cd"
requestBody.SetRecipientUserId(&recipientUserId) 
recipientShiftId := "e73408ca-3ea5-4bbf-96a8-2e06c95f7a2c"
requestBody.SetRecipientShiftId(&recipientShiftId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
swapShiftsChangeRequests, err := graphClient.Teams().ByTeamId("team-id").Schedule().SwapShiftsChangeRequests().Post(context.Background(), requestBody, configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SwapShiftsChangeRequest swapShiftsChangeRequest = new SwapShiftsChangeRequest();
swapShiftsChangeRequest.setSenderShiftId("5ad10161-6524-4c7c-9beb-4e8677ba2f6d");
swapShiftsChangeRequest.setSenderMessage("I can't make my shift, any chance we can swap?");
swapShiftsChangeRequest.setRecipientUserId("567c8ea5-9e32-422a-a663-8270201699cd");
swapShiftsChangeRequest.setRecipientShiftId("e73408ca-3ea5-4bbf-96a8-2e06c95f7a2c");
SwapShiftsChangeRequest result = graphClient.teams().byTeamId("{team-id}").schedule().swapShiftsChangeRequests().post(swapShiftsChangeRequest, requestConfiguration -> {
	requestConfiguration.headers.add("Authorization", "Bearer {token}");
});
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const swapShiftsChangeRequest = {
  senderShiftId: '5ad10161-6524-4c7c-9beb-4e8677ba2f6d',
  senderMessage: 'I can\'t make my shift, any chance we can swap?',
  recipientUserId: '567c8ea5-9e32-422a-a663-8270201699cd',
  recipientShiftId: 'e73408ca-3ea5-4bbf-96a8-2e06c95f7a2c'
};

await client.api('/teams/788b75d2-a911-48c0-a5e2-dc98480457e3/schedule/swapShiftsChangeRequests')
	.post(swapShiftsChangeRequest);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Teams\Item\Schedule\SwapShiftsChangeRequests\SwapShiftsChangeRequestsRequestBuilderPostRequestConfiguration;
use Microsoft\Graph\Generated\Models\SwapShiftsChangeRequest;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SwapShiftsChangeRequest();
$requestBody->setSenderShiftId('5ad10161-6524-4c7c-9beb-4e8677ba2f6d');
$requestBody->setSenderMessage('I can\'t make my shift, any chance we can swap?');
$requestBody->setRecipientUserId('567c8ea5-9e32-422a-a663-8270201699cd');
$requestBody->setRecipientShiftId('e73408ca-3ea5-4bbf-96a8-2e06c95f7a2c');
$requestConfiguration = new SwapShiftsChangeRequestsRequestBuilderPostRequestConfiguration();
$headers = [
		'Authorization' => 'Bearer {token}',
	];
$requestConfiguration->headers = $headers;


$result = $graphServiceClient->teams()->byTeamId('team-id')->schedule()->swapShiftsChangeRequests()->post($requestBody, $requestConfiguration)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = @{
	senderShiftId = "5ad10161-6524-4c7c-9beb-4e8677ba2f6d"
	senderMessage = "I can't make my shift, any chance we can swap?"
	recipientUserId = "567c8ea5-9e32-422a-a663-8270201699cd"
	recipientShiftId = "e73408ca-3ea5-4bbf-96a8-2e06c95f7a2c"
}

New-MgTeamScheduleSwapShiftChangeRequest -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.teams.item.schedule.swap_shifts_change_requests.swap_shifts_change_requests_request_builder import SwapShiftsChangeRequestsRequestBuilder
from kiota_abstractions.base_request_configuration import RequestConfiguration
from msgraph.generated.models.swap_shifts_change_request import SwapShiftsChangeRequest
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SwapShiftsChangeRequest(
	sender_shift_id = "5ad10161-6524-4c7c-9beb-4e8677ba2f6d",
	sender_message = "I can't make my shift, any chance we can swap?",
	recipient_user_id = "567c8ea5-9e32-422a-a663-8270201699cd",
	recipient_shift_id = "e73408ca-3ea5-4bbf-96a8-2e06c95f7a2c",
)

request_configuration = RequestConfiguration()
request_configuration.headers.add("Authorization", "Bearer {token}")


result = await graph_client.teams.by_team_id('team-id').schedule.swap_shifts_change_requests.post(request_body, request_configuration = request_configuration)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
"id": "0b87dd20-d5ed-4764-9c3e-cfc8516def09",
"senderShiftId": "5ad10161-6524-4c7c-9beb-4e8677ba2f6d",
"recipientShiftId": "e73408ca-3ea5-4bbf-96a8-2e06c95f7a2c",
"assignedTo": "recipient",
"state": "pending",
"senderUserId": "3fe0bc21-1398-4fd9-9713-52511b434c1e",
"senderDateTime": "2019-05-01T10:00:00Z",
"senderMessage": "I can't make my shift, any chance we can swap?",
"recipientUserId": "567c8ea5-9e32-422a-a663-8270201699cd",
"recipientActionDateTime": null,
"recipientActionMessage": null,
"managerUserId": null,
"managerActionDateTime": null,
"managerActionMessage": null
}
```
